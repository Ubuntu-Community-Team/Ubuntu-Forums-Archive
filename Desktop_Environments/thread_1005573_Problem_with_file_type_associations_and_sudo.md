---
title: "Problem with file type associations and sudo"
date: 2008-12-08
forum: Desktop Environments
---

### Post by generic-identity on 2008-12-08
Hi!

I wanted to have an option in Nautilus to open files as superuser with a right click. I found a simple script for that here: [http://www.pendrivelinux.com/2007/10/02/how-to-open-files-as-root-via-a-right-click/]("http://www.pendrivelinux.com/2007/10/02/how-to-open-files-as-root-via-a-right-click/")

Basically, the script calls [FONT="Courier New"]gksudo[/FONT] and [FONT="Courier New"]gnome-open[/FONT] for the file.

Now, my problem is that this does not use *my* file type assocations, but those of root for opening the file. So, if I've changed the default association, it will open the wrong application.

Any ideas on how to overcome this?

(Some thoughts:
It should be possible to look up "my" file association and open the respective app directly as root. However, my knowledge of Bash and Gnome is quite limited...
Second, is there a setting I can change so that file type associations I make as a regular user also take effect for root? I'm the only user of my machine anyway.)

---

### Post by generic-identity on 2008-12-10
I've solved (more or less) this myself. I'm posting my script here because it might be of interest to others.

The problem arises because changes of the file type association in Nautilus (via right click > "Properties" > "Open with") are saved user-locally, in the file "~/.local/share/applications/mimeapps.list".

I've written a Python script to open files with root privileges, but still with the application the user has defined for the respective file type. If the script is copied into "~/.gnome2/nautilus-scripts", it will be available via the right-click menu in Nautilus.
Here it is:

```

#!/usr/bin/python

# inspired by scripts from magnus (http://therning.org/magnus/archives/251) and
# kaer (http://mail.python.org/pipermail/python-list/2008-September/508040.html)

# note: using "return" in the main body makes the script not work!

import gnomevfs, os, subprocess, re

# environment variables exported by Nautilus:
vars = dict(paths="NAUTILUS_SCRIPT_SELECTED_FILE_PATHS", 
            uris="NAUTILUS_SCRIPT_SELECTED_URIS", 
            current="NAUTILUS_SCRIPT_CURRENT_URI",
            geo="NAUTILUS_SCRIPT_WINDOW_GEOMETRY")

files = os.environ[vars["paths"]].split("\n")

if files:
    # without this, only one file will be opened later (strangely):
    if len(files) > 1:
        subprocess.call("gksudo true", shell=True)

    # file with MIME application associations defined for current user:
    mime_file = os.path.join(os.environ["HOME"], 
                             ".local/share/applications/mimeapps.list")
    # main MIME directory:
    mime_dir = "/usr/share/applications"

    def open_default(file):
        subprocess.Popen('gksudo -k gnome-open "%s"' % file, shell=True)

    if os.path.exists(mime_file): 
        # open and parse MIME application info:
        source = open(mime_file)
        lines = [line.strip() for line in source]
        source.close()
        lines = [line.split("=") for line in lines if "=" in line]
        mime_apps = dict(lines)
        for file in files:
            mime_type = gnomevfs.get_mime_type(file)
            # open corresponding app:
            app = mime_apps.get(mime_type)
            if app:
                app = app.split(";")[0] # desktop file
                # get path to app:
                info = open(os.path.join(mime_dir, app))
                for line in info:
                    if line.startswith("Exec="):
                        path = line.strip().split("=")[1]
                        break
                info.close()
                # ignore exec parameters/field codes (http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html):
                path = re.sub(r"%[fFuUdDnNickvm]", "", path)
                subprocess.Popen('gksudo -k %s "%s"' % (path, file), shell=True)
            else:
                open_default(file)
    else:
        for file in files:
            open_default(file)


```

By the way, there is also a Nautilus extension (available in package "nautilus-gksu") that adds functionality for opening files as superuser, but I haven't tried it yet and don't know how it deals with the associated applications...

---


---
title: "bash script won't run from gnome sessions manager"
date: 2008-12-13
forum: Desktop Environments
---

### Post by mageus on 2008-12-13
Can't get bash scripts to run when I place them in the Startup Programs section of the Sessions Preferences.

- scripts work fine from a console or grun
- scripts don't require user input
- permissions on the files are fine
- although the files have execute permissions, I've even tried using sh in the command line - doesn't work

Any ideas?

---

### Post by sdennie on 2008-12-13
Are you using ~ in the location of the bash scripts?  ~ is interpreted by the shell and so I believe it won't work properly anytime you are presented with an "Enter command" type dialog in gnome.  You'll need to use /home/your_username instead of ~.

---

### Post by mageus on 2008-12-14
Did some more testing.  Bash scripts (in general) will run, but these specific scripts won't.

1st script:
"sudo gtk-update-icon-cache -f /usr/share/icons/Human"
- I've given nopasswd access to gtk-update-icon-cache via visudo

2nd script - randomizes compiz skydome.  Here's the important line
dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/cube/screen0/skydome_image org.freedesktop.compiz.set string:"$filename"


Both of these scripts work fine from the command line, or from grun (from within my personal, non-root, account).  I think it has to do with running the commands while gnome is starting up (though I have no idea why).

And, yes, I am using full paths for all filenames.

---

### Post by mcurran on 2009-02-18
I'm attempting to do the same.  Were you able to figure this out, or find some other workaround for the dbus script?

---


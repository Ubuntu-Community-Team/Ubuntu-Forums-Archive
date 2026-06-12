---
title: "Gnome MIME types and icons editor tool recommendation"
date: 2022-06-23
forum: Desktop Environments
---

### Post by louthrax on 2022-06-23
Hi everyone,

I'm looking for a tool allowing to quickly edit MIME types and associate icons on Gnome.

I know how to do this manually, but I recently had to resintall all my development environment, and realized that all the painfull and error-prone process could probably be automatized. For example, I'd like to associate all my *.pro files to QtCreator AND have the QtCreator icon displayed for those files. Gnome allows me to change the default application for all *.pro files, and set is as default. So far so good! But for the icon, I have to change it individually for each file (I've seen no "Set as default" tab for this).

I've already tried different tools (including gnome-tweaks), searched the web and forums, but have not found anything allowing to easily change the default application and icon for a MIME type.

Let me know if you have any suggestion.

Louthrax

---

### Post by Claus7 on 2022-06-24
Hello and welcome to the forums,

If I'm not mistaken then you should try something like this (it should work for other filetypes as well):
the icons are "drawn" from the theme you have selected
so, since you are aware of tweaks, verify the theme you are currently using from there
then go to /usr/share/icons/*your_theme*/48x48/apps and find the mime application icon (under this folder you should come accross just one mime named file)
change this icon with the one you wish, yet do a backup of the original icon first (as root change it name by adding for example at the end of its name the string bup) and then name the new icon exactly the same as the original
log out and back in and see the changes

If things go wrong, just revert back by moving the backup file to its original place.

Regards!

---

### Post by louthrax on 2022-06-25
Thanks Claus7 for the reply.

Yep, that method works! I'm just a bit surprised that no existing tool allow to do that in a more automated way.

So I just started working on a little Python script that could to that, using a common prefix for the newly created MIME entries and icons and using only "user" folders.

It would take a configuratrion file as input:
```
import os


mimeFolder         = "~/.local/share/mime"
iconsFolder        = "~/.local/share/icons"
applicationsFolder = "~/.local/share/applications"


entries = [
    ("pro", "~/Downloads/Qt_small.svg", "~/Qt/Tools/QtCreator/bin/qtcreator", "%F", "Qt Creator"),
    ("ygf", "~/bin/yEd/.install4j/yEd.png", "~/bin/yEd/yEd",    "%F", "yEd")
    ]

```

and scale / generate all icons for the available themes and sizes, along with the new MIME type and application. Still working on the design, I'll try to make it public if it works and people are interested...

---


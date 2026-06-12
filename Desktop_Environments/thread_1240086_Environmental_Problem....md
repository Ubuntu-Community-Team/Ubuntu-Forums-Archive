---
title: "Environmental Problem..."
date: 2009-08-14
forum: Desktop Environments
---

### Post by wotsit on 2009-08-14
[FONT=Palatino Linotype]OK so I have AWN on sessions to load on start-up with this icon set

[http://www.gnome-look.org/content/show.php/BuuF-iconset?content=46201](http://www.gnome-look.org/content/show.php/BuuF-iconset?content=46201)

(it's a gorgeous set, no?) I also run conky on start-up with #!/bin/bash sleep 20 && conky; with a conky rc from gnome-look, i forget which...

Also, I am trying to run the terminal on start up, with a tutorial to set it infront of the background that ive followed here

[http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop](http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop)

all was well with just the terminal and conky but when i got AWN as well, on start-up the terminal is transparent but no longer syncs with the desktop. It is in its own window like normal.

So I thought lets delay terminal to let devilspie load in case terminal is trying to run before its dependencies have loaded, so made a .sh and added to sessions

[/FONT]#!/bin/bash
sleep 10 && gnome-terminal --window-with-profile=DesktopConsole
...but it doesnt seem to work. Can anyone explain whats going wrong?

---


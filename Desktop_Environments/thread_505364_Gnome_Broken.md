---
title: "Gnome Broken"
date: 2007-07-20
forum: Desktop Environments
---

### Post by Boston on 2007-07-20
So I broke Gnome, somehow.

I changed the splash screen with this Bash script.

```
#!/bin/bash
#
# Tools-Set_as_Splash -> (set image as splash screen)
#
# Owner : Largey Patrick from Switzerland
#   	  patrick.largey@nazeman.org
#	  www.nazeman.org
#
# Licence : GNU GPL 
#
# Copyright (C) Nazeman
#
# Dependency : Nautilus
#
# Encoding UTF-8
#
# Vers.: 1.00 11.02.2004
#
# fix gnome 2.2 bug
#
curpath=`echo $NAUTILUS_SCRIPT_CURRENT_URI | sed 's/file\:\/\///'`
cd $curpath
#
# gconf editor
#
gconftool-2 --type string --set /apps/gnome-session/options/splash_image "$curpath/$1"
```

And It set the splash screen just fine.

Long story short, I get to GDM, login (I tried both regular Gnome session and failsafe, but have yet to attempt booting in the command-line environment), and Gnome starts up, but shortly freezes and then X restarts. The only two other things I did in addition to this is installed GTK 2.0 source files and PHP5/Apache2, but I don't see how those can affect Gnome.

Originally, the splash image I had was on the desktop, then a couple hours went by, I wasn't thinking and deleted the image and had to restart my machine for some reason, and then I run into this. On one occasion Gnome didn't freeze so I was able to recover the image, put it in ~/.splash/image.jpg and updated the path to it, but I still have the problem.

I assume it's a simple fix that I can do without running X, did anyone else run into this?

I also use Beryl (ATI-mobility 9600 with open drivers) which runs perfectly.

---

### Post by Happy_Man on 2007-07-20
Boot into the recovery mode, and redo the script so that it points to another picture or something.

---


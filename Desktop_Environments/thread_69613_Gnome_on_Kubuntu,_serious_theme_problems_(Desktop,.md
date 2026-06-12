---
title: "Gnome on Kubuntu, serious theme problems (Desktop, Panels)"
date: 2005-09-27
forum: Desktop Environments
---

### Post by Montgomery on 2005-09-27
Hi!

didn't really know where to put this thread, so fell free to move it :)

I'm using Kubuntu (5.04) on a laptop, and everything regarding the hardware seems to work fine so far.

a few days ago i installed the ubuntu-desktop package, i tried installing new (gnome-)themes and noticed a few bugs/problems. The gnome-theme-manager behaves really weird when scrolling, and uses a lot of cpu-resources, and certain themes (like [email]d3a@gnome-look.org[/email]) cause the desktop and the panels to crash,...

with a different user on this system everything works fine,...

thx!

[[IMG]http://img236.imageshack.us/img236/5180/bildschirmfoto0ng.th.png[/IMG]](http://img236.imageshack.us/my.php?image=bildschirmfoto0ng.png)
(screenshot of the gnome-theme-manager)

---

### Post by Paperjam on 2005-09-27
[QUOTE=Montgomery]with a different user on this system everything works fine,...
[/QUOTE]

To me it looks like your gnome configuration-files are messed up. Try moving them to another directory ```
mv .gnome2 .gnome2-backup
``` and log back into gnome. If it works, you'll have to copy your configuration-files one by one from *.gnome2-backup* to *.gnome2*.
If it doesn't work, you can restore your files with ```
mv .gnome2-backup .gnome2
```.

**Warning**: You do this on your own risk.

---

### Post by chavo on 2005-09-28
It looks like you're using the gtk-qt engine under KDE. That is the theme engine that makes Gnome apps look like KDE apps while running KDE. 

The problem is that this engine doesn't work well and causes problems when used under gnome. When you set up the theme with Control Center in KDE it writes a ~/.gtkrc-2.0 file and sets the environment variable GTK2_RC_FILES=~/.gtkrc-2.0.

So what you need to do is this -> unset $GTK2_RC_FILES then rm ~/.gtkrc-2.0. Now you should be able to get the theme manager working. Everything should clear itself up when you change your theme.

I have KDE and Gnome installed here and I have my startup scripts modified to rename the .gtkrc-2.0 file on Gnome startup and then copy it back on KDE startup.

---

### Post by Montgomery on 2005-09-28
[QUOTE=chavo]It looks like you're using the gtk-qt engine under KDE. That is the theme engine that makes Gnome apps look like KDE apps while running KDE. 

The problem is that this engine doesn't work well and causes problems when used under gnome. When you set up the theme with Control Center in KDE it writes a ~/.gtkrc-2.0 file and sets the environment variable GTK2_RC_FILES=~/.gtkrc-2.0.

So what you need to do is this -> unset $GTK2_RC_FILES then rm ~/.gtkrc-2.0. Now you should be able to get the theme manager working. Everything should clear itself up when you change your theme.

I have KDE and Gnome installed here and I have my startup scripts modified to rename the .gtkrc-2.0 file on Gnome startup and then copy it back on KDE startup.[/QUOTE]

yes, that was it :D

you mind telling me how to set up such a script?

---


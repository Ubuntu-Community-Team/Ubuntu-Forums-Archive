---
title: "icon theme problem"
date: 2009-08-11
forum: Desktop Environments
---

### Post by krazytreee on 2009-08-11
so, i've been trying every technique under the sun to try and change my icon theme. i tried dragging it into the themes manager, no workie. i tried extracting it to the desktop and using sudo to move it to usr/share/icons, did not werk. i tried dragging it to the file using gksudo nautilus, the file moved but it never showed up in the appearence settings, fail. so i used nautilus to see what was different about the other icon sets and i realized that the icon theme i wanted [http://www.gnome-look.org/content/show.php/Red+Icons+for+GNU%2BLinux?content=84396 ]("http://www.gnome-look.org/content/show.php/Red+Icons+for+GNU%2BLinux?content=84396")
lacks a  file called a index.theme file.
so my question is, can i createone of these files to make the icon set aplicable to my theme manager? is there something in jaunty jackalope that has changed since hardy? is there some other workaround that i havent heard of? thx in advance for the help:confused:

---

### Post by qamelian on 2009-08-11
What you've downloaded ins not a theme but an icon set. If you want to use these icons in a theme, you'll find a tutorial here: [http://live.gnome.org/GnomeArt/Tutorials/IconThemes](http://live.gnome.org/GnomeArt/Tutorials/IconThemes)

An icon set is just a collection of icons which you can assign manually to file types etc. The index.theme file essentially tells Gnome which icons to use for what purpose as a complete "set".

---

### Post by krazytreee on 2009-08-11
sweet \m/ ^.^ \m/ thanks for the info. also, can i use this tutorial to make my own icon sets if i can design icons? that would be ballin'

---


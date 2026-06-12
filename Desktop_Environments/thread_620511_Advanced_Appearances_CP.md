---
title: "Advanced Appearances CP"
date: 2007-11-22
forum: Desktop Environments
---

### Post by frbe0101 on 2007-11-22
I find the existing appearance control panel in Ubuntu 7.10 limiting, is there a advance control panel I can summon?

---

### Post by frbe0101 on 2007-11-26
Hey can someone help me on this?

---

### Post by erfahren on 2007-11-26
> **frbe0101 said:**
> I find the existing appearance control panel in Ubuntu 7.10 limiting, is there a advance control panel I can summon?
not that I know of, other than the Visual Effects "Advanced Desktop Effects Settings"

if you enable the desktop effects (Visual Effects) - which is Compiz-Fusion you can get the emerald package (theme manager), that has advanced options.

(there's also the gnome-compiz-manager, but to be honest I'm not quite sure what it does. I haven't installed it. I just configure the desktop effects through the "Advanced Desktop Effects Settings".)

Anyway, for the regular themes (going through the Appearance control panel - Metacity, GTK2, icons, etc.) you can get more at gnome-look.org --- there is also the gnome-art package you can get through Synaptic to browse and install the themes from there.

if you don't know the difference between Metacity, GTK2, etc. this thread explains it: [http://ubuntuforums.org/showthread.php?t=349408](http://ubuntuforums.org/showthread.php?t=349408)

there's a guide here: [http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/#more-131](http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/#more-131)
info here: [http://www.informit.com/articles/article.aspx?p=664146&seqNum=4&rl=1](http://www.informit.com/articles/article.aspx?p=664146&seqNum=4&rl=1)

note: I don't use emerald, but have tried it. I thought it was a llittle too much, and just one more thing that needed to run. I found a GTK2 theme I liked and stuck with it. You can see it here: [http://www.one-tweak-loop.com/misc_files/messy_scrnshot_ubuntu.htm](http://www.one-tweak-loop.com/misc_files/messy_scrnshot_ubuntu.htm)

wallpaper can be added to the terminal through it's settings - Edit > Current Profile

hope all that wasn't too confusing! lol

---

### Post by frbe0101 on 2007-11-26
Thanks, that helps, somewhat, all I'm looking to do is control the colors of the menu and text a little better, maybe a theme editor of some kind?

---

### Post by erfahren on 2007-11-26
I know what you mean by a theme editor. I don't think a GUI based one exists at this time. I've searched for something before and actually tried to search for information on how those themes at gnome-look.org were made. I never really found much information on that.

The GTK2 themes that I've gotten from gnome-look have a file for the theme called gtkrc. It seems like a XML based file. I'm sure that the icon text could be changed in there. I don't know what is used to create it, and I'm under the impression from what I've seen is that the only way to edit them at this time is manually.

On this thread here they're talking about the same type of thing, and someone gives a link to an app that is still in the developement stage. [http://ubuntuforums.org/showthread.php?t=452648](http://ubuntuforums.org/showthread.php?t=452648)

You can do some advanced using gconf-editor - look under apps > nautilus to start. That can also be gotten to through Applications > System Tools (but it may ned to be enabled to show in the Menu Editor).

good luck

---


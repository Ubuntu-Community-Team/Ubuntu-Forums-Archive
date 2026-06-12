---
title: "MacMenu Bar on 8.04?"
date: 2008-05-13
forum: Desktop Environments
---

### Post by javaTN on 2008-05-13
Well.. im a fairly new migrant to the Ubuntu community...

can i compile or install a mac-menu bar applet to my Gnome desktop? i am running Ubuntu 8.04 Hardy Heron -- gnome 2.22.1.

really hope there is a way i can do this mod, so i need someones help.

thanks!
-tom

---

### Post by NikoC on 2008-05-13
Well you might be interested in installing avant window navigator...
Just take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=762363]("http://ubuntuforums.org/showthread.php?t=762363")

---

### Post by javaTN on 2008-05-13
i have avant installed with my Synaptics...what im interested in is a Macmenu bar for Ubuntu 8.04.

like this:
[IMG]http://developer.apple.com/documentation/Porting/Conceptual/win32porting/art/menubar.jpg[/IMG]

---

### Post by ozorba on 2008-05-13
I assume that you have read this:

[http://ubuntuforums.org/showthread.php?t=241868](http://ubuntuforums.org/showthread.php?t=241868)

---

### Post by javaTN on 2008-05-13
yes i have, thoroughly and many times... but i get the picture that its only made for gtk 2.10.x or 2.8.x (dont know what that means, but when i go to System > About Gnome on my computer it says Gnome 2.22.1, which is not one of those versions).

im also not sure which is the first step i take to make it work, they just list downloads and stuff, nothing that really guides me in any direction of what to do exactly.

---

### Post by Gunfreak on 2008-05-14
GTK is a theme manager if I am not mistaken.

---

### Post by RAOF on 2008-05-14
To do this you will need to download the GTK+ source, patch it, and then rebuild it.  As far as I know there are no prebuilt packages with this (major) patch applied.  Nor is it currently likely to be incorporated in official GTK+ - it's an invasive change, and breaks a fair range of appliations (as mentioned in the linked thread).

The instructions in that thread still apply.  I would suggest, however, that this is a bad idea on any machine that you would like to work reliably.

---

### Post by chris062689 on 2008-05-14
I could have sworn I saw this kind of a feature in KDE 3.x, try under Window Settings.

EDIT: Found it, System Settings > Desktop > Behavior > Menu Bar Top of Screen.

This is probably as close as your going to be able to get.

---

### Post by javaTN on 2008-05-14
> **chris062689 said:**
> I could have sworn I saw this kind of a feature in KDE 3.x, try under Window Settings.

EDIT: Found it, System Settings > Desktop > Behavior > Menu Bar Top of Screen.

This is probably as close as your going to be able to get.

thanks for the help guys... i guess ill live without it.

PS chris, i dont use kubuntu.

---

### Post by LavianoTS386 on 2008-05-16
Follow the directions here:

[http://code.google.com/p/gnome2-globalmenu/wiki/InstallingonUbuntu](http://code.google.com/p/gnome2-globalmenu/wiki/InstallingonUbuntu)

---

### Post by Poyzin on 2008-12-22
i'm not getting on how do use these instructions for intrepid. I'm on ubuntu 8.10.. that's intrepid, yes?

---


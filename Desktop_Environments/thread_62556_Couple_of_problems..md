---
title: "Couple of problems."
date: 2005-09-05
forum: Desktop Environments
---

### Post by celluloid on 2005-09-05
Hey guys, Need some more help.
A few things that I need some help on. Using Breezy + XFCE.

1. Using wifi connection, problem is, it keeps "timing out"? or disconnecting me after about 20-30minutes, needing a reboot to re-connect it. Can't seem to find the problem and all settings seem to be correct.

2. Nothing major but I'd like some launchers on my taskbar. Question is, where are all my program icons kept? I can use say "gaim" as the command but I need an icon for it, can't find the folder.

3. Compiling keeps giving me errors. What are some packages that I can get from Synaptic that will pretty much solve all my compling/make errors.

I hope these aren't too general, if any more details are needed please let me know what you need and how to get it.

Thanks very much.
Grant.

---

### Post by xmastree on 2005-09-05
[QUOTE=celluloid]2. Nothing major but I'd like some launchers on my taskbar. Question is, where are all my program icons kept? I can use say "gaim" as the command but I need an icon for it, can't find the folder.[/QUOTE]Well, most icons are in usr/share/pixmaps, including /usr/share/pixmaps/gaim.png

---

### Post by frodon on 2005-09-05
[QUOTE=celluloid]3. Compiling keeps giving me errors. What are some packages that I can get from Synaptic that will pretty much solve all my compling/make errors.
[/QUOTE]When you have compilation problems you should give us the errors you get, maybe it's a dependency problem or something else. However if you haven't installed **build-essential** package it could be the problem.

If you want a gaim icon on the gnome panel :
Right click on gnome panel and choose to add an icon, choose standard application icons and go in internet folder and you will find the gaim icon then press OK.

---

### Post by smeager on 2005-09-05
[QUOTE=celluloid]Hey guys, Need some more help.
A few things that I need some help on. Using Breezy + XFCE.

1. Using wifi connection, problem is, it keeps "timing out"? or disconnecting me after about 20-30minutes, needing a reboot to re-connect it. Can't seem to find the problem and all settings seem to be correct.

.[/QUOTE]

You are using the driver version 0.19 that came with ubuntu which is old. You need to get the newer version (vrs. 1.0.6) and firmware (2.3) and complile them for your kernel. (everytime you update your kernel image you have to recomplie the drivers for it) 

You can gat the instuctions on how to do this in this thread:  [http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623) 

Plus (in a terminal) type **dmesg | grep ipw** and copy what it says here.

---

### Post by celluloid on 2005-09-06
[QUOTE=smeager]You are using the driver version 0.19 that came with ubuntu which is old. You need to get the newer version (vrs. 1.0.6) and firmware (2.3) and complile them for your kernel. (everytime you update your kernel image you have to recomplie the drivers for it) 

You can gat the instuctions on how to do this in this thread:  [http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623) 

Plus (in a terminal) type **dmesg | grep ipw** and copy what it says here.[/QUOTE]
 root@ubuntu:/home/grant/bmp-docklet-1.3 # dmesg | grep ipw
root@ubuntu:/home/grant/bmp-docklet-1.3 #

:S
Gives me nothing?

---


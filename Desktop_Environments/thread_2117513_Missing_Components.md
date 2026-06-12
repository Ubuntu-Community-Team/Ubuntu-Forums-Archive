---
title: "Missing Components"
date: 2013-02-18
forum: Desktop Environments
---

### Post by eipapp on 2013-02-18
Just recently installed Ubuntu Gnome 3 on my desktop. Everything went well but I was disappointed to find that I somehow lost my software manager.It was there, then it wasn't ?!? I was also surprised to find that it lacked Gdebi package installer. I'm terrible when it comes to installing tar files. Yuk....
Any ideas how I can reclaim the Software Manager and then install the Gdebi pkg installer as well ? 
Also I note that every time I come off hibernate it wants to do a disk check which is very annoying. Any help with these issues would be greatly appreciated.

Thanks,
Bruce

---

### Post by Frogs Hair on 2013-02-18
Move the cursor into the top left corner and type software center. Once  open add the the application to the panel on the left with a right click.

The software center is a Ubuntu application and does not appear by default in the Gnome Shell . Gdebi is not a default application and if you installed in Ubuntu you can find it Gnome or install it from the software center. 

The Gnome Shell calendar on the panel is designed to work with Evolution and not Thunderbird.Evolution is not installed if you want to use this feature.


Gnome Cheat Sheet (needs updating): [https://live.gnome.org/GnomeShell/CheatSheet](https://live.gnome.org/GnomeShell/CheatSheet)

---

### Post by eipapp on 2013-02-18
When I start to type software center the only thing that appears is Software Updater, not software center.

---

### Post by aarons6 on 2013-02-18
do you mean the ubuntu software center?

did you remove unity?

just type in 
sudo apt-get install software-center

---

### Post by eipapp on 2013-02-18
Did not install Unity, only Gnome version of Ubuntu so software manager is not the same as in Unity. Will try apt-get as you suggested and see how that works.

Thanks,

---

### Post by Frogs Hair on 2013-02-18
It appears under system tools for me but I installed the shell as an add-on to my Ubuntu desktop and not the Gnome Remix.

[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10](https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10)

---

### Post by eipapp on 2013-02-18
Wish I would have done the same.
Anyway, YOU DID SOLVE ONE OF MY PROBLEMS, I now have the software center back. What, if anything, can be done about the other issue, why the disk check every time ? Is there a way to stop that ?

Thanks again for ur help, much appreciated.
Bruce

---

### Post by aarons6 on 2013-02-18
my system also does a disk check every time it boots.. 
im sure there is a way to make the system to the check every x number of boots but i dont restart my computer much.. maybe twice a month.

it also takes less then a second anyway..

---


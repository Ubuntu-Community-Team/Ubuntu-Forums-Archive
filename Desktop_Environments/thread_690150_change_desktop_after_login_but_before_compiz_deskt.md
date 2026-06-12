---
title: "change desktop after login but before compiz desktop appears"
date: 2008-02-07
forum: Desktop Environments
---

### Post by misterfloyd on 2008-02-07
Hi All

Is it possible to customise the screen that appears after you login but before the compiz desktop appears?  I'm running 7.10 with compiz enabled.

Many thanks

---

### Post by jeffus_il on 2008-02-07
It's definitely possible, Xubuntu displays the little mouse running in the circle  kde changes the screen at different stages of the startup. I''l have a look and see how if you don't beat me to it.

---

### Post by jeffus_il on 2008-02-07
Found this:
> Yukonjack
January 17th, 2005, 07:33 AM

To change the splash screen, put the downloaded image in ~/.gnome or any place you would like but ~/.gnome is a good place. ~ means /home/yourname/.gnome/splash.png. This way it will be easy to change splash screen in the future. Rename your new splash screen to splash.png if it's a png file or splash.jpeg if it's a jpeg file. Now we have the splash screen ready ~/.gnome/splash.png. Then edit the GConf key /apps/gnome-session/options/splash_image using the Configuration Editor (Panel menu->System Tools->Configuration Editor) right click on splash_image key and choose edit key, where you see Key Value enter the new key value /home/yourname/.gnome/splash.png or the commandline tool gconftool-2. Now do a quick reboot Ctrl-Alt-Backspace and bingo your new splash screen. In the future if you want to change the splash screen just rename you new downloaded splash screen to splash.png or .jpeg and move or rename your old one and drop the new splash screen in ~/.gnome this way it save renaming the Key Value everytime you want to change splash screen. Next time you reboot you will see the new splash screen.

/for the real newbee/if you change from a png to a jpeg file don't forget to change the Key Value to the new file format/ that is all



here:
[http://ubuntuforums.org/archive/index.php/t-11478.html](http://ubuntuforums.org/archive/index.php/t-11478.html)

---

### Post by misterfloyd on 2008-02-07
Thanks for the quick responce however I followed your instructions and it doesn't quite work :(

After logging in I get the flat brown screen for a couple of seconds, then the splash screen i set up for a couple of seconds then back to the flat brown until compiz starts about 10 seconds later.

---

### Post by misterfloyd on 2008-02-07
oops - looks like this has already been covered in an earlier thread

[http://ubuntuforums.org/showthread.php?t=583905&highlight=gdmsetup](http://ubuntuforums.org/showthread.php?t=583905&highlight=gdmsetup)

---


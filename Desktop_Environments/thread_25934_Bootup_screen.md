---
title: "Bootup screen"
date: 2005-04-11
forum: Desktop Environments
---

### Post by cc05 on 2005-04-11
I would like to add a nice bootup screen to my Hoary 5.04 install.

Is it possible to add a bootup screen to Hoary 5.04?

//have a nice day ;)

---

### Post by XDevHald on 2005-04-11
[left]Click --> [[color=Navy]Change Your Boot Screen[/color]]("http://ubuntuforums.org/showthread.php?t=25144&page=2&pp=10")[color=Navy]  [color=Black]with official settings on how to do this, please read the instructions VERY carefully to get this done right.

P.S look for [/color][/color]**[color=Navy]Joh_'s [/color]**[color=Black]name as he best explains the procedure.[/color]
[/left]

---

### Post by nad on 2005-04-11
From: [http://ruslug.rutgers.edu/~mcgrof/grub-images/](http://ruslug.rutgers.edu/~mcgrof/grub-images/)

1. Instructions
1.0 Requirements for GRUB splashimages:

    1. xpm.gz file type
    2. 640x480
    3. 14 colors only

1.1 I have my image, now what?

    1. Gzip your xpm file and put it into your /boot/GRUB directory (or to any directory of a /dev/hda1 partition). (do: `gzip myfile.xpm`)
    2. Edit your GRUB config file (aka /etc/GRUB.conf) and add this line:
    splashimage=(hd0,0)/GRUB/myfile.xpm.gz
    NOTE: Change the partition and directory according to your system's setup.
    3. reboot and cross your fingers

End Cut and Paste

There is much more information at this site. Note that the instruction to modify your GRUB config file will be /boot/grub/menu.lst for ubuntu.

Good luck,

Dan M

---

### Post by vanaedium on 2005-04-11
Usplash preview 0.1 works fine

[http://wiki.nanofreesoft.org/index.php/UsplashHowDoesItWork](http://wiki.nanofreesoft.org/index.php/UsplashHowDoesItWork)
Download and install the 2 libs and 1 pack

 ;-)

---


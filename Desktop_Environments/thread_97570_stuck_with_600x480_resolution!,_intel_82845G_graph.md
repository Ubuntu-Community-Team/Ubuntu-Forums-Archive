---
title: "stuck with 600x480 resolution!, intel 82845G graphics card"
date: 2005-12-01
forum: Desktop Environments
---

### Post by michaeljking on 2005-12-01
I have tried installing ubuntu several times but I either get no graphics or a linited 600x480, my graphics card is a intel 82845G, 
when I installed it there was a message saying some packages were not installed
Does anyone know how to resolve this?

---

### Post by xmastree on 2005-12-01
Search these forums for resolution.
You'll probably find that you need to manually add your screen refresh rates to xorg.conf

[http://www.ubuntuforums.org/search.php?searchid=2751212](http://www.ubuntuforums.org/search.php?searchid=2751212)

---

### Post by tseliot on 2005-12-01
Have a look at this guide: [HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973")

---

### Post by michaeljking on 2005-12-01
Thanks very much!

sudo dpkg-reconfigure bit to xserver-xorg

this worked, after a couple of try's, I lost the graphical screen for most of it (The only thing i am consous of doing diferently is changing the color from 24bit to 16, but whatever, this worked!

(played around with settings and at the return of the command prompt)

startx 

voila

resolution resolution!

---

### Post by blair on 2005-12-01
A minor but important clarification to the above: The correct command syntax to load the graphical xorg.conf application is:

sudo dpkg-reconfigure xserver-xorg

---

### Post by hardclip on 2005-12-06
Best and easiest thing to do is change the shared video memory from 1024k to 8192k in the BIOS before booting...instant fix

---

### Post by nolagirl05 on 2006-12-17
> **hardclip said:**
> Best and easiest thing to do is change the shared video memory from 1024k to 8192k in the BIOS before booting...instant fix

Can someone provide detailed instructions on how to do this?  I am sort of a noob, but not totally.  Thanks!

---

### Post by vendejp on 2007-02-24
this is probably too late, but if you hit F2 when your machine is booting up it will take you to the bios config.  somewhere you should be able to up the video buffer from 1MB to 8MB.  unfortunately this didnt take care of the problem for me and Im still suffering.

Good luck

---


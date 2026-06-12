---
title: "Eve Online &amp; NVidia GTX260 vs 30/10/2008 patches"
date: 2008-10-30
forum: Gaming &amp; Leisure
---

### Post by draxbear on 2008-10-30
I just upgraded with the latest patches which unfortunately rendered my NVIDIA GTX260 unusable by Eve-online.

I was on: NVIDIA-Linux-x86_64-177.68-pkg2.run

Fortunately NVIDIA released a new (and several others I missed) version of their driver here:
 [ftp://download.nvidia.com/XFree86/Linux-x86_64/177.80/](ftp://download.nvidia.com/XFree86/Linux-x86_64/177.80/)

After downloading the newer version and running it:
-switch to a terminal & login
 CTRL-ALT-F1
-stop your local x server
 sudo /etc/init.d/gdm stop
-make your download executable
 chmod 544 NVIDIA-Linux-x86_64-177.80-pkg2.run
-run your download
 ./NVIDIA-Linux-x86_64-177.80-pkg2.run
-follow the prompts and generally say yes a lot EXCEPT for the last question regarding Xorg file editing. I answered no to retain my customized xorg, if you were working before with the older driver that's the way to go.
-If you are doing this for the first time say yes to get a basic xorg.conf file for the driver. Your old one is backed up fyi.

I'm all ok again. Figured I'd let you all know in case you run into the same problem.

Some handy details:
$ uname -a
Linux vega 2.6.24-21-generic #1 SMP Tue Oct 21 23:09:30 UTC 2008 x86_64 GNU/Linux
Ubuntu Heron 8.04
NVIDIA GTX260


Great to see a new driver so promptly available on NVIDIA site, although it would be nice if they would just let go and open the thing so we don't have to hit the command line to kick start it in future...

---

### Post by Jucke35u on 2008-10-30
The world is a ladder for some to go up and others to go down.Thsale is a professional, loyal and reliable wow gold supplier online, we pioneered selling cheap wow gold. [wow gold](http://www.wowgold-pl.com/), We are a Great MMORPG company. wow money and wow items,which is very cheap WOW Gold&#65281; [wow gold](http://www.wowgold.ws/), Welcome to thsale buy world of warcraft gold Buy Cheap WoW Gold, World of Warcraft Gold, Please look here![wow gold](http://www.wowgold-pl.com/conditions.html), All US Server 24.99$/1000G on sell! Cheap wow gold,rs powerleveling,wow power leveling,Buy Cheapest/Safe/Fast WoW US EU Gold Power leveling [wow gold](http://www.wowgold.ws/wowgold.html),  [FFXI Gil](http://www.ffxigilvip.com/),

---


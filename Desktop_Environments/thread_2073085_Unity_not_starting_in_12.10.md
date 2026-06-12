---
title: "Unity not starting in 12.10"
date: 2012-10-18
forum: Desktop Environments
---

### Post by BSOD64 on 2012-10-18
Hey y'all,

I just updated to 12.10 and when I login I see my desktop icons but no unity dock or top bar. There are no window borders either. It works fine when I use gnome but I'd really like to use unity.

thanks

---

### Post by 2F4U on 2012-10-19
What are your hardware specs, graphics card and graphics driver? Am I right in assuming that Unity worked before the upgrade?

---

### Post by phoe2693 on 2012-10-19
have the same issue.  i can force unity to get going by control-alt-t to open a terminal and running unity&

although sometimes it takes a godawful time to load, and other times I end up having to control-alt-f1 and start it from the console.

i havent explored what else might be causing it yet, but id note that my installation of 12.04 is perhaps 6 weeks old, and I have not modified it significantly.  Im on an x230 with intels i915 graphics.

---

### Post by llmishra on 2012-10-19
I have the same problem with Dell C640 pentium-4 Radon card. It was working fine in 12.04 . When I tried from terminal. It is saying hardware not supported.

---

### Post by safir on 2012-10-19
I have the same problem after upgrading from 12.04 to 12.1. No menu bar no launcher.

---

### Post by mitchelllc on 2012-10-20
I also have the same problem, and still don't know why

---

### Post by oldfred on 2012-10-20
If you need proprietary video drivers see this thread & these bugs.

Fix for nVidia with 12.10 missing kernel dpkg reconfigure:
[http://ubuntuforums.org/showthread.php?t=2072862](http://ubuntuforums.org/showthread.php?t=2072862)

Has most bug reports:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341)

[https://bugs.launchpad.net/fglrx/+bug/1068456](https://bugs.launchpad.net/fglrx/+bug/1068456)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488)
[https://bugs.launchpad.net/fglrx/+bug/1068661](https://bugs.launchpad.net/fglrx/+bug/1068661)

Has what worked for me, install headers & dpkg update.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068942](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068942)

---

### Post by mitchelllc on 2012-10-22
This solves my problem!:P
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)
I got the solution from this thread [http://ubuntuforums.org/showthread.php?t=2074397](http://ubuntuforums.org/showthread.php?t=2074397)

---

### Post by BSOD64 on 2012-10-23
Graphics Card: Mobility Radeon HD 4200
Graphics Driver: VESA: RS880M
RAM: 2GB
Processor: AMD V120

Unity worked fine before I updated from 12.04 to 12.10.

I tried mitchelllc's link and now, whenever I boot with kernel version 3.5 I get a black screen instead of the login screen.

---

### Post by BSOD64 on 2012-10-24
Sorry I was a bit slow in responding. bump.

---

### Post by BSOD64 on 2012-10-29
bump

---

### Post by oldfred on 2012-10-29
I only really know a bit of nVidia. 

With your AMD, you need to know if you have legacy version which is not supported by the new drivers or a newer board that is supported.

Did you install the headers. That is critical to get anything to work with 12.10.

Not sure now which is for current or which is for legacy with AMD/ATI.

[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)
#sudo aticonfig --initial -f
sudo aticonfig --adapter=all --initial
After reboot to get Catalyst Control Center
sudo apt-get install fglrx-amdcccle

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
[http://ubuntuforums.org/showthread.php?t=1558406](http://ubuntuforums.org/showthread.php?t=1558406)

sudo apt-get install fglrx

---

### Post by _salem_ on 2012-11-02
> **mitchelllc said:**
> This solves my problem!:P
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)
I got the solution from this thread [http://ubuntuforums.org/showthread.php?t=2074397](http://ubuntuforums.org/showthread.php?t=2074397)

After spending a few hours stuffing around installing, reinstalling, uninstalling all sorts of combinations of drivers, the above ppa of legacy catalyst drivers worked for me, too. Thanks for the link, mitchell!

---

### Post by robinofsussex on 2013-03-01
I have no launcher, and no window decorations after last nights update on my laptop.
I can run terminals via ALT-CNTRL-F1 etc, but it seems the update has broken unity.

---

### Post by ysse on 2013-03-01
Had that issue after update yesterday. Have had 12.10 running without problems for several weeks.
Obviously, some new updates have come along since yesterday evening, for after a new update everything works.

From a terminal (Ctrl-Alt-T), run update-manager.

---

### Post by Bachi on 2013-05-10
In my case, the Unity problem persisted even after changing to the correct driver. I noticed that using a guest account, everything was fine, so it a user setting was broken. ```
dconf reset -f /org/compiz
``` solved the issue (though some compiz settings were resetted also)

---


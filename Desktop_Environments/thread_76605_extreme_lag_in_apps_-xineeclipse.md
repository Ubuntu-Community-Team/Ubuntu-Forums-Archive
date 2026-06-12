---
title: "extreme lag in apps -xine/eclipse"
date: 2005-10-15
forum: Desktop Environments
---

### Post by pear-i on 2005-10-15
my laptop sys right now seems to be running into quite a bit of lag for some of the applications -- anyone have any idea whats going on?

System right now is - Dell C640 Laptop -  P4M 2.0 512 mb 20 GB HDD w/ ubuntubreezy

I've tried running DVDs in Xine/Totem and in Xine it plays... but lags and then dies when i try to change the track. totem it goes alright except it is jittery like a celeron pig insane amounts of skipping.

Eclipse -- well whenever i start a new Java Project it just white screens and lags until i kill it. 

right now -- my laptop is slower than my winblows machine (desktop - AMD 900mhz 512 mb) so... thats kinda really annoying -- any ideas what might be the problem for those 2 apps in particular?

---

### Post by jdong on 2005-10-15
[QUOTE=pear-i]my laptop sys right now seems to be running into quite a bit of lag for some of the applications -- anyone have any idea whats going on?

System right now is - Dell C640 Laptop -  P4M 2.0 512 mb 20 GB HDD w/ ubuntubreezy

I've tried running DVDs in Xine/Totem and in Xine it plays... but lags and then dies when i try to change the track. totem it goes alright except it is jittery like a celeron pig insane amounts of skipping.
[/quote]
What kind of video card? Have the appropriate 3D drivers (if ati or nvidia) been installed?

Is DMA enabled on your DVD drive (check sudo hdparm /dev/hdc)

> 
Eclipse -- well whenever i start a new Java Project it just white screens and lags until i kill it. 

GCC 4.0 Java is surprisingly slow on Ubuntu (was faster on Fedora 4)... Try installing Sun Java (search up the HOWTO section for the proper way -- java-package).

---

### Post by pear-i on 2005-10-15
I'm using an ATI Radeo 7500 Mobility w/ 32 mb 

as for the java compiler i already have the sun-j2sdk1.5 package from way back for hoary 

just turned on hdparm -- i'll let you know if that speeds up anything :)

---


---
title: "wireless configuration in ubuntu 9.10"
date: 2010-01-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by G0uth4m on 2010-01-25
Hai,

I installed **UBUNTU 9.10 **in my brand New **DELL INSPIRON 1440** laptop. But when I am trying to configure wireless, No such option is enabled. Can you give me a solution to configure wireless in my laptop.

---

### Post by r_s on 2010-01-25
Just switch on your bluetooth

---

### Post by G0uth4m on 2010-01-25
I am doubted whether there is a driver in my DELL 1440 or not... !!!!!

In dell latitude D630 it automatically detected... But in my Dell 1440 it's n:confused:t detecting :(

---

### Post by Kixtosh on 2010-01-25
Has this been resolved yet? 
 
I just installed Ubuntu 9.10 in a very old (1999) Dell, which is using a PCMCIA wireless card, and there were no wireless issues. 
 
At first, it didn't seem to be working, but look on the top "panel", on the right hand side. You should see a logo that looks similar to a cell phone tower icon, such as those used on ... well ... mobile phones! It's fairly discreet when there is not active signal (just like on a cell phone with no bars), but it my case, it's located between the sound icon and the time/date information area. If you see that icon, just click on it, and you should immediately see a list of available networks, including the one you usually connect to. Click on that.
 
That's all I had to do. It was so incredibly simple, even though this particular card actually required special drivers with Windows, and was not recognized at all by Knoppix (Live CD) when I first tried that about five years ago.

---

### Post by efflandt on 2010-01-26
See what wireless device shows up doing **sudo lspci -v** in a terminal.

If it is BCM4311 or BCM4312, if you have a temporary ethernet connection, go to System > Adminstration > Hardware Drivers and activate Broadcom STA.  Otherwise insert your installation CD and temporarily add (check) the CD as a source for Synaptic and install bcmwl-kernel-source package.

---

### Post by lovelife53 on 2010-02-03
@ above..thank you so much sir..it worked .. !

---


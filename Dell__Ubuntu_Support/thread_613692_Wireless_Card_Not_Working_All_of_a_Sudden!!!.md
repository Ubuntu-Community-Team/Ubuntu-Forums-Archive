---
title: "Wireless Card Not Working All of a Sudden!?!!?"
date: 2007-11-15
forum: Dell  Ubuntu Support
---

### Post by zfactor1981 on 2007-11-15
Hi Folks,

I was using my wireless card to connect in a cafe last night. All of a sudden, Ubuntu just died on me. I rebooted, and everything seemed to be working fine. When I got home and fired up my laptop, my computer wouldnt make a connection to my wireless modem. Oddly it asked me for the security key, which i had stored (i connected the day prior). I restarted the computer and my wireless card was not being detected. 

I reinstalled the ndiswrapper, which somehow uninstalled itself, but i still cannot connect to the internet. Anyone have a similar problem? Can you recommend a way to fix it?

Also, as a side question, does anyone know how to change the size of the window when using the default remote desktop software that comes with Ubuntu. 

A Vista Ditcher for the Open Source...Hitcher (?), 

Z

---

### Post by Triptol on 2007-11-15
Seems you had a nice crash ruining part of your install. Or there was someone else on the network playing with your laptop.

I would completely remove everything ndiswrapper:
```
aptitude purge ndiswrapper
```after which I would check whether everything is gone (no ndiswrapper in /etc anymore or anywhere else).

Then reinstall and reconfigure it.

You should also check whether your wireless card still can be seen by the system. You could check with dmesg and/or lspci and friends. There is a possibility that your pc crashed because of the fact that the card suddenly decided to commit suicide.

---


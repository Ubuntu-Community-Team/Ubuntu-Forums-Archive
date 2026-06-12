---
title: "Ubuntu Running in Low Graphics Mode"
date: 2008-11-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kordite on 2008-11-29
It began innocently enough with an automated update to my laptop. The Update Manager came up and said it wanted to update linux-restricted-modules-common (2.6.22.4-15.1) to 2.6.22.4-16.12. Actually, I didn't pay much attention to it at the time, this detail I got from the Update Manager History)

After the required reboot it threw an error "Ubuntu running in low graphics mode" and booted to a display size of 800x600 instead of what it should have been 1440x900.

I have attempted to modify the xorg.conf file to include the 1440x900 display mode. I have restored from a backup xorg.conf file. I uninstalled the Envy application that had been managing my NVIDIA drivers but had come with a warning that it would need to be uninstalled before any upgrade (that is, upgrade from 7.10 to 8 or something major like that. It should not have affected a driver upgrade). I uninstalled and reinstalled the nvidia-driver module and the restricted-modules. A manual graphics configuration was tried. I uninstalled the 2.6.22.4-16.12 drivers and went back to version 2.6.22.4-15.1.

All of this pretty much bounces between the Low Graphics Mode and 800x600 failure and a 1024x768 marginal success. I was unable to get it to the full 1440x900 screen. The problems seems to be in the NVIDIA accelerated graphics driver. In the Restricted Drivers Menu it is shown as "Not in use" and attempting to enable them caused the whole failure routine to cycle again.


Inspiron E1505 N
Intel® Pentium® dual-core proc T2080(1MB Cache/1.73GHz)
Ubuntu Edition version 7.10
15.4 inch Wide Screen XGA Display with TrueLife™
1GB Shared Dual Channel DDR2 SDRAM at 533MHz, 2 Dimm
120GB 5400rpm SATA Hard Drive
8X CD/DVD Burner (DVD+/-RW)
256MB NVIDIA® GeForce® Go 7300 TurboCache™
Intel PRO/Wireless 3945a/g

---

### Post by falcon61102 on 2008-11-29
This seems to be a pretty reoccurring problem that has since been fixed in 8.10.  Since a new kernal has been installed, you need to re-install the drivers for it to function.  

Have you attempted to re-install Envy and install the drivers through Envy again since that is what you originally used?  Also, you may want to start fresh by unistalling all current nvidia drivers before proceeding.  That will help the Envy install.

---

### Post by kordite on 2008-11-29
I had the Nvidia drivers working with 1440x900 but when Second Life did an upgrade, it was no longer compatible with the drivers that I had. I used Envy to update those. This experience and some things I read since made me a bit suspicious of Envy and logically since my drivers worked before Envy, they should be able to work without Envy.

Lacking any other suggestions at this stage, however, I reinstalled Envy.

Aftre the first reboot I had no error messages, the screen came up to 1024x768 and while there were more resolution choices in the Screen Resolution Menu, none were higher than 1024x768.

I noted that the Nvidia drivers weren't actually enabled in the Restricted Drivers Manager so I enabled them and rebooted. It threw an error saying that there was an error starting the GNOME Settings Daemon. The screen resolution was 1024x768 but the icons were not correct. I rebooted again, which solved the daemon issue but still didn't grant me the 1440x900 setting.

I looked at the xorg.conf file and noticed that it was had entries like "Failsafe Monitor." I restored my backup file and it restored the screen to something that looked right but was only 1280x800. I looked at some old screen captured and realized that my laptop had alway only had 1280x800 (the 1440x900 resolution is what my desktop machine has and I misremembered.) This error did not invalidate my problems, however.

ISSUE IS RESOLVED.

I can't say that I'm pleased that I had to re-install envy to do it, again, I have some suspicion that it may have been part of the reason that this particular restricted driver update failed. I hope that the next update does not cause the same problems. At least I'll have an established procedure to repair it.

---

### Post by falcon61102 on 2008-11-29
Glad you got it fixed to some degree at least.

---


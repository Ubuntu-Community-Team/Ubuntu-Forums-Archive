---
title: "Help With Twinview"
date: 2009-04-21
forum: Desktop Environments
---

### Post by ryman102990 on 2009-04-21
So I'm new to Ubuntu. What drew me in was the Ubuntu Studio, since I'm a supposed "recording artist." When I use windows xp, I use two monitors. I've managed to get both my monitors working, but not in any functional manner. I have a ProView 1280x1024 LCD monitor and a random CRT 1280x1024 running on a Nvidia GeForce 7600GT. I'm using ubuntustudio 8.10. 

So, my issue is that when i edit my xorg.conf, i can get my LCD monitor to display in native resolution, but my CRT will only display up to 1024x768. I really need them to both be the same resolution. I can't for the life of me figure out how to fix this problem and would REALLY appreciate any help and advice.

Here is my xorg.conf:

Section "Device"
         Identifier  "Videocard0"
         Driver      "nvidia"
         VendorName  "EVGA"
         BoardName   "NVIDIA GeForce 7600GT"
         Option      "TwinView"                 "true"
         Option      "RenderAccel"              "true"
         Option      "UseEdidFreqs"             "true"
         Option      "MetaModes"                "1280x1024,1280x1024;1280x1024,NULL"
         Option      "SecondMonitorHorizSync"   "30-110"
         Option      "SecondMonitorVertRefresh" "50-160"
 EndSection

Section "Screen"
         Identifier   "Screen0"
         Device       "Videocard0"
         Monitor      "Monitor0"
         DefaultDepth 24
         SubSection "Display"
           Viewport   0 0
           Depth      24
           Modes      "2560x1024" "1280x1024"
         EndSubSection
 EndSection


So, once again, my primary monitor will run in 1280x1024 resolution, but my secondary CRT will only run up to 1024x768 in auto in the nvidia control panel.

If it helps at all, they are both plugged into the DVI ports on the card via VGA-DVI converters.

---

### Post by skullmunky on 2009-04-22
try the "nvidia-settings" utility.  (you'll have to install it from synaptic first).  it lets you configure monitors and graphic card options on nvidia cards w/o editing xorg.conf.  search this forum for "nvidia-settings" for helpful threads about it if you're stuck.

---

### Post by Vadi on 2009-04-22
Do alt+f2, "gksudo nvidia-settings", and use the X Server Display configuration section to configure it. much easier than with xorg.conf: [http://www.ubuntu-pics.de/bild/12851/screenshot_42_ZqTwtB.png](http://www.ubuntu-pics.de/bild/12851/screenshot_42_ZqTwtB.png)

---


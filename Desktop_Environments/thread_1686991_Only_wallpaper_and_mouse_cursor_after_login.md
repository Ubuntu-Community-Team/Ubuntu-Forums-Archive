---
title: "Only wallpaper and mouse cursor after login"
date: 2011-02-13
forum: Desktop Environments
---

### Post by Hans3 on 2011-02-13
Hi!

I've had this problem for some time now and googled for days but nothing has worked, so if anybody could help me it would make my day!

Heres what happened:
I used ubuntu 10.04 for some months and it worked just fine. Suddenly when my little sister and brother used the computer it crashed (Could be because of some upgrade). Black screen after ubuntu loading screen. So I googled for a while but lost my temper so I loaded my ubuntu cd formatted the disk and installed ubuntu over again.

This time i get to login screen and after login all i see is the wallpaper and mouse cursor. I can move the cursor but I cant right-click or anything. Ubuntu works perfectly in safe mode though!

A difference a noticed from the first time I installed was that the first time: I could choose to install proprietary drivers for my graphic card and wifi network card whith "Jockey". Now i cant and I have no wifi internet connection! I dont know how the graphic card works but apparently its using some kind of default driver as i can see things ;)

Well if anoboudy know how to make my ubuntu work as good as before, please help me!

Graphic card: ATI Radeon X1200 (It worked before with compiz, desktop effects and everything!)
Network card: Broadcom Netlink BCM5787M (Yes this is also my wifi card because of the M in the end, also worked good as ever, before)
Computer: HP Compaq 6715b

---

### Post by Hans3 on 2011-02-13
ok i have now solved most of the problems!

I did this:
ctrl+alt+f1 to get to command line.
type this code: sudo apt-get remove xorg
accept that two programs are being removed
now type: sudo reboot

Now you can see all menues and such. Now go to program center and install the binary x.org driver for ATI graphic cards and you have a nice fast computer again! :D

Now its only the wireless networc card left..

---

### Post by Hans3 on 2011-02-13
ok so now i fixed the wifi also!

just remove the broadcom-somthing program from program central ant restart computer. now you can find a good working proprietary driver with hardware driver-tool

Over and out!

---

### Post by Krytarik on 2011-02-13
> **Hans3 said:**
> ok i have now solved most of the problems!

I did this:
ctrl+alt+f1 to get to command line.
type this code: sudo apt-get remove xorg
accept that two programs are being removed
now type: sudo reboot

I'm wondering why you have a desktop *at all* after doing this!? This would also remove "ubuntu-desktop" (at my system, maybe you have another desktop environment).

And if you don't re-install them, you have nothing left but the console!

---


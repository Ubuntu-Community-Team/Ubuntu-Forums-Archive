---
title: "[NEED HELP] Stuck in Low Graphics mode"
date: 2008-12-24
forum: General Help
---

### Post by Couto on 2008-12-24
Alright, so I just reinstalled Ubuntu for the 4th time TODAY to try to fix this, and I've given up! Everytime I install the NVIDIA Graphics Driver Version 177 and then reboot (after installing all the updates it needs me to install also) It says I need to go into Low graphics mode.

Anyways, I'm running the newest Ubuntu (8.10)
I have NVIDIA GeForce 9500 GS graphics card.
Whatever other info you need me to do, and anything you want me to install or do in terminal please let me know. Thanks.

---

### Post by gettinoriginal on 2008-12-24
Ok, not knowing what you have tried, I will start at the beginning, please be patient.  :P

System > Preferences > Screen Resolution   make sure your resolution/refresh rate is correct

System > Admin > Hardware Drivers     make sure your driver is activated.

---

### Post by Couto on 2008-12-24
Driver is activated, and if I change Screen Resolution I get messed up screens and it's just all fuzzy and I can't see what I'm doing, even after reboot.

Anything else for me to try?

---

### Post by gettinoriginal on 2008-12-24
I would try this to reconfigure your display, just follow the instructions:

In terminal type:

sudo dpkg-reconfigure xserver-xorg

It will run you through several screens asking about your system.

---

### Post by WillBMX on 2008-12-24
If that doesn't work, try booting up in recovery mode, then right clicking on applications then add the 'Other>Screen and Graphics' application. Open it up and then tell it what screen you have and what GPU you're using, Then you should be able to set the screen res and refresh rate to whatever you want. Close it then reboot into normal mode and see what happens.

---

### Post by Couto on 2008-12-25
I did sudo dpkg-reconfigure xserver-xorg many times it does not help.
I do not have "Screen and Graphics on Edit Menus.

---

### Post by akshay.sulakhe on 2008-12-25
Hey why dontu try downloading the run file from Nvidia site and installing itby urself...so that it will tell u what to do..and as mentioned while installing the restricted driver..they are not open source..so no once can help..plz download the run file and install it...i also have Nvidia 9600gt...i do the same...i know GS is altogether different...

---

### Post by Couto on 2008-12-25
I do not understand, NVIDIA has no 9500 GS option on their site anymore, can't really download something that's not on their site.

---

### Post by Couto on 2008-12-25
Why does Ubuntu 8.10 not have Screen and Graphics on Other anyways.
When I try to install Ubuntu 8.04 I have no Internet connection somehow. and it does have Screen and Graphics.
Anyways can nobody helps or something.

---

### Post by armandh on 2008-12-25
try a different monitor
I had one that would not report the needed plug & play info back to the os. 
until I used a different monitor all I got was low rez.

---

### Post by Couto on 2008-12-25
My other monitor is an anchor.

---

### Post by Couto on 2008-12-25
I'll try my other huge anchor monitor now to see if thats the problem, I guess.

---

### Post by Couto on 2008-12-25
My other monitor doesn't work either.

---

### Post by Couto on 2008-12-25
Is there no fix for this or what? Cause without it, there is no point having Ubuntu, I mind aswell switch to Windows.

---

### Post by Couto on 2008-12-25
This forum to busy and my thread keeps getting buried.

---


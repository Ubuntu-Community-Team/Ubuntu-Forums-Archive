---
title: "Pweeezzzzz... Help!"
date: 2008-04-09
forum: Dell  Ubuntu Support
---

### Post by Tootiecat on 2008-04-09
I finally got Ubuntu installed (8.04 beta) via Wubi.  My laptop is a Dell Inspiron B130 and the OS is running off of an external hard drive.  It installed correctly for the most part, but I can't print via local USB (Canon MP160) or record from a microphone or connect to my wireless microphone... all of which I need to be productive.  I also wanted to know if it was possible to print with Ubuntu with Bonjour over to my Airport Express.

---

### Post by Victormd on 2008-04-09
I'm using gutsy right now, but if I'm not mistaken, the driver for MP160 comes with Hardy.  I have a canon mp460 and use the mp150 driver to print over the network (no drivers for the mp460 that I know of). What does System>Administration>Printing show you? Usually, you'll have to change the settings for the make and model. Ubuntu detects the printer but sets it to text only (or something like that) and you have to set it up manually by changing either the "device" or the "make and model" (don't remember which).

For your mic., try this: double click the volume icon and check if the Microphone is set to mute, if not, then on the window with all the volume sliders, go to Edit>Preferences, and scroll down to Microphone Capture and mark that.

**You might have to reboot for the mic to work...**

For your wireless, you might try thess links, they're for HP but... they use Dell drivers to get the wireless working, so I guess they should work just fine for you.
[http://ubuntuforums.org/showthread.php?t=572005](http://ubuntuforums.org/showthread.php?t=572005)
[https://wiki.ubuntu.com/HP_dv6000_Series](https://wiki.ubuntu.com/HP_dv6000_Series)

---

### Post by Tootiecat on 2008-04-12
I saw what you meant for the microphone, and I am currently working on the wireless drivers & whatnot.  I couldn't test my mic, b/c the way Wubi installed Ubuntu is screwed up... I would like to know how to give more space to Ubuntu on my external hard disk. (Maxtor--USB--- 100GB)(Which it is running off of.)

<<THIS WAS FIXED AS OF 4/13/08>>
<<WIRELESS IS NOW WORKING>>

---

### Post by renatoborges on 2008-05-25
> **Tootiecat said:**
> I finally got Ubuntu installed (8.04 beta) via Wubi.  My laptop is a Dell Inspiron B130 and the OS is running off of an external hard drive.  It installed correctly for the most part, but I can't print via local USB (Canon MP160) or record from a microphone or connect to my wireless microphone... all of which I need to be productive.  I also wanted to know if it was possible to print with Ubuntu with Bonjour over to my Airport Express.

about the airport express print;

all you have to do is install the avahi-utils by the synaptic package manager (system/administration/synaptic package manager) and after installation restart your system.

then go to system/administration/print and click the new printer button, your printer or printers, connected to the airport express should appear in the list of printers available for installation.

---


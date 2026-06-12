---
title: "Dual screen problem with NVIDIA driver"
date: 2016-03-28
forum: Desktop Environments
---

### Post by echo59 on 2016-03-28
Hi, I'm looking for some help.


I'm running 15.10 (64-bit) and I've a dual-screen setup.  My graphics card is a EVGA GeForce GTX 750 and I have 2 monitors connected, both identical Asus VE247 LED screens.  I've one connected to the graphics card via DVI (on left) and the other via HDMI (on right).


I've installed the proprietary NVIDIA driver, version 352.63.


Currently I've the monitors set up as providing an extended desktop, so I can drag windows from one screen to the other.  However, I like using Compiz desktop cube so I can change desktops but obviously I can't switch desktop on one monitor without moving on the other one also.  This is actually what I want.  To be able to change desktop on either/both monitor independent of each other.


I've tried using the NVIDIA X Server settings dialog to change this but without any luck.


In the NVIDIA X Server settings on display configuration I have selected the right-hand screen and changed the configuration to 'New X screen (requires X restart)' 


I then 'Save to X Configuration File' and log out and log back in again.  Now the HDMI (Screen1) is black but when I move my cursor over it a black X with white edging appears as the cursor.

Any ideas as to what I need to do to get a second x server running to display my right-hand desktop???  I've attached some screenshots from the NVIDIA settings.

[ATTACH=CONFIG]268034[/ATTACH]        [ATTACH=CONFIG]268033[/ATTACH]

---


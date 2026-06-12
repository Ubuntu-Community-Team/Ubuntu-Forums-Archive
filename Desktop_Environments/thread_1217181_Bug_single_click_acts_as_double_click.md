---
title: "Bug: single click acts as double click"
date: 2009-07-19
forum: Desktop Environments
---

### Post by BramWillemsen on 2009-07-19
Hello,

Yesterday I finally managed to convince my father to get rid of the old, slow windows XP that was installed on his computer. He agreed to try ubuntu after I told him how enthousiastic I was about it. Most things seem to work fine, except for one thing.

A certain percentage of the single clicks count as double click when using a Quare optical mouse. It is quite annoying if a browsing window opens when you only wanted to select a certain directory for example. I opened xev and it showed that two clicks are sometimes recorded when I only click once. 

When i connect my Trust USB laptop mice everything works just fine. The problems seems to be related to the Quare optical mouse. I already tried entering this in xorg.conf

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/mouse"
        Option          "Protocol"              "Auto"
EndSection

It had no effect unfortunately. The Quare mouse is most likely not broken, it worked fine in windows yesterday. Does anyone have a tip? Thanks!

Bram

edit: my father just remembered he also experienced some strange effects in windows. A single click minimising and then maximising a window and such. I guess the mouse was also giving trouble then. Probably broken hardware. (threat can die)

---

### Post by bluplanet on 2009-08-01
I have the same issue.  I'm using 9.04 on a Dell Inspiron 1520 with a Logitech Blutooth mouse.

Symptoms:
Highlighting a paragraph of text with the mouse is hit and miss.  Sometimes, I get what I want.  Sometimes, the highlight doesn't start till after I've started sliding the mouse and some text gets left out.  Sometimes It cuts out before I finish sliding the mouse and text near the end gets left out.  I'm talking about pressing the left mouse button, sliding the mouse over a paragraph and then releasing the button.  A few times, I've done that and only got a single letter highlighted somewhere in the middle of the paragraph.

Single-clicking icons can be problematic.  If I click the "Back" button on my browser, it usually is interpreted as two clicks and I go back too far.  

Playing the game "Freecell" is a trip.  Single clicking a card tends to throw it up into the storage area at the upper left of the screen.  Then clicking it in that storage area often makes it jump to another empty storage cell.

Someone with the same issue wrote that they thought the problem could be worked around by making sure the mouse wasn't moving when it is clicked.  I've discovered this doesn't always work.  It seems that making very slow deliberate clicks helps though.  It seems like maybe there is some mouse related code being executed that supersedes mouse clicks and interrupts a depressed mouse button.  When the code is finished, the depressed mouse button is interpreted as having been released and clicked again.

I've tried several edits of xorg.conf based on suggestions in this forum that are claimed to "work almost all the time" but they haven't worked for me.  This has included simple edits that added CorePointer and Configured Mouse Input devices and edits that have had a few or a lot of options under those.   I've read that this is only an issure with laptops with a touchpad in addition to a mouse (Please confirm this).

---

### Post by Aearenda on 2009-08-01
I've seen it before with a dodgy mouse, where the Windows driver seemed to have a better tolerance for bouncing contacts inside the mouse than the Linux driver. The only fix I found was to get another mouse :-(

---

### Post by Bucky Ball on 2009-08-01
9.04 is maybe not the one to go for if you are changing. 8.04 LTS (Long Term Support) is more stable because it has been around longer and maybe a better bet.

---

### Post by albanodesign on 2009-08-01
take a look at the system/preferences/mouse

---

### Post by joopie18 on 2009-08-01
or just change to kubuntu.. :)
If I'm not mistaking KDE makes use of the single mouse click..
Gr

---

### Post by robert shearer on 2009-08-01
You might want to buy your dad a new mouse as his "Welcome to Ubuntu" bonus.:)

---

### Post by Bucky Ball on 2009-08-01
Yea, I am using Xubuntu right now but I have all my machines set up for one click. It is in one of the menus as mentioned above. Probably just need to change it.

---

### Post by jtrott on 2010-03-28
I had the same issue with a wireless mouse that worked well previous and then started exhibiting the same behavior. Tried a USB mouse and the problem was gone, I suspected it was the batteries, they were Ni-MH and kinda old. So, I tried some alkaline (not even brand new) and the problem disappeared on the wireless mouse as well. I've also seen this with Ni-MH battery packs and Wii remotes where they would lose sync too frequently. So you might look at that and see if it helps.

---

### Post by yvsong on 2011-05-21
This bothers me a lot. Triggered many extraneous actions accidentally with a bluetooth mouse when single clicks counted as double. When 2 clicks with very short interval are detected, the OS should treat it as a single click. If no human can do double clicks that fast, it means it's a hardware malfunction.

---

### Post by isaach on 2011-08-18
There's a bug item for this problem over at Launchpad.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/365300](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/365300)

Grab a Launchpad account and vote for the bug and maybe they'll fix it some day.

---


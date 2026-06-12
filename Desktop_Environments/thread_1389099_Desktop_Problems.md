---
title: "Desktop Problems"
date: 2010-01-23
forum: Desktop Environments
---

### Post by Ckoi on 2010-01-23
Hello everyone, I am new to Linux and Ubuntu... i have just installed the Desktop version on my IBM laptop... and i am experiencing problems with the desktop...

The screen does not seem to load properly, and incompletely... when i click on Firefox for example, i can see it appear in the bar at the bottom, but it doesn't load on the screen... but when i move the mouse cursor around, the content of the webpage slowly appears under where i move the cursor... 

i don't know how to fix this problem.. if anyone could help it would be greatly appreciated.

thanks !!

Rick (Ckoi)

---

### Post by lykwydchykyn on 2010-01-24
What model is your laptop?  It's usually helpful to know the make and model of the graphics chip in these instances.

Also, what are the basic specs of the laptop (cpu, RAM, etc)?

---

### Post by Unix-Man on 2010-01-24
It's because they're is no video driver installed to use you're video card to it's max potential. 

Give us you're hardware information and we can determine what driver you should activate :D

---

### Post by Ckoi on 2010-01-24
Hey guys,

Its an IBM Thinkpad R40...  here are the specs on it...


[LIST]
[*]Intel Pentium 4 M 1.3 GHz Processor
[*]512 MB PC2100 Memory (2 GB Maximum)
[*]40GB Hard Drive
[*]24x CD-RW Combo Optical Drive
[*]15" XGA LCD and ATI Radeon Mobility M7 Graphics with 32MB
[*]SoundMAX AC'97 Audio
[*]v.92 56kbps Modem and 10/100 Fast Ethernet
[*]802.11b Wireless
[*]Two USB 2.0 Ports, One FireWire Port and One Type III PC Card Slot
[*]12.3" x 10" x 1.5" @ 5.6 lbs.
[/LIST]
thanks for the help !!   Linux is all new to me, so i'm just learning how to work things out.

Rick. (Ckoi)

---

### Post by Ckoi on 2010-01-24
Still looking for some help guys...    

anyone out there have any ideas as to what correction i would have to make to stop the desktop from going crazy ???

Thanks !!

---

### Post by lykwydchykyn on 2010-01-24
You have an ATI chip in there, so we should try loading the proprietary driver.

If you can see the menu, try opening the "hardware drivers" tool.  It should indicate that there is a proprietary driver available for your video card which is not activated.  

Activate it.  You'll need to be online, because it'll download and install the ATI video driver.

When it's done, reboot and see if the video is any better.

---


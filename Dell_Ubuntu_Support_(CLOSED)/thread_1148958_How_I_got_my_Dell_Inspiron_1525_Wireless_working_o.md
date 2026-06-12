---
title: "How I got my Dell Inspiron 1525 Wireless working on 9.04 Jaunty"
date: 2009-05-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Minipalmer on 2009-05-04
I'm sure there will be floods (or already are) of questions about these very soon, so I thought I might try and help.

I just upgraded to the new Ubuntu 9.04 Jaunty Jackalope. Immediately my graphics card and wireless card stopped working as they were in Intrepid.

I haven't fix the graphics card problem, but for the wireless card I merely went into my drivers and disabled the new ones.

1. System > Administration > Hardware Drivers

2. Select "Broadcom STA Wireless Driver"

3. Click "Deactivate"

I could always pick up and find connections, I just couldn't connect. After I deactivated this, I could connect just fine.

Hope it helps someone.

---

### Post by eb sol on 2009-05-26
could you tell me how did you fix graphics card problem ??

---

### Post by enlli on 2009-05-29
Funny that both my Broadcom Driver and Graphics card are working perfectly with 9.04 and the 1525

---

### Post by nomorewindoz on 2009-06-09
My video and wireless were working great with 9.04 and my Dell 1525 until I did an upgrade.... now wireless stops all together, but video is good....
I tried going to hardware drivers, but it says there are no proprietary drivers in use on this system...

Good thing I have an Acer one as a backup!

---

### Post by KineticIdea on 2010-02-26
> **Minipalmer said:**
> I'm sure there will be floods (or already are) of questions about these very soon, so I thought I might try and help.

I just upgraded to the new Ubuntu 9.04 Jaunty Jackalope. Immediately my graphics card and wireless card stopped working as they were in Intrepid.

I haven't fix the graphics card problem, but for the wireless card I merely went into my drivers and disabled the new ones.

1. System > Administration > Hardware Drivers

2. Select "Broadcom STA Wireless Driver"

3. Click "Deactivate"

I could always pick up and find connections, I just couldn't connect. After I deactivated this, I could connect just fine.

Hope it helps someone.
  
Well I am having a similar problem. When I upgrade to Karmic, my wireless card won't pick up any networks. 
When I go into my drivers, It says "Broadcom STA Wireless Driver is activated but not currently in use." I have no idea how to use it?

---

### Post by TracyO on 2010-02-28
I have the same exact computer.  I'm still using Jaunty.  What is it showing when you go to "Network connections"?

---

### Post by compaq64 on 2010-03-01
I have the same model laptop and i got the wireless function perfectly normal. I think i just went into drivers and activated the wireless.

---

### Post by Surachinen on 2010-10-17
okay, using a dell inspiron 1525 with maverick meerkat (10.10)

was not connected to internet when installing ubuntu, and afterwords wireless would not work.
the 'additional' drivers that ubuntu offered kept saying something along the lines of missing package or whatnot (was connected at this stage)

downloaded ndiswrapper from software center

found xp drivers for wlan (in windows partiton of said laptop, don't know where to get them otherwise)

dragged said driver (was in a folder labeled ProgramFiles/Dell/DellWlanCard/Drivers, so i took the whole folder) to desktop of ubuntu

ndiswrapper worked perfectly in this scenario, no reboot needed.

want to thank the community for putting me on the right track.

---


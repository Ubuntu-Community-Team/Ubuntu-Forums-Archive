---
title: "Static Lines on Dell Inspiron 6400"
date: 2010-06-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by platnicat on 2010-06-20
My dad has a Dell Inspiron 6400 with an ATI Mobility Radeon X1300 128MB video card. I've finally convinced him to install Ubuntu (Yay! :guitar:) but I'm running into a problem: I'm getting little static lines (.5-3 cm long) all over the screen. These aren't there at bootup, but they appear after ~5 minutes of usage. I've tried changing drivers, turning desktop effects on and off, etc. These also appear in console view when shutting down, so I think it might not be X. When I take screenshots, they don't appear, so it isn't a problem in the rendering (I think), and it works fine in Windows. I really don't want to have to tell him that Ubuntu won't work right on his hardware, so I'm hoping this'll turn out to be fairly easy to fix.

Thanks in advance, Matt

EDIT: I forgot to mention, I'm running Lucid (10.04) with all updates installed. i need to update my OS indicator.

---

### Post by efflandt on 2010-06-26
I have same work laptop with same video, although, I run 64-bit 10.04 on it from USB WD Passport, so I do not have to mess with anything on its internal hard drive.  Sometimes when it booted 10.04 it had an almost regular pattern of red or orange hash marks near the top of the screen and seemed to lock up.  The solution is to use **nomodeset** kernel boot parameter to use the regular radeon modules instead of kernel mode setting driver.

See [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

My desktop also has an ATI X1300 AGP card, although, with slightly different problems (some slow video and failed to suspend or hibernate).  The nomodeset boot parameter fixed that, so I was already aware of that when trying the Dell laptop.

---


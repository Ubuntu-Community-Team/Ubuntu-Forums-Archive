---
title: "Unity very poor performance with 13.04 and nvidia 9500GT"
date: 2013-04-26
forum: Desktop Environments
---

### Post by mmerlone on 2013-04-26
Greetings,

Just fresh installed 13.04 from scratch and unity is terribly slow. I have tried binary drivers for nvidia-304, nvidia-310 and nvidia-313, but no luck. Installing mate desktop now to check. Any suggestions?

Sds.

---

### Post by Frogs Hair on 2013-04-26
I have an 8 series card with 3.13 drivers running well. Unity , the Gnome shell, and XFCE are currently installed. I beta tested and preformed a clean installation of the 13.04 final release as well . Considering you have a newer graphics card I don't know what the problem could be. I have also tested the Compiz cube and other plugins also on both beta and final releases.

---

### Post by mmerlone on 2013-04-30
Went to gnome-fallback with compiz, it is usable for a couple of hours, then performance drops quickly, to the point I have to close the session and login again. Tried all available drivers (nouveau was as kick as my CPU could get) and no luck. Any ideas?

---

### Post by Frogs Hair on 2013-04-30
Did you verify the ISO image and Disc ? 

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Cammy on 2013-04-30
I also have a 9500GT and I'm using the Nouveau drivers.  I just couldn't find a good way to install the Nvidia driver that actually worked without causing some other problem.  The Nouveau works, but as the OP stated, the performance isn't all that great.  I'm thinking about swapping the card for a Radeon 3850 that I have, but I'm not sure if the ATI drivers will be any easier to deal with.

---

### Post by mmerlone on 2013-05-01
> **Frogs Hair said:**
> Did you verify the ISO image and Disc ? 

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Well, actually no, but downloaded from ubuntu official download site and installed from an USB stick.

---

### Post by mmerlone on 2013-05-01
> **Cammy said:**
> The Nouveau works, but as the OP stated, the performance isn't all that great.  I'm thinking about swapping the card for a Radeon 3850 that I have, but I'm not sure if the ATI drivers will be any easier to deal with.

Nouveau works for me, with half frame per second. As for ATI, it were never able to make me happy, in a decade, just headaches.

---

### Post by Cammy on 2013-05-03
So after a number of hours last night following just about every "how to" I could find on getting the proprietary nvidia drivers installed, I ended up with the dreaded "wallpaper only" desktop.  Rolling back to the Nouveau driver didn't help, and neither did re-installing 13.04 over top of itself.  Looks like I'm in for reformat/reinstall #4 since switching to 13.04.

And I would be touching the video drivers in ubuntu again, that's for sure!

---

### Post by Frogs Hair on 2013-05-03
> **mmerlone said:**
> Well, actually no, but downloaded from ubuntu official download site and installed from an USB stick.

It is not the download location but , the quality of the disk or USB. I'm not sure how able to run three window managers and the cube  well on an 8 series Nvidia card. I can't  find a  problem specific to the 9500GT except those in this thread .

---


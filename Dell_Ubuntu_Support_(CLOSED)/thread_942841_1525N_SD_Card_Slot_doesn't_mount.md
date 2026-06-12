---
title: "1525N SD Card Slot doesn't mount"
date: 2008-10-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sassinak on 2008-10-09
I have a 1525 with the front MMC/SD Card slot next to the headphone jacks and I discovered the other day that the device isn't automatically mounting the card when it's inserted.

Problem seems persistent, even after a reboot, and the device fails to show up on the desktop, or mounted anywhere else in the system that I can find.  The only thing that I can think of is that I got a non Dell specific kernel upgrade that failed to include a driver perhaps? :confused:   

Anyone got any ideas?  I don't use the card slot frequently, but I'd like it to actually work when i want to use it.

---

### Post by ajgreeny on 2008-10-09
Are you using an sdhc card?  These are not read by quite a few older card-readers (I have one of those, though an external one in my case) and this could just be your problem.  I don't know if there could perhaps be an updated firmware for the card-reader, but it's worth checking that out if that is the problem

---

### Post by sassinak on 2008-10-09
Nope, no SDHC, it's just a run of the mill 128MBSD card from a P&S camera.  Works fine in the camera and worked the last time I inserted it in the laptop a few months ago, but just not working now.

---

### Post by ajgreeny on 2008-10-10
Strange, but try reformatting the card in the camera, not using gparted, and see if that brings it to life again.  If not I suspect the card has just simply died.

---


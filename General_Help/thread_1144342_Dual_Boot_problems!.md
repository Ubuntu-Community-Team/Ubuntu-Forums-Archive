---
title: "Dual Boot problems!"
date: 2009-04-30
forum: General Help
---

### Post by AlexLuckett on 2009-04-30
Hi guys.

Right, I've got a Dell Inspiron laptop next to me, with 2 hard drives installed. On the one hard drive (C: ), I have Windows Vista installed. My aim is to install the new Kubuntu on to the second hard drive (D: ) without affecting Vista.

I've installed Kubuntu using the "Install Within Windows" option, and selected the D: hard drive as the installation path. When I come to load Kubuntu from the menu when I boot my laptop - I get a black screen and nothing more. I've been told it's an issue to do with GRUB not being installed correctly/on the right device.

Can anybody tell me how to install GRUB correctly onto my D: hard drive? Without affecting Vista? If not, is there anyway to install Kubuntu onto the second drive so it works?

Thanks in advance,
Alex

---

### Post by codeseer on 2009-04-30
I strongly advise against installing using that wubi stuff. If you have a drive (D) that you're willing to use anyway, I recommend just straight installing it to that drive.

To do a straight install, just put the Kubuntu CD in and boot the system from that. Then select install and go through the simple steps. I also recommend manually allocating partitions when you get to that option (probably step 4). Give a swap partition equal to the size of your RAM and dedicate the rest to root. Some people dedicate some to root and the rest to /home, but I prefer relying on backups instead of a live partition in case of disaster. Either way, I recommend manual partitioning.

---

### Post by NJC on 2009-04-30
Apologies if silly, but have you selected to boot from D in BIOS?

---

### Post by AlexLuckett on 2009-04-30
> **codeseer said:**
> I strongly advise against installing using that wubi stuff. If you have a drive (D) that you're willing to use anyway, I recommend just straight installing it to that drive.

To do a straight install, just put the Kubuntu CD in and boot the system from that. Then select install and go through the simple steps. I also recommend manually allocating partitions when you get to that option (probably step 4). Give a swap partition equal to the size of your RAM and dedicate the rest to root. Some people dedicate some to root and the rest to /home, but I prefer relying on backups instead of a live partition in case of disaster. Either way, I recommend manual partitioning.
Thanks for the help. Well I have never really trusted that method, since the last time I attempted it I somehow wiped the whole of my laptop.

I'm going through the install steps now. Just to be on the safe side I won't do it manually. Anyway, I'm on the step now where it says:

> Use Entire Disk
- SCSI1 (0,0,0) (sda) - 160.0 GB ATA
- SCSI3 (0,0,0) (sdb) - 160.0 GB ATA
Specify partitions manually (advanced)

So am I to presume the first option (SCSI1) is Vista? And that if I select the second option (SCSI3), I will install Kubuntu on the D: drive without affecting Vista whatsoever?

As you can tell, I'm new to all this! Sorry!

> **NJC said:**
> Apologies if silly, but have you selected to boot from D in BIOS?
Yes, I'm sure!

---

### Post by Monotoko on 2009-04-30
It will recognise your internal system drive first, the same one Windows recognises as C:\ so you are correct in your assumption :)

---

### Post by NJC on 2009-05-01
I take the next step and unplug the 80 pin IDE (or SATA) connector on the Win drive. Then there's NO chance to overwrite the win installation, nor any chance of having Grub installed on the wrong drive too.

---

### Post by codeseer on 2009-05-01
> **NJC said:**
> I take the next step and unplug the 80 pin IDE (or SATA) connector on the Win drive. Then there's NO chance to overwrite the win installation, nor any chance of having Grub installed on the wrong drive too.

That'll show 'em! :P

---

### Post by AlexLuckett on 2009-05-01
> **NJC said:**
> I take the next step and unplug the 80 pin IDE (or SATA) connector on the Win drive. Then there's NO chance to overwrite the win installation, nor any chance of having Grub installed on the wrong drive too.

Oo thanks. Do you mind telling me how to do this, if you know?

---

### Post by NJC on 2009-05-04
Open case and unplug the power connector to Win drive, that would be easier. At least there wouldn't be any possibility of breaking a SATA cable (if it is SATA).

EDIT: Sorry, I just realized this is a laptop! :oops: Not sure how easy it is to unplug drives.

---

### Post by codeseer on 2009-05-04
> **NJC said:**
> Open case and unplug the power connector to Win drive, that would be easier. At least there wouldn't be any possibility of breaking a SATA cable (if it is SATA).

EDIT: Sorry, I just realized this is a laptop! :oops: Not sure how easy it is to unplug drives.

Fairly easy. They just don't have wires/cords. It should be just a screw or two on the bottom of the laptop to remove a plate and slide the drive out, sometimes by pulling on a plastic tab. This is assuming it isn't some non-standard design.

---


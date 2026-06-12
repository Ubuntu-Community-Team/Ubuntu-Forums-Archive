---
title: "Feisty - External USB hard disk no automount"
date: 2007-04-27
forum: Desktop Environments
---

### Post by dentaku65 on 2007-04-27
Hi,
is someone able to automount an external USB hard disk (vfat in my case)?
I've chek in the forum and I found a lot of issues about the usb devices; can someone post here the launchpad ticket(?) for the usb harddrives (if any)?

TIA

---

### Post by dcstar on 2007-04-27
> **dentaku65 said:**
> Hi,
is someone able to automount an external USB hard disk (vfat in my case)?
I've chek in the forum and I found a lot of issues about the usb devices; can someone post here the launchpad ticket(?) for the usb harddrives (if any)?

TIA

Works fine for me, make sure that the automounter process is running.

---

### Post by dentaku65 on 2007-04-27
> **dcstar said:**
> Works fine for me, make sure that the automounter process is running.


How can I check the automounter process?

---

### Post by dentaku65 on 2007-04-27
...anyway it's weird!
I have an external USB drive (vfat) and an external USB CD-DVD-RW drive and they are not automounted (or mouted for the CD drive); to use them I have to switch off and then on again and the system recognize them... ant hint?

---

### Post by dentaku65 on 2007-04-27
ok, I fill as bug on launchpad...

[https://bugs.launchpad.net/ubuntu/+bug/110555](https://bugs.launchpad.net/ubuntu/+bug/110555)

---

### Post by xe1ufo on 2007-05-14
After trying a dozen other things, what brought my automounting of my external hard drives back to normal was removing the Automatox read/write NTFS and FAT32 Mounter. Now my external USB drives automount without a problem!!!

:popcorn:

---


---
title: "[SOLVED] ata3.00: status: { DRDY } for the past 30 minutes"
date: 2008-07-01
forum: Desktop Environments
---

### Post by Jordanwb on 2008-07-01
I started up my desktop PC at around 8:40 AM. Now it's 9:11AM and it's stuck at:

```

* Checking root file system...
fsck 1.40.8 (13-Mar-2008)
[   86.288816] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   86.288873] ata3.00: cmd c8/00:08:cd:9e:81/00:00:00:00:00/ec tag 0 dma 4096 in
[   96.288921] ata3.00: status: { DRDY }

```

Plus the hard drive light is on. I did do a google search and it occured with users with SATA hard drives. I have two SATAs.

[Edit]

I think my hard drive just died. I shutdown my computer and now it says it only detected my 160 GB and my 40GB hard drive, but not the 320GB drive which happens to have both XP and Ubuntu on it.

---

### Post by koslayn on 2008-07-17
I have the same problem (
How can you SOLVED it ?

---

### Post by Jordanwb on 2008-07-17
I really didn't. I forced the computer to shutdown, then I started having hard drive problems.

---

### Post by dreadmeat on 2008-07-17
i believe i had this error too.
using [Xubuntu] 8.04 at the time, caused so much grief i killed it and installed [Xubuntu] 7.01 instead.

---

### Post by koslayn on 2008-07-18
AHCI on in bios/ it reduce erros which I have
if you have windows on your hdd:
[http://www.neowin.net/forum/lofiversion/index.php/t457699.html](http://www.neowin.net/forum/lofiversion/index.php/t457699.html)

---

### Post by chriweis on 2008-12-11
It's weird ... I had the same issues and as soon as I took the empty CD-RW out of the CD drive everything worked fine again. Hope that helps other people, too ... maybe you should also take out the USB devices.

---


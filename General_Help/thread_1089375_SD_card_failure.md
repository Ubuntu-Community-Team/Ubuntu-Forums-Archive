---
title: "SD card failure"
date: 2009-03-07
forum: General Help
---

### Post by ugm6hr on 2009-03-07
I use an 8GB SD card with my Dell Mini 9, and think there is a hardware fault with the SD card.

I just want 2nd opinions to back me up, in case there is a problem returning it.

The SD was used as default with fat32.  Files remained accessible, but it failed to automount on startup (which it had always previously done).  It was also not recognised unless I removed and reinserted it.  Additionally, all the files on there were corrupted (OO.org files had to be recovered, or had an Input/Output error and media files were unrecognisable by Totem-Gstreamer).

At this stage, Windows XP did not even recognise the card existed.

I tried both fdisk and cfdisk, trying to write a new partition table (they both complained that none existed).  They went through the motions, but writing a new table had no effect (exiting and restarting fdisk / cfdisk resulted in the same complaint).

I then tried zero-ing the SD with dd (dd if=/dev/zero of/dev/mmcblk0) and left it running for 12 hours.  It still hadn't finished by that time, and I cancelled with Ctrl+C.  It stated that 4100 (ish) MB had been copied.

I then used testdisk, which when analysing the disk did this:

```
Disk /dev/mmcblk0 - 8017 MB / 7646 MiB - CHS 244672 4 16
Analyse cylinder 135367/244671: 55%
Read error at 135366/2/1 (lba=8663456)
```

This sounds like there is a hardware fault at this cylinder, which is presumably what caused dd to write only 4100(ish) MB to the card.

---

### Post by LoneWolfJack on 2009-03-07
you appear to be a pretty patient person. I would have returned the card at the first read/write error, which is also what most people would do, just telling the sales guy that this thing "doesn't work"... if you tell them what your wrote here, there shouldn't be any trouble at all with returning it.

---

### Post by fragos on 2009-03-07
I'd try doesn't work 1st and only get into detail if they balk at the exchange. Not all sales people are savy with what they sell. I always spoon feed them hoping to get a resolution before the deer in the headlights look takes over.

---


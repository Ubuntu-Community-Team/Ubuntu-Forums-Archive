---
title: "SD Media Drive Missing on Dell Mini 9 (Lucid)"
date: 2010-07-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bhadams1 on 2010-07-08
My SD drive is missing, and I cannot figure out how to get it back.  Anyone have any suggestions?

I am using:
- Dell Mini 9
- Ubuntu 10.04 / Kernel generic 2.6.32-23
- 1MB RAM / 8GB SSD
- With a built-in SD card mount (which is now missing)

---

### Post by anjilslaire on 2010-07-09
Try ejecting & reseating it, or rebooting it with it already inserted. I've seen that happen to mine ocasionally. After updating to bos A06 it seems to be better. Instructions here: [http://anjilslaire.wordpress.com/2010/07/08/bios-a06-updated-on-mini-9-sans-windows/]("http://anjilslaire.wordpress.com/2010/07/08/bios-a06-updated-on-mini-9-sans-windows/")

---

### Post by ugm6hr on 2010-07-10
Post output from:
```
sudo fdisk -l
```

---

### Post by bhadams1 on 2010-07-10
Thanks anjilslaire, but it's a no go here :(

Thank you ugm6hr, but I don't quiet understand.  I went to the terminal typed the code, but this is all that happen:
[INDENT]Disk /dev/sda: 7682 MB, 7682605056 bytes
255 heads, 63 sectors/track, 934 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x80d78fd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         887     7124796   83  Linux
/dev/sda2             888         934      377527+   5  Extended
/dev/sda5             888         934      377496   82  Linux swap / Solaris
[/INDENT]

So the code allows me to see it within the terminal but not under the files.

I am still unable to recover the drive.  Do you have another suggestion or more guidance?

---

### Post by ugm6hr on 2010-07-12
> **bhadams1 said:**
> So the code allows me to see it within the terminal but not under the files.

I am still unable to recover the drive.  Do you have another suggestion or more guidance?

Actually, you can't see any SD cards there. Your output refers to the internal SSD.

Hence, the possibilities are that the SD card is broken, or your SD card reader is broken - assuming the SD card was in its reader when you ran the command (and there are no issues with electrode contact etc).

Try a different SD card in the machine, and run the command again, or try the SD card in a different (working) machine to see id it is recognised.

---

### Post by bhadams1 on 2010-07-12
Well, ugm6hr that solved the problem and another one started (sort of).

I was using a Micro SDHC 8GB (with the SD Adapter).  Before starting up the netbook, I'd inserted a regular SD card, the netbook recognizes it--So no problem.

So safely removed it and re-inserted the Micro SDHC, and of course, it was a no-go: even using a different adapter and using a different Micro SDHC.

So the netbook will recognize a regular SD card but not no more Micro SDHC.

The original Micro SDHC is corrupted, but the netbook will only read the other SDHC with a USB reader.

But that's okay--I can use a regular SD card in the built in reader.

I'm curious why the SD card reader no longer accept the SDHC?

---

### Post by ugm6hr on 2010-07-13
Maybe the SDHC adapter is faulty?

Otherwise I have no idea.

---


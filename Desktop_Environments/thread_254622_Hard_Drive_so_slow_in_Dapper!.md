---
title: "Hard Drive so slow in Dapper!"
date: 2006-09-10
forum: Desktop Environments
---

### Post by newman on 2006-09-10
I can't figure out why my second hard drive is so slow.  I have two seagate 7200 RPM PATA drives each set to master with UDMA cables on seperate motherboard onboard IDE controllers. I have no slave devices connected to them.  Motherboard is ECS  with VIA KT333 & VT8235 chipset supporting UDMA133 ATA. 


this is what I'm getting:


kevin@kevin-desktop:~$ sudo hdparm -t /dev/hda

/dev/hda:
 Timing buffered disk reads:  160 MB in  3.00 seconds =  53.33 MB/sec
kevin@kevin-desktop:~$ sudo hdparm -t /dev/hdc

/dev/hdc:
 Timing buffered disk reads:   20 MB in  4.50 seconds =   4.44 MB/sec
kevin@kevin-desktop:~$

---

### Post by newman on 2006-09-10
Oh, and both are formatted with EXT3 FS if that matters...

---

### Post by ajgreeny on 2006-09-10
Why is your second drive hdc (which is usually a cdrom/optical drive) and not hdb, as I would expect it to be.  If it was a cdrom drive then the slow speed would be expected, but hard drives should be the same fast speed.  Surely there is no system setting which automatically makes hdc act as a cdrom drive, is there?

---

### Post by tuxinvader on 2006-09-10
You should check if DMA is enabled.

hdparm -d /dev/hdc

These will give you some clues too. run the -i and check for the UDMA mode being used.

hdparm -i /dev/hdc
hdparm -I /dev/hdc

---

### Post by brucevangeorge on 2006-09-10
> **tuxinvader said:**
> You should check if DMA is enabled.

hdparm -d /dev/hdc

These will give you some clues too. run the -i and check for the UDMA mode being used.

hdparm -i /dev/hdc
hdparm -I /dev/hdc

Why does this not work for me? Whenever I try these commands, it says "No such file or directory found"

---

### Post by brucevangeorge on 2006-09-10
NVM, I had to go hdb instead of hdc.

---

### Post by newman on 2006-09-10
> **newman said:**
> Oh, and both are formatted with EXT3 FS if that matters...
I did have a dvd drive connected as a slave to the first hard drive - that's why my drives are hda and hdc.  The dvd drive was hdb.  But that doesn't explain why hdc is so slow!

DMA is on.

---

### Post by newman on 2006-09-13
I removed all my drives from the system. I installed hdc as hda now and it is the only hard drive in my system and set as master on IDE 1.  DVD writer is master on IDE 2. I reinstalled xubuntu on hda and I'm getting :

kevin@kevin-desktop:~$ sudo hdparm -t /dev/hda

/dev/hda:
 Timing buffered disk reads:   46 MB in  3.07 seconds =  15.01 MB/sec
kevin@kevin-desktop:~$


I wonder if this drive is a defect?  It is actually newer than my other drive that was faster!
What's going on here?!

---

### Post by carontis on 2006-09-13
Try to check on Seagate web site if there is an update firmware for your hdd; I know some company gives sometimes the last firmware. Probably it needs update.

---

### Post by newman on 2006-09-15
Thanks. I called Seagate and they said they don't offer firmware updates for ATA drives - only for SCSI drives.  I ran the Seagate diagnostics and it returened a hardware problem error. I sent the drive to Seagate for replacement.  I'll see if that does it...

---

### Post by newman on 2006-09-29
update:
seagate sent me a replacement refurb drive ( a bigger one :) ) and it seems to be OK now...


kevin@kevin-desktop:~$ sudo hdparm -t /dev/hda

/dev/hda1:
 Timing buffered disk reads:  188 MB in  3.01 seconds =  62.36 MB/sec
kevin@kevin-desktop:~$ sudo hdparm -t /dev/hda

---


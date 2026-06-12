---
title: "The quick demise of a fresh install"
date: 2006-09-15
forum: Desktop Environments
---

### Post by flummoxed on 2006-09-15
Ok, so I installed Dapper about 5 days ago or so, on one of my two 80GB hard drives (S-ATA). Windows is installed on my master IDE drive. I decided to be fancy while I was paritioning, and I made the / partition formatted in ReiserFS, because I remember hearing somewhere that ReiserFS could give you a speed advantage. Anyways, I figured it wouldn't made a difference, and I might as well try something exotic. Well, I noticed problems, often while doing something like downloading torrents, that all gnome applications would start going really sloowwwww, and somtimes after a minute or two things would go back to normal, but other times a CTRAL + ALT + BACKSPACE was in order, or a ALT + SYS + RSEIUB to completely restart the system. Well, the file system finally gave out. Now it won't boot at all, it gets halfway through the loading screen, and when it gets to checking file system, it says

ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x11/04

and 

Buffer I/O error on device sda8, logical block 10262

repeatedly. Is there any way to save my install without having to start from scratch, or should I have just avoided the Reiser and stuck with good old ext3, so now I have to start all over again? I have the / and /boot partitions separate from the /home partition.

---

### Post by slimdog360 on 2006-09-15
you can boot with the live cd mount the /home partition and save the files that way. But yeah from what it sounds like you need a reinstall.

---


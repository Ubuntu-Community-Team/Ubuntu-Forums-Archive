---
title: "Ubuntu 10.04 through 11.10 fail at partitioning stage on PERC 4/DI"
date: 2012-01-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dchurch24 on 2012-01-21
Hi,

I'm completely stuck. I've been given a Dell Poweredge 2800.

I have set the RAID up as two RAID 0 - giving 219gb on one and 297 on another.

The installer sees both of these as harddrives. 

No matter what I do, I cannot get Ubuntu installed on it.

It simply fails after waiting a very long time with the error:

The ext4 file system creation in Partition #1 of SCSI3 (2,0,0) (sda) failed.

I get no further error and I have tried all versions from 10.04 (Desktop) to 11.10 (including Desktop/Server/Alternate versions).

I've even tried Mythbuntu and Mythdora.

I've been trying for a week now, and have read around the forum and the general consencus is that it should just simply install without problem.

Booting to live and opening GParted gets me "No devices detected", yet the Disk Utility sees them both, but can't format them. If I try to delete the partition (although what partition I don't know as it fails every time when trying that step), then I get the error message "Daemon is inhibited".

---

### Post by dchurch24 on 2012-01-21
I've tried Mint and Debian as well now.

I've also tried using just 1 disc.

Nothing wants to install on this thing.

---

### Post by dchurch24 on 2012-01-21
I've come to the conclusion that Linux does not work with this hardware.

Windows installs fine on it, which is a shame because I don't need that.

It's going to have to go in the bin...if I can lift it ;-)

Dell....if you're listening....make your hardware compatible with serious operating systems!

---


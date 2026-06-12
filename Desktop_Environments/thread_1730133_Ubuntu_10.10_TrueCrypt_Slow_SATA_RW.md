---
title: "Ubuntu 10.10 TrueCrypt Slow SATA R/W"
date: 2011-04-15
forum: Desktop Environments
---

### Post by addux on 2011-04-15
I have a default install of Ubuntu 10.10 and am trying to use TrueCrypt on my internal SATA HDD's.  In windows and Debian I can get R/W speeds @ 60MB/s (with TrueCrypt) but with Ubuntu I see only 20MB/s, consistently.  Strangely, though, I have seen 60MB/s on a few occasions with Ubuntu.
I have tried using IDE emulation and SATA RAID via my motherboard with the same results.  I specify using TrueCrypt because if I use the Disk Utility to perform benchmarks, its reports show a R/W speed around 64MB/s.  I understand TrueCrypt can slow drive R/W, but as I have said the same drive reads @ 60MB/s on Windows 7 and Debian testing.  I like Ubunutu but like it is times like this I want to go back completely to Debian!!  Any help would be appreciated.
Steve

---

### Post by addux on 2011-04-16
As a sort of update, I also tried copying from SATA drive to SATA drive, @ 30MB/s in ubuntu and 60MB/s in Debian.  Maybe this is a kernel module issue?

---

### Post by bcarlowise on 2011-04-21
I also use truecrypt and typically see approx. 20MB/sec transfer rate but I use external encrypted drives to backup my data to. I don't have any of my internal drives encrypted with Truecrypt....I use the functionality within Ubuntu to encrypt my home folder which is a separate partition on my hard drive.

---


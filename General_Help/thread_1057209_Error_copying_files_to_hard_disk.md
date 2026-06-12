---
title: "Error copying files to hard disk"
date: 2009-02-01
forum: General Help
---

### Post by MatthewHIrst on 2009-02-01
I keep getting a problem when trying to install Ubuntu
It says this message:

'The installer encountered an error copying filed to the hard disk:
[Errno 5] Input/output error

This is often due to a faulty CD/DVD Disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed'

I've tried this on 2 computers, so it can't be the hard drive, Yet i've burnt it at different speeds on about 6 disks.

Yet the problem continues to persist. 

Thanks in advance for the help

---

### Post by cmnorton on 2009-02-02
When you download an ISO image, there are usually two files at the site. One is small in size and contains the MD5 checksum for the ISO image. The other file is the ISO image. You need to download both. 

Once you've downloaded the ISO image, compute the MD5 checksum on the ISO image using the command md5sum, and here is the chicken and egg problem. You are trying to install a system, so you'll have to compute the checksum on another system, the one two which you downloaded the ISO image.

As a quick diagnostic, can you boot any of these systems with the live CD? And, if you can boot these systems with the live CD, can you mount the drive or drives?

---


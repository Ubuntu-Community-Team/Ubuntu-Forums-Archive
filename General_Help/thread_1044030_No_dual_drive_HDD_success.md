---
title: "No dual drive HDD success"
date: 2009-01-19
forum: General Help
---

### Post by Drawstop on 2009-01-19
I have a drive with Windows 2000 installed - only used to drive my scanner. I have tried to install Ubuntu on this drive but it will not install. I am told either there is not enough room (30G not enough!!!) or it cannot partition. On my laptop I have XP and Ubuntu so is there some technical reason that Ubuntu will not install with 2000 as a dual drive HDD?
Many thanks for any help.

---

### Post by wjp.reg on 2009-01-19
Did you leave any free space on the drive?  Are you wanting to replace windows 2000 on the drive?  More info...?

---

### Post by vanadium on 2009-01-19
It is probably your current partitioning that does not allow the automatic procedure to create two new partitions. You probably will need to do some manual adjustments first, or eventually do the entire partitioning manually.

Can you post the output of "sudo fdisk -l". This shows your current partitioning and will allow me to see if my assumption is right, and what manual adjustments eventually will be possible to accommodate for two more partitions.

---


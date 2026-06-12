---
title: "Failed to boot after adding harddisk"
date: 2009-05-13
forum: General Help
---

### Post by calvinchu on 2009-05-13
I am new to Linux and I installed Ubuntu 9.04 in a harddrive connecting to 4th SATA port of my mobo. The drive was /dev/sdc at installation time because I have 2 other drives in 2nd and 3rd SATA ports as well. And Ubuntu works fine until I plug another harddisk to the 1st SATA port, it fail to boot.

I guest it is because my boot device was changed to /dev/sdd when disk is added. Is it ? How can I fix this ? Thank you very much !

---

### Post by khantastic on 2009-05-13
There are many ways on how to fix this, but I would put the ubuntu-disk at SATA1, assuming the ubuntu-disk has the boot-loader grub installed. Then I would edit grub.conf to also include booting from other drives.

---

### Post by louieb on 2009-05-13
Exactly what happens when you boot? Any messages? 

Ubuntu should handle the new drive without problems. But the GRUB boot loader depends on boot order to tell which disk is which.  Grub sometimes has a problem when drives are switched around or added.

Quick fix get  a [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") and see if it can sort it out and get the PC to boot again.

If you still need help follow the instruction here [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")  and post the results.txt file.

---


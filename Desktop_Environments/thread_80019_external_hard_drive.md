---
title: "external hard drive"
date: 2005-10-21
forum: Desktop Environments
---

### Post by thrust on 2005-10-21
i have an external HD enclosure with a WD hard drive in it. ubuntu to finds the hard drive no problem but i cant write to it. i also have a usb flash drive and i can write to that fine, i thought it would be the same with the HD does anybody have any sugestions 

i would really like to have some feedback 

thx

matthew

---

### Post by adriantry on 2005-10-21
Is it formatted NTFS? Linux can't write to NTFS volumes.

I've formatted mine FAT32 so it can be read by Linux, Mac and Windows.

---

### Post by irv on 2005-10-21
I was dealing with this same issue yesterday, and my problem was the NTSF format. I have a new thread:

 [http://ubuntuforums.org/showthread.php?t=80086](http://ubuntuforums.org/showthread.php?t=80086) 

where I am looking for more answers on NTSF and Linux. I may just move some files off the USB Hard Drive, re-format Fat32 and then move them back to work around this problem.

---


---
title: "How can I test SD / MMC / CF cards for defective flash memory?"
date: 2009-01-31
forum: General Help
---

### Post by scotty64 on 2009-01-31
I have an SD card, and I am not sure if it is "ready for the bin". Is there any way on Ubuntu to test flash devices? I am looking for something like memtest86 for RAM, but for flash devices.

---

### Post by asashnov on 2009-09-23
**badblocks -w /dev/sdX**
do something similar, but it not detects error on my broken USB flash drive.

Also may try 
**dd if=/dev/zero of=/dev/sdX**  and
**badblocks -p 7 -s -v -w -t random /dev/sdX**

where /dev/sdX is a USB flash drive (insert it and look into dmesg output).

---


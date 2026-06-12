---
title: "Tricky back-up question!"
date: 2006-02-23
forum: Desktop Environments
---

### Post by Gnobody on 2006-02-23
I have a partition for another computer backed-up as a compressed Norton Ghost image, and I was wondering if there is a way I could extract, convert, or write the image to a partition from Linux.  I don't have Windows or Norton Ghost, don't ask!  I have tried partimage but it segfaults when I try to load the image to an empty partition.

---

### Post by lamego on 2006-02-23
I don't believe you can achieve that without norton ghost, ghost explorer or another comercial software with norton ghost image support..

---

### Post by Gnobody on 2006-02-23
Wow, that sucks...  I've googled it to no avail too!

---

### Post by ardchoille on 2006-02-24
1) Download a copy of the [System Rescue LiveCD]("http://www.sysresccd.org/Main_Page") and burn it to a CD.

2) Boot into system rescue cd and type "fb1024 nokeymap" (without quotes) at the boot line. You can press F2, F3 or F4 to get more boot options.

3) when the shell prompt comes up (this is just an example)
```

mkdir /mnt/work
mount /dev/partition/to/hold/image /mnt/work

```
change the above to suit your needs and be sure to read the docs for system rescue cd.

4) mount the partition you want where you want to put the image into the mount point you specified above. You must unmount the partition you want to image and mount the partition where the image file is going to be placed.
Example:
 /dev/hda1 - unmounted - partition to be imaged
 /dev/hda2 - mounted - partition to hold the image file

5) type partimage to run partimage and you should be able to image your partitions.

This works great for all 11 of my machines and is the primary way I install Linux on multiple machines - install Linux on one machine, install all updates and patches, tweak the system, image the partitions and use those images to install Linux on other machines. Imaging a fresh Ubuntu 5.10 install takes about 10 minutes and restoring that image takes about 12 minutes. I usually burn the images to a DVD-R in case anything happens to the hard drive.

---


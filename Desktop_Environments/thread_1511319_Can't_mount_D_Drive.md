---
title: "Can't mount D Drive"
date: 2010-06-16
forum: Desktop Environments
---

### Post by clayman1000x on 2010-06-16
I just reinstalled Ubuntu 10.04 because of problems with windows. I can see both my drives with gparted, but I cannot mount the d drive, I put the Ubuntu install next to windows on the c drive but last time I installed 10.04 I could see my d drive, that is where all my music and .avi files are located. I get an error when trying to mount this drive:
Unable to mount Drive D
Error mounting: mount exited with exit code 12: Failed to read last sector (976773096): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

It _is_ (was) an NTFS format by the way.

Just found out that after the 10.04 install, my d drive was wiped out, any way of getting those files back? I haven't formatted yet with windows. Windows needs to format it and Ubuntu can't mount it, it is nowhere land.

---

### Post by clayman1000x on 2010-06-18
Hello, I also have a lot of other issues with Ubuntu 10.04 at this time. Is anyone even here?

---

### Post by oldos2er on 2010-06-18
Are you using RAID? You can try testdisk for file recovery. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by clayman1000x on 2010-06-18
> **clayman1000x said:**
> Just found out that after the 10.04 install, my d drive was wiped out, any way of getting those files back? I haven't formatted yet with windows. Windows needs to format it and Ubuntu can't mount it, it is nowhere land.

I have my d drive back now, I used a program called "GetDataBack" to recover files on the drive, the only problem I had was I could not save the files over a network, I had to recover the files to my c drive, (only 65g of space on c drive, and over 400g to recover) then move the files from c drive over my network to another drive on 2 other computers, then move them back after formatting D again, a lot of work but it is done.
When I was last in Ubuntu, the screen was all messed up, I could not see the bottom of the pages I had open but could not move it up enough to get to the buttons at the bottom.
Oh, no raid.

---


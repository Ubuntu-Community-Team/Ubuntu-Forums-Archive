---
title: "Error reading CDs burned using Windows XP / Nero 6"
date: 2006-06-13
forum: Desktop Environments
---

### Post by darrenst on 2006-06-13
I'm having problems copying disks that I have created in Windows XP.

The CD described below is a copy of the Ubuntu Live CD burned using Nero 6 on Windows XP straight from the downloaded image. I wondered if it might be because this was a bootable CD. However, I have found the same with any old backup CD (drag and drop style) I previously created in Windows.

The GUI hangs for ages, but on further investigation behind the scenes, the "readcd" command is the underlying problem.

It basically runs very quickly to the end of the disk, but then hangs for ages on one of the very last sectors. I've included a dump of what it says below.

I downloaded the same image again into Ubuntu, and burned it using the right click / Burn to Disk option. Copying this one using the default Nautilus copy worked absolutely fine.

I only found this out when a mate at work expressed an interest in Ubuntu Dapper Drake, and I said I would copy my disk for him, the one I downloaded in Windows XP and used to convert to Ubuntu a little over a week ago (and haven't looked back yet!) I then found it was quicker to download the image again and re-burn it, compared to the length of time the copy of the Windows burned one hung around during the copy process.
 
Is there some strangeness in Windows burned disks? I had a hunt about on these forums and didn't see anyone else mention this.

Grateful for any assistance. The output of the readcd command is below.

Cheers,

Darren

---

darren@ubuntu-desktop:~$ readcd -dev=/dev/hdc -f=/home/darren/CopyCD/Ubuntu_6.06_i386.iso
Read speed: 7056 kB/s (CD 40x, DVD 5x).
Write speed: 5644 kB/s (CD 32x, DVD 4x).
Capacity: 357297 Blocks = 714594 kBytes = 697 MBytes = 731 prMB
Sectorsize: 2048 Bytes
Copy from SCSI (1,0,0) disk to file '/home/darren/CopyCD/Ubuntu_6.06_i386.iso'
end: 357297
readcd: Success. read_g1: scsi sendcmd: no error
CDB: 28 00 00 05 73 80 00 00 31 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 03 00 05 73 B0 0E 00 00 00 00 11 05 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x11 Qual 0x05 (l-ec uncorrectable error) Fru 0x0
Sense flags: Blk 357296 (valid)
resid: 100352
cmd finished after 5.918s timeout 40s
readcd: Success. Cannot read source disk
readcd: Retrying from sector 357248.
.................................................~ ~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~
readcd: Success. Error on sector 357296 not corrected. Total of 1 errors.

Time total: 1067.641sec
Read 714496.00 kB at 669.2 kB/sec.
Max corected retry count was 0 (limited to 12.
The following 1 sector(s) could not be read correctly:
357296
darren@ubuntu-desktop:~$

---


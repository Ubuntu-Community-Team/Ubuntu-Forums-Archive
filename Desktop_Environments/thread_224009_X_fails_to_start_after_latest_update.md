---
title: "X fails to start after latest update"
date: 2006-07-27
forum: Desktop Environments
---

### Post by cybertoast on 2006-07-27
(amd64, running dapper 6.06 w/ latest updates, ati x600 video using proprietary ati drivers)
my system was working fine until i installed the latest updates (7/26/06). When i rebooted the system, x no longer will start up. When i try to do a dpkg-reconfigure xserver-xorg, I get the following:
```
[ 947.572010] attempt to access beyond end of device
[ 947.572047] sda2: rw=0, want=6478643248, limit=39070080
[ 947.572079] attempto t access beyond end of device
[ 947.572109] sda2: rw=0, want=6478643248, limit=39070080
Bus error

```

My xorg.log.0 does not really reveal anything that i can decipher as the problem (and it's really long so i'm hesitant to post it here, but will do so if it's useful). Anyway, the system boots fine into windows, so i don't think there's a problem with the video card.

i'm not really sure what the next step i should try is (i'd rather not go through the process of re-installation again). i'd be grateful for any suggestions or ideas.

cheers

---

### Post by x64Jimbo on 2006-07-27
sda2 refers to your SCSI/SATA/USB hard disk. From the looks of that error, there's something screwy with your partitions. You may also want to check your cables to see if maybe one of them jiggled loose. Beyond that, I'm afraid I am not sure where to look, but maybe this will get you a jumpstart on the solution.

---


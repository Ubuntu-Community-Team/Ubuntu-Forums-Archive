---
title: "Help! Mounting Encrypted HDD using devicemappers"
date: 2006-08-20
forum: Desktop Environments
---

### Post by BuggyDE on 2006-08-20
Hi,

I have 3 HDDs in my system I have encrypted them all using the method I found here 

[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

Now 2(hda, hdd) of the drives mount alright after a reboot but one(hdb) of my drives will not.  When I look at the /dev/mapper/crypt* I find that the devicemapper is not there even tho I did create it and the drive worked fine until the reboot.

I have tried to re-create the devicemapper but the I get an error mounting the drive about using the incorrect file system.  How can I add the devicemapper and mount this drive on my system?  I use to be able to move encrypted drives between systems when I used red hat via a loopback system.

Thanks.

---


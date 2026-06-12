---
title: "File system check failed"
date: 2009-01-02
forum: General Help
---

### Post by dishbert on 2009-01-02
I tried to boot back into a previous version that has worked for me for a year or 2, only to get this message.

checkfs from /var/log/fsck shows this:

Log of fsck -C -R -A -a 
Tue Dec 30 16:35:36 2008

fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hdb5: 5332 files, 821068/1979543 clusters
fsck.ext3: Unable to resolve 'UUID=4de7a075-24f4-4d3b-a14c-4b4eb051f1b0'

fsck died with exit status 8

Is this a hard drive issue?

---

### Post by cariboo on 2009-01-02
Boot up using the LiveCD and manuannly run fsck of drive /dev/hdb5, open a terminal and type:

```
sudo fsck /dev/hdb5
```

For some reason fsck couldn't fix the drive automatically so you have to run it manually.

Jim

---

### Post by mcduck on 2009-01-02
Actually the check for /dev/hdb5 completed succesfully, but the next check failed because the drive specified in /etc/fstab couldn't be found.

Perhaps you have installed a new OS, or in some other way edited your partitions since installing that Ubuntu version? This has caused a partition's UUID to change, but the fstab still has old UUID so fsck fails.

Check the correct UUIDs for all your partitions with the "blkid"-command, and then edit /etc/fstab to use those UUIDs.

---

### Post by dishbert on 2009-01-02
Hi mcduck, you are correct, I've installed a newer version since the one that fails, but I'd like to continue to be able to boot to both if I can.

The output of blkid -c -o is:

<device DEVNO="0x0801" TIME="1230623452" UUID="30E052A6E05271D8" TYPE="ntfs">/dev/sda1</device>
<device DEVNO="0x0805" TIME="1230682624" UUID="ddf7a82e-ebca-4dfe-b571-6bb568be614d" TYPE="ext3">/dev/sda5</device>
<device DEVNO="0x0806" TIME="1230623452" UUID="ce4c935c-cf7d-43bd-9b2b-5b5784b6a460" TYPE="swap">/dev/sda6</device>
<device DEVNO="0x0811" TIME="1230623452" UUID="6250A65050A62B2D" LABEL="DRV2_VOL1" TYPE="ntfs">/dev/sdb1</device>
<device DEVNO="0x0815" TIME="1230623452" LABEL="DRV2_VOL2" UUID="28A6-7066" TYPE="vfat">/dev/sdb5</device>
<device DEVNO="0x0816" TIME="1230623452" UUID="5abfeabc-da4d-4967-a437-bff031d40a6a" TYPE="swap">/dev/sdb6</device>
<device DEVNO="0x0817" TIME="1230623452" UUID="e2403509-f653-4629-b811-bdf97817707d" SEC_TYPE="ext2" TYPE="ext3">/dev/sdb7</device>
<device DEVNO="0x0700" TIME="1230623452" TYPE="squashfs">/dev/loop0</device>
<device DEVNO="0x0821" TIME="1230623452" UUID="DAB48589B48568B9" LABEL="FreeAgent Drive" TYPE="ntfs">/dev/sdc1</device>

And the content of /etc/fstab from the OS that won't boot is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb7
UUID=e2403509-f653-4629-b811-bdf97817707d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=30E052A6E05271D8 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda3
UUID=4de7a075-24f4-4d3b-a14c-4b4eb051f1b0 /media/hda3     ext3    defaults        0       2
# /dev/hdb1
UUID=6250A65050A62B2D /media/hdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdb5
UUID=28A6-7066  /media/hdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=1e7ebb99-921f-4e42-b563-b76d2b9f917b none            swap    sw              0       0
# /dev/hdb6
UUID=5abfeabc-da4d-4967-a437-bff031d40a6a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


There seem to be several differences and I'm not sure which to change.  Or perhaps you meant the /etc/fstab file in the new OS?

---

### Post by dishbert on 2009-01-02
Solved, thanks mcduck, I put up the fstab file side by side with the blkid output and made a guess about which UUID do change and got lucky.

I almost always have a couple of versions of Ubuntu running on the same machine and this is the first time this has happened.  They must have made a change with Hardy that broke this protocol.

---

### Post by mcduck on 2009-01-03
Yeah, at some point the developers started using UUIDs in fstab instead of pointing to disks with their device names (like "/dev/hda"). This means that you can freely move your disks to different cables etc, and they will still be detected correctly, but as any changes to partitions will cause the edited partitions UUID to change you need to remember to fix the fstab..

Using UUIDs still makes sense, as that allows you to also define mount options for removable drives in fstab, and also fixes the issue some people have with their hard drives being detected in different order at every boot causing the drive that was /dev/hda on last boot to become /dev/hdb on next one. Plugging in removable drives while booting can also change the names of the drives depending on the order in which the drives are detected, and using UUIDs in fstab solves this problem as well. So the only actual downside of UUIDs is that they change if the partitions are edited, which is something most people don't really do that often.

---


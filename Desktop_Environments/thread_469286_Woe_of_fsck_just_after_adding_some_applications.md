---
title: "Woe of fsck just after adding some applications?"
date: 2007-06-09
forum: Desktop Environments
---

### Post by Nanoboy on 2007-06-09
I feel helpless...

All I have done was installing a few auto-updates of linus as routinely checked by the update manager, which after downloading required restart afterwards.  But before I restart, i was reading lifehacker website and followed a few suggestions on the "Top 10 apps on Ubuntu" and installed a few applications.

Then I restarted my laptop, and fsck appeared to have been messed up.  The log reads:
```
fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda1: 88 files, 3627/36051 clusters
/dev/sda3: clean, 7973/7094272 files, 720233/14161297 blocks
fsck.ext3: No such file or directory while trying to open /dev/hda3
/dev/hda3:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

```

I typped in reboot which allowed me to boot into Ubuntu and log in to a clean desktop environment, i.e. without my own /home directory or my settings.  My /home is on a separate partition on /dev/hda3.  I'm not very familiar with what ext3 and ext2 (as stated by fsck above) really means.  I dual boot with Windows, which is on /dev/hda2.  My file system and swap is on /dev/hda5.

For information, output of my fstab is:
```
# /dev/hda5
UUID=8c9f2871-4d83-4f5d-a026-a4e3834d0e96 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1
UUID=07D4-0914  /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda2
UUID=7228767B28763E63 /media/sda2 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Taken this bit out of the original line above after defaults: nls=utf8,umask=$

# /dev/hda3
# changed 2 to a 1, replaced the end bit: defaults,errors= with rw,user
UUID=ee111eb8-32ef-4a7e-b80c-3b545d20afab /media/sda3 ext3 rw,user 0 1

# /dev/hda6
UUID=5928264c-237a-4a61-9318-cc92079c4517 none swap sw 0 0

# Taken this line out: /dev/scd0, replaced with /dev/cdrom as below :
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0

# added from old fstab directory
# Specify /home directory to use from the /sda3 partition :
/dev/hda3 /home ext3 nodev,nosuid 0 2

```

And my blkid:
```
/dev/sda2: TYPE="ntfs" 
/dev/sda3: UUID="ee111eb8-32ef-4a7e-b80c-3b545d20afab" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="5928264c-237a-4a61-9318-cc92079c4517" TYPE="swap" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DELLUTILITY" UUID="07D4-0914" TYPE="vfat" 
/dev/sda5: UUID="8c9f2871-4d83-4f5d-a026-a4e3834d0e96" SEC_TYPE="ext2" TYPE="ext3" 

```

Any help to get my system back to what it was before would be greatly appreciated.  Feeling despair.  I hope I won't need to re-install Ubuntu.  Thanks.

---

### Post by Nanoboy on 2007-06-09
*bump*

---

### Post by Nanoboy on 2007-06-09
And I ran fsck on the Windows partition from terminal. 

```

jack@hedgehog:/$ sudo fsck /dev/hda2
Password:
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: No such file or directory while trying to open /dev/hda2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;

```

What's gone wrong?

---

### Post by VirtualTiger on 2007-06-10
I just had the same problem after upgrading to the latest kernel.

I was able to fix it by changing /etc/fstab.

Old Entry:
```
# Entry for /dev/hda3 :
/dev/hda3 /home ext3 nodev,nosuid 0 2
```

New Entry:
```
# Entry for /dev/hda3 :
UUID=b7795430-50f6-4457-a141-1145d02ca147 /home ext3 defaults,errors=remount-ro,data=writeback,noatime 0 1
```

I hope this helps.

---

### Post by Nanoboy on 2007-06-10
Thanks VirtualTiger!!

Just copied your line into my fstab (with my own UUID of course :p), and now it's back to normal, yay!!

Kernel upgrade problem!

---

### Post by VirtualTiger on 2007-06-10
Great, I'm glad it worked for you as well.

---

### Post by mcduck on 2007-06-10
> **Nanoboy said:**
> 
For information, output of my fstab is:
```
# /dev/hda5
UUID=8c9f2871-4d83-4f5d-a026-a4e3834d0e96 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1
UUID=07D4-0914  /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda2
UUID=7228767B28763E63 /media/sda2 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Taken this bit out of the original line above after defaults: nls=utf8,umask=$

# /dev/hda3
# changed 2 to a 1, replaced the end bit: defaults,errors= with rw,user
UUID=ee111eb8-32ef-4a7e-b80c-3b545d20afab /media/sda3 ext3 rw,user 0 1

# /dev/hda6
UUID=5928264c-237a-4a61-9318-cc92079c4517 none swap sw 0 0

# Taken this line out: /dev/scd0, replaced with /dev/cdrom as below :
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0

# added from old fstab directory
# Specify /home directory to use from the /sda3 partition :
/dev/hda3 /home ext3 nodev,nosuid 0 2

```


By the way, only / partition should have '1' as the last number in it's entry. For all other partitions you should use either '2' (to check the partition after /) or '0' (to not run fsck at all for the partition).

I recommend using a '0' for all FAT/NTFS partitions

---


---
title: "RAID devices not mounting after upgrade"
date: 2009-05-12
forum: General Help
---

### Post by m8ryx on 2009-05-12
Hello, I have had my software raid running happily in v8 for awhile, but am having trouble mounting it after upgrading.  This is not my boot disk, so I'm not sure why anything would have changed with it during an upgrade to Jaunty.


m8ryx@drunkguy:~$ ls -l /dev/mapper/
total 0
crw-rw---- 1 root root  10, 61 2009-05-12 07:31 control
brw-rw---- 1 root disk 252,  0 2009-05-12 07:31 sil_aiajbgafbgai


m8ryx@drunkguy:~$ sudo dmraid -r
/dev/sdb: sil, "sil_aiajbgafbgai", mirror, ok, 625140400 sectors, data@ 0
/dev/sda: sil, "sil_aiajbgafbgai", mirror, ok, 625140400 sectors, data@ 0

Previously, I mounted via 
/dev/mapper/sil_aiajbgafbgai1 /media/store  ext3  relatime  0  2

But that device no longer exists.  I see /dev/sda and /dev/sdb, but no /dev/sda1 and /dev/sdb1.

I tried mounting w/o the partition (sil_aiajbgafbgai):

m8ryx@drunkguy:~$ sudo mount /media/store
mount: wrong fs type, bad option, bad superblock on /dev/mapper/sil_aiajbgafbgai,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


The news from gparted isn't all that rosey.  I'm not sure where it gets its info, but it says /dev/mapper/sil_aiajbgafbgai1 is unallocated.  I get a warning viewing /dev/sda (bad superblock, no such file or directory /dev/sda1) but none when viewing /dev/sdb (unallocated).

I also see this in STDOUT on the command line:
/dev/mapper/sil_aiajbgafbgai: unrecognised disk label
/dev/sdb: unrecognised disk label


m8ryx@drunkguy:~$ sudo dmraid -r -c
/dev/sdb
/dev/sda

m8ryx@drunkguy:~$ cat  /proc/partitions |strings
major minor  #blocks  name
   8        0  312571224 sda
   8       16  312571224 sdb
   8       32   39088896 sdc
   8       33          1 sdc1
   8       34   18539010 sdc2
   8       37    4883728 sdc5
   8       38     465853 sdc6
   8       39   10273473 sdc7
   8       40    4923891 sdc8
 252        0  312570200 dm-0


I would greatly appreciate any help!  cheers.

---

### Post by fjgaude on 2009-05-12
Likely all you have to do is run this:

```
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

The issue is the upgrade changed the UUID of your array and this will put it to what it needs to be.

---

### Post by m8ryx on 2009-05-12
something's not right:
root@drunkguy:~# mdadm -v -v --examine --scan 
mdadm: No md superblock detected on /dev/block/252:0.
mdadm: No md superblock detected on /dev/sdc8.
mdadm: No md superblock detected on /dev/sdc7.
mdadm: No md superblock detected on /dev/sdc6.
mdadm: No md superblock detected on /dev/sdc5.
mdadm: No md superblock detected on /dev/sdc2.
mdadm: No md superblock detected on /dev/sdc1.
mdadm: No md superblock detected on /dev/sdc.
mdadm: No md superblock detected on /dev/sdb.
mdadm: No md superblock detected on /dev/sda.

I get no output at all w/o the 2x verbose.

thanks for the suggestion!

rick

---

### Post by ronparent on 2009-05-12
In your initial post, you indicate mounting the /dev/mapper/ symbolic link for the raid partition. This indicated you initially used dmraid to map and mount your raid partition. I guess to start at the beginning, does your raid still appear 'healthy' in the raid bios (usually seen when booting)?

---

### Post by m8ryx on 2009-05-12
it looks fine on boot.  It's reported as an SIL mirrored RAID.  I don't see any errors in the SiL bios either.  Here's some dmesg output.  Thanks again.

m8ryx@drunkguy:~$ dmesg |grep sd[ab]
[    2.996980] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    2.997012] sd 0:0:0:0: [sda] Write Protect is off
[    2.997016] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.997063] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.997182] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    2.997208] sd 0:0:0:0: [sda] Write Protect is off
[    2.997212] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.997256] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.997264]  sda: sda1
[    3.008287] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.008631] sd 1:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.008659] sd 1:0:0:0: [sdb] Write Protect is off
[    3.008663] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.008707] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.008802] sd 1:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.008828] sd 1:0:0:0: [sdb] Write Protect is off
[    3.008832] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.008875] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.008882]  sdb: unknown partition table
[    3.033377] sd 1:0:0:0: [sdb] Attached SCSI disk

---

### Post by ronparent on 2009-05-12
I admit I am stumped!!! There is nothing in an update that should affect a separate data drive. Dmraid itself is relatively passive and primarily operates by reading (discovering) the metadata on the drives. I doubt that it could inadvertently destroy a partition table (deliberately maybe). More likely that a separate partitioning operation is responsible. And for a raid1 it would have to be on both of the drives for a partition to disappear on both! If only one were partitioned than the data should remain intact on the other.

Your posts of the situation were pretty thorough incidently. Unless someone knows of how you might recover data from a lost partition there is little chance of recovering your data. Your best chance is if you do nothing else to those drives until you initiate a recovery stategy. Good luck. I regret I can't be more helpful.

---

### Post by m8ryx on 2009-05-12
is it possible that something active happens to the /media mounts during the upgrade process?

---

### Post by ronparent on 2009-05-12
That shouldn't affect anything if the metedata is intact. You would see it in /dev/mapper/. The symbolic links in the mapper location would probably just be remounted at next boot.

---

### Post by m8ryx on 2009-05-14
I picked up a copy of spinrite and if I'm reading this correctly, it is recognizing a linux partition on the RAID controller.  That was a bit unexpected ;)

---

### Post by m8ryx on 2009-05-14
Alright, this is odd.  Apparently spinrite is so powerful all it has to do is look at a drive and the drive repairs itself.  The Chuck Norris of HD recovery software.

After running spinrite (it took no discernible actions, and detected no bad blocks), I booted back into Ubuntu.  Just for kicks I checked /dev/mapper, and w00t, sitting there is sil_aiajbgafbgai1 (the 1 at the end is the important part).  I quickly modified my fstab back to the original broken state, and it is broken no more!

It's not a final solution that I'm all that comfortable with, because I don't know what the problem was, or the fix, but apparently spinrite was the answer.

cheers!  And thanks for the help.

---

### Post by m8ryx on 2009-05-14
One last piece.  After I got it up and running, it would only mount as read-only.

this was an easy, though slightly stressful, fix.  Basically, just reboot and let the boot process detect that it is unhappy with the drive(s), it should fsck for you.

I my case, fsck failed and dumped me into single user mode, and told me to run fsck w/o flags.  It also reported that my ext3 journal was corrupt and  now the fs is ext2.

So, I ran fsck /dev/mapper/blah1.

It immediately wanted to zero out the journal.  There were also some corrupted directories, and some other spew.  I just accepted everything (nervously) that it wanted to do.

Then reboot.  This was a bit buggy and scare the crap out of me briefly.  I typed reboot at the command line, at which time it booted and rebooted at the same time, dropping me at gdm (or whatever they use these days) with no mounted filesystems.  I pushed buttons until  could reboot...not sure if it sorted itself out or if I just forced the issue.

After the reboot my /media/store still wasn't there.  Weird that it didn't drop into single-user on startup.

Easy fix though.  I just edited /etc/fstab to change the fs from ext3 to ext2.

Anyways, everything appears to be working fine now.  cheers!

---

### Post by ronparent on 2009-05-14
That sounds like great news. Glad to hear that everything is spinning right!!! May try it myself for my current predictament.

---

### Post by m8ryx on 2009-05-14
apologies for using the forum in this way, but it won't allow me to send a message yet.

what's your current issue?  I didn't see any recent threads from you.  But I'm not a forum power user.  In fact, how do I add "resolved" to my thread's title?

---

### Post by ronparent on 2009-05-14
Yes, by all means mark resolved. 

My current headache is with winXP on another computer that is crashing on boot. I suspect file or disk corruption because it had been working fine to date. I hesitated to answer your post on this forum because the jibes will be forthcoming, alas. Unfortunately ubuntu 8 series won't run on that same computer because of kernel panic and 9.04 runs crippled because the ati graphic card is unssuported (ie twin view is unavailable, aspect ratio is wrong for a wide screen monitor, etc.). I guess I will have to settle for win7 on that unit.

---


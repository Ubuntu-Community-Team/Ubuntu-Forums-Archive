---
title: "Small fsck'n Ubuntu Raid / mdadm problem."
date: 2009-04-09
forum: General Help
---

### Post by Cyborg28 on 2009-04-09
Hi,

I used mdadm to clone an existing harddrive and then create a Raid 1 mirror of the drive.

Everything went perfectly. The final result is now when I check my raid health via ```
cat /proc/mdstat
``` I get this output: 
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdd1[0] sde1[1]
      488383936 blocks [2/2] [UU]

unused devices: <none>
```

Great.

Now my problem is when my system is restarted I get the error shown in the attached image.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=109233&d=1239294057[/IMG]

So I check the logfile that it tells me to go see and I see essentialy the same thing:

```
Log of fsck -C3 -R -A -a 
Tue Apr  7 22:04:47 2009

fsck 1.41.3 (12-Oct-2008)
/dev/md0: The filesystem size (according to the superblock) is 122096000 blocks
The physical size of the device is 122095984 blocks
Either the superblock or the partition table is likely to be corrupt!


/dev/md0: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
fsck died with exit status 4

Tue Apr  7 22:04:48 2009
----------------
```

mdadm/mdstat says everything is fine.


The two drives are both Seagate 500GB drives, the original being a 7200.10 and the clone a 7200.11.  This may be the source of my problem.

If I just ignore the error and proceed with booting everything works fine.

Should I be worried?  Can I fix this?

Thanks,

Cyborg

---

### Post by Cyborg28 on 2009-04-09
Found this possible solution:

>  Re: fsck.ext3: Device or resource busy
Interesting. I changed the PASS value to 0 in /etc/fstab for /dev/md0, and the system booted up normally. (As expected, since fsck skipped scanning the array).

However, I changed the PASS value back to 2, and then the UUID=xxx to /dev/md0. I got a new error on boot:

Code:

/dev/md0: The filesystem size (according to the superblock) is 48839600 blocks
The physical size of the device is 48839584 blocks
Either the superblock or the partition table is likely to be corrupt!


/dev/md0: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e. without -a or -p options)
fsck died with exit status 4
   ...fail!
 * File system check failed.

I guess the filesystems did not get resized with the partitions somehow? So I ran the commands:

Code:

$ sudo e2fsck -f /dev/md0
e2fsck 1.39 (29-May-2006)
The filesystem size (according to the superblock) is 48839600 blocks
The physical size of the device is 48839584 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/md0: 438/24428544 files (5.9% non-contiguous), 1200621/48839600 blocks
$ sudo resize2fs /dev/md0
resize2fs 1.39 (29-May-2006)
Resizing the filesystem on /dev/md0 to 48839584 (4k) blocks.
The filesystem on /dev/md0 is now 48839584 blocks long.

This resized the filesystem I guess. My system now boots normally!

Is this safe to try?  What happens when you resize a file system?  I cannot afford to loose the data on this array!

---


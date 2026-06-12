---
title: "How to disable the boot time disk checks?"
date: 2011-08-01
forum: Desktop Environments
---

### Post by deepaknet on 2011-08-01
These days I see the disk check that is popping up when my Ubuntu is booting up quite frequently. It says 'press C to cancel' but C (or Shift C or CTRL C or CTRL ALT C) does not have any effect. 

Pressing CTRL+ALT+DELETE reboots but again ends up in the vicious loop of disk check. How to bypass it? 

When I need to critically enter the desktop for an urgent  pressing info waiting for 20 to 25 minutes disk check is kind of driving me crazy.

---

### Post by ajgreeny on 2011-08-01
You must have some major problems with your disks or filesystems if the disk checks happen often.  The default is every 30 boots, and the time to check should normally be no more than a minute or two; 20-25 minutes suggests something is very wrong, so to disable the checks is the last thing that I would do.

I suggest you boot to a live CD/USB and run ```
sudo e2fsck /dev/sdx#
``` where the sdx# is you device name for the ubuntu partition, and see if any error messages are shown.

If so, maybe there is something that can be done to improve this problem, rather than simply ignoring it by stopping the checks.

---

### Post by malspa on 2011-08-01
Seems like 20-25 minutes waiting for fsck to finish is an awful long time. I wonder if something's wrong.

One way to completely bypass it is to edit /etc/fstab so that fsck doesn't run at boot. Note: I am NOT recommending this! There are times when you might want to do this, but if you do, you really want to have some routine where you regularly run fsck on your partitions.

Here's the part of my /etc/fstab in question, in Lucid:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=136f3cdf-c824-4f8a-8bac-d86faaf17f63 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=eb55f063-766c-45fd-8ee3-93f33cc735b5 /home           ext3    defaults        0       2
```

The numbers "1" or "2" in the last column controls when fsck runs. If you change it to "0" fsck will not run. You should look at **man fstab**, this part:

> The  sixth field, (fs_passno), is used by the fsck program to deter&#8208;
       mine the order in which filesystem checks are done at reboot time.  The
       root  filesystem  should  be specified with a fs_passno of 1, and other
       filesystems should have a fs_passno of 2.  Filesystems within  a  drive
       will  be checked sequentially, but filesystems on different drives will
       be checked at the same time to utilize  parallelism  available  in  the
       hardware.   If  the sixth field is not present or zero, a value of zero
       is returned and fsck will assume that the filesystem does not  need  to
       be checked.

But, again, if you disable this in fstab you really need to have a way in place to periodically run fsck.

---

### Post by malspa on 2011-08-01
OP: Please note ajgreeny's reply above, that is totally correct. Like I said, unless you have another way of running fsck on those partitions, you shouldn't disable it from fstab. Don't ignore the problem. But if you need to temporarily get around it, you can do so. Again, see **man fstab**.

---

### Post by skimtneer on 2011-08-01
You should also consider repartitioning so that most of the time only the boot partition needs to be checked -- it would be a very small partition and the check would complete in ten or fifteen seconds.  A 20-25 minute disk check sounds like your entire system is on one partition?

---

### Post by ajgreeny on 2011-08-01
> **skimtneer said:**
> You should also consider repartitioning so that most of the time only the boot partition needs to be checked -- it would be a very small partition and the check would complete in ten or fifteen seconds.  A 20-25 minute disk check sounds like your entire system is on one partition?
I agree, but still believe that 20-25 minutes is far too long, so something is not right with the whole setup, in my opinion.

---

### Post by skimtneer on 2011-08-01
Definitely.  Even a disk check for good reason should not take that long.  Also, no one should just accept frequent (or constant) disk checks at startup; the original poster should figure out what's causing that above all else.

The only way I can see 20-25 minutes is if he has his whole system on a single partition on a really huge drive.  Could that scenario take that long, like on a 2TB drive?  Even then the normal boot-time fsck wouldn't be checking all the free space, though, would it?

---

### Post by fsboreal on 2011-11-17
I have a fsck that has been running all night on a 1.5 T RAID array.

---

### Post by luvr on 2011-11-17
I used the *“tune2fs”* command to turn off mount count based, as well as time interval based checking on each of my file systems, as follows:
```
sudo tune2fs -c 0 -i 0 /dev/sdDN
```
(where, obviously, *“D”* represents the disk, and *“N”* represents the partition number of the file system).

I do manually run a file system check from time to time, for which I boot from either a CD, or another system partition installed on my computer.

---

### Post by luvr on 2011-11-18
After I posted the above reply, the Ubuntu system on one of my computers suddenly decided to want to run a file system check on one of its partitions whenever I booted it—though I have no idea whatsoever why it would do that. Quite a mystery...

The first time it did it, I let it run to completion, and it took some 20 minutes to complete. The next few times that I booted it, however, it wanted to run yet another file system check, but I interrupted it. (I'm not sure exactly *which* file system it wanted to check—it automounts three partitions at startup—and I'm not even sure that it wanted to check the *same* file system upon each boot.)

Afterwards, I booted the computer from an Ubuntu Live CD, and manually forced a file system check on each of its Ubuntu partitions—like so:
```
sudo fsck -f /dev/sdDN
```
None of these checks reported any anomalies, or appeared to make any changes to the file systems.

I then verified the *“mount count”* on each of these partitions; to that end, I ran the ***“dumpe2fs”*** command, as follows:
```
sudo dumpe2fs -h /dev/sdDN
```
**Note:**

[INDENT]I actually piped the output from the *“dumpe2fs”* command through to the *“grep”* utility, since I wasn't interested in any of its output, except for the *mount count*:
```
sudo dumpe2fs -h /dev/sdDN | grep '^Mount count:'
```[/INDENT]
The *mount count* for the partitions (i.e., the number of times that they were mounted since the last file system check) was 0—as expected:
```
Mount count:              0
```
Since then, the file system check at boot time has stopped.
Strange, indeed...

---


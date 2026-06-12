---
title: "Cloning/Mirroring An Existing Harddrive"
date: 2009-04-09
forum: General Help
---

### Post by goochpsk on 2009-04-09
I'm extremely new to Linux. I'm currently running Ubuntu 8.10 Intrepid. I would like to clone/mirror my existing harddrive. Does anyone know the exact steps I would take. I've done some research but am having a hard time understanding some of the processes. Any help would be appreciated. Thanks.

---

### Post by bhishan on 2009-04-09
> **goochpsk said:**
> I'm extremely new to Linux. I'm currently running Ubuntu 8.10 Intrepid. I would like to clone/mirror my existing harddrive. Does anyone know the exact steps I would take. I've done some research but am having a hard time understanding some of the processes. Any help would be appreciated. Thanks.

Use Clonezilla. The help will guide u through.

---

### Post by madverb on 2009-04-09
RAID Mirror or just make a clone when necessary?

---

### Post by goochpsk on 2009-04-09
It would be a raid mirror.

---

### Post by neurostu on 2009-04-09
you can use dd or Disk dump
```

dd if=/dev/old_drive of=/dev/new_drive

```
Replace old_drive with sda or sdb or whatever the old drive is, and then do the same for new_drive.

Note you probably don't want to use sda1 or sdb3 etc... the number reflects a partition on the drive and you don't want to clone the partition but the entire drive (including the partition table) so omit the number.

If you have any questions post back or look at:
```

man dd

```

---

### Post by Cyborg28 on 2009-04-09
> **goochpsk said:**
> It would be a raid mirror.

Do you want to use a hardware or integrated raid controller or use Linux Built in software Raid?

I did what you want to do using Linux Raid with the mdadm tool.  It has all of the managment functions for a simple raid built in.

*EDIT*

To see if linux raid is allready supported on your system type:

cat /proc/mdstat

it should give you an output like this if it is installed:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]

If it is not found, installing mdadm and restarting the system should activate the raid system.

ie. apt get mdadm

---

### Post by _Doc_ on 2009-04-09
I believe we are both trying to do the same thing... I have found these 2 articles on creating a raid 1 with an existing drive...

[http://gavinbenda.com.au/2008/09/12/mdadm-raid-using-an-existing-drive/](http://gavinbenda.com.au/2008/09/12/mdadm-raid-using-an-existing-drive/)

and

[http://www.wains.be/index.php/2007/03/12/centos-raid-with-mdadm/](http://www.wains.be/index.php/2007/03/12/centos-raid-with-mdadm/)

They make sense... and use what Cyborg28 talked about... mdadm but my question would be how do I modify the /etc/fstab to properly mount the raid and what else do I have to modify? grub?

---

### Post by _Doc_ on 2009-04-09
i think this link answers my grub and fstab questions...

[http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1](http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1)

one thing I noticed while looking around was that in the 2 links i sited above... they never copy the partition information from the existing drive to the new one... I think that is needed but since I have not done this before I can't say... but hopefully after this weekend I can report back :)

*edit*
that link only handles the grub stuff... I found some info and it looks like you have to change your fstab to 
/dev/md0        /               ext3    defaults,errors=remount-ro 0       1
/dev/md2        /home           ext3    defaults        0       2
/dev/md1        none            swap    sw              0       0

where /dev/md(x) referrers to your mirrored partitions
If you are doing mirroring of partitions... which is how I think I will do mine.

---

### Post by Cyborg28 on 2009-04-09
> **_Doc_ said:**
> I believe we are both trying to do the same thing... I have found these 2 articles on creating a raid 1 with an existing drive...

[http://gavinbenda.com.au/2008/09/12/mdadm-raid-using-an-existing-drive/](http://gavinbenda.com.au/2008/09/12/mdadm-raid-using-an-existing-drive/)



Wow, Thanks, I was trying to find that article.  That is what I used to do my setup.  I am not mirroring my boot drive or partition so I did not mess with grub.  If you need raid on your boot drive your best bet is to start fresh with the "alternate install" (not sure exactly what it is called) Ubuntu CD.  It has tools for raid right at the partitioning stage.

> one thing I noticed while looking around was that in the 2 links i sited above... they never copy the partition information from the existing drive to the new one...

You don't need to, this command "rebuilds" the array and clones all the information.

```
mdadm --add /dev/md0 /dev/sda2
```

I have had a small problem with this method.  The system works fine but has an fsck problem.  I have started another thread about it and would not mind some input.
[URL="http://ubuntuforums.org/showthread.php?t=1120840"]
http://ubuntuforums.org/showthread.php?t=1120840[/URL]

Here is info re fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdd1 /dev/sde1
/dev/md0       /home/username/Storage   ext3 defaults 0 2
 
```

I have just told fstab where to mount the md0 raid array. The comment above it tells me what disks the array is made of. mdamd manages setting up md0 on startup.

---

### Post by Cyborg28 on 2009-04-09
> I have had a small problem with this method. The system works fine but has an fsck problem. I have started another thread about it and would not mind some input.

Apparently running:
```
sudo e2fsck -f /dev/md0
```
Fixes the problem by changeing the filesystem size but I am hesitant to try.  Is this a risky operation?  I don't want to loose the data on the array.

---


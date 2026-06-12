---
title: "Disk Partition Extending Problem"
date: 2009-06-08
forum: General Help
---

### Post by General-Gouda on 2009-06-08
So up until this weekend I was dual booting Ubuntu 9.04 and Win XP on a 30 GB hard drive.  I wanted to make sure that Ubuntu would work sufficiently enough before getting rid of Windows XP.  

Well, I finally got my copy of Ubuntu to a place where I was ready to get rid of WinXP this weekend so I booted up the Live CD, fired up Partition Editor and deleted my WinXP partition.  I then began merging that unallocated space into my Ubuntu installation to create more room.  The process was taking a VERY long time and it seems it was copying things over out of the unallocated space.  After a very long time it eventually gave me an error message and the partition extension stopped.  

Now, before I started the 30 GB was split between a 1 GB swap area, a 13.6 GB WinXP partition and a 13.6 GB Ubuntu partition.  Now, after the process, I have a 1 GB swap area, and 26 GB partition for Ubuntu.  The program is that it says that 19 GB of that is filled up.  But when I load up Ubuntu (not the live CD) it says that I still only have 13 GB available with only 5 GB of space left over.  

What happened to the extra space?  It's not in the file system and I have no idea how to retrieve it without reinstalling Ubuntu.  I'd rather not do that again as it would be the 4th or 5th time I've reinstalled it onto my laptop and I finally have it set up how I like it!

Any help would be appreciated!

Thanks!

---

### Post by merlinus on 2009-06-08
Try this for the info you are wanting:

```

df -h

```If that doesn't do it, post a screenshot of gparted.  You might also look in System/Administration/System Monitor.

---

### Post by General-Gouda on 2009-06-09
Here are the results for the df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              14G  5.6G  7.2G  44% /
tmpfs                 249M     0  249M   0% /lib/init/rw
varrun                249M  212K  249M   1% /var/run
varlock               249M     0  249M   0% /var/lock
udev                  249M  144K  249M   1% /dev
tmpfs                 249M   76K  249M   1% /dev/shm
lrm                   249M  2.4M  247M   1% /lib/modules/2.6.28-12-generic/volatile


I have a 30G drive...where is the rest of it?  :(

Here is a picture of Gparted.

[IMG]http://img196.imageshack.us/img196/2312/screenshotdevsdagparted.png[/IMG]

Any ideas?

---

### Post by merlinus on 2009-06-09
What does System Monitor show?  Some of the space is used by formatting and the ext3 journalling system.

---

### Post by General-Gouda on 2009-06-09
> **merlinus said:**
> What does System Monitor show?  Some of the space is used by formatting and the ext3 journalling system.

[IMG]http://img38.imageshack.us/img38/9902/sysmonfilesystems.png[/IMG]
:-(  

It's just gone!

---

### Post by michy99 on 2009-06-09
What is the output of```
sudo fdisk -l
```

---

### Post by merlinus on 2009-06-09
When you say that you merged the free space into your ubuntu partition, is that a different process from resizing?  If so, you may have all sorts of leftover windows garbage (tmp and fragmented files, for example) that are hidden from view and occupying space.

---

### Post by General-Gouda on 2009-06-10
> **michy99 said:**
> What is the output of```
sudo fdisk -l
```

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb559b559

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         131     1052226   82  Linux swap / Solaris
/dev/sda3             132        3648    28250302+  83  Linux

[quote=merlinus]When you say that you merged the free space into your ubuntu partition, is that a different process from resizing? If so, you may have all sorts of leftover windows garbage (tmp and fragmented files, for example) that are hidden from view and occupying space.[/quote]

I made sure that before I started the disk extension that the NTFS partition had been deleted and it was being shown in GParted as Unallocated space. I pressed the apply button to make doubly sure that the partition was deleted.  I had to because there was a swap file between the two partitions that I had to remove before I could merge the two larger partitions.

Should I have taken that unallocated space and formatted it to ext3 before merging SDA3 with the unallocated space?

---

### Post by mixmaster on 2009-06-10
OK, there is no way you can have used 19Gb of your partition given that it was only 13Gb in size before it was extended.

I am inclined to believe the output of df which showed 
dev/sda3 14G 5.6G 7.2G 44% /

I suspect what happened was that the extension process failed and left the partitions in something of a mess, specifically it extended the partition table but failed to extend the filesystem to use the new space.

Given that your filesystem is in a somewhat odd state I would be inclined to immediately back up anything vital.  Then you could try using fsck to repair the filesystem and if this fails I would reinstall.

TBH, after a partitioner failure I would be tempted not to attempt the repair but to go straight to the reinstall stage.  Beg, borrow, steal or even buy an 8Gb USB stick, boot the live CD, copy all your stuff onto the stick, reinstall, reboot the live CD and copy the stuff back from the stick.  It won't take much longer than a repair (if repair is possible) but you will know afterwards that you are safe.

---

### Post by General-Gouda on 2009-06-10
I was afraid of this.  I was happy that I finally got Ubuntu to a state where I wanted it with apps and things installed.  I guess I'll have to start from scratch.  Oh well, I've become an expert at it!

Thanks for the input everyone.

---

### Post by Entropy_Sam on 2009-06-10
What does /etc/fstab look like? I had a strange problem once when I'd messed up trying to copy my Ubuntu install to another HD. I had two identical partitions with the same UUID, and a third one on the new HD (don't ask - it was a newb mistake in GParted).
 
At one point, I was trying (and failing) to boot the installation on the new HD, and it seemed my entire filesystem was being mounted twice - I had twice the amount of expected free space for the older HD, and my filesystem was twice the expected size.
 
Is it possible something strange like this is happening?
 
I can't see your GParted image from my work account, but have you carefully checked the UUIDs of your partitions against each other and your fstab to make sure tehy are being mounted correctly?

---

### Post by General-Gouda on 2009-06-10
I reinstalled the OS.  All seems to be working better now.

Thanks!

---

### Post by merlinus on 2009-06-10
Excellent!  Often it is better to cut one's losses and start over, rather than go through teeth gnashing and hair pulling which can still lead nowhere.

---

### Post by General-Gouda on 2009-06-10
> **merlinus said:**
> Excellent!  Often it is better to cut one's losses and start over, rather than go through teeth gnashing and hair pulling which can still lead nowhere.

I set myself back up much faster than I originally thought I would.  I'm back to practically where I was before after borrowing a 4GB flash stick and copying my Home folder over to it.  Everything else was just a quick redownload.  Nothing I couldn't do while multi-tasking at work!

Thanks again!

---


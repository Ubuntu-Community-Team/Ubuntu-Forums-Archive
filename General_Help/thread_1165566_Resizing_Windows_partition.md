---
title: "Resizing Windows partition"
date: 2009-05-20
forum: General Help
---

### Post by dvfreelancer on 2009-05-20
Installed 9.04 on a laptop, which was a breeze. The funny part was Ubuntu managed to update the wireless card driver and get the wireless working, which would not work under XP.   But it only left me 125 megs of free space.  Not good.  

I put the live CD back in and used the partition editor to shave 11 Gigs off the Windows partition and format it with ext3.  It came out labeled sda4, I think.  

I can see it as media in the file browser, I can mount it, but I can't figure out how to move it over to where Ubuntu can see it as usable space.  What do I have to do to make that auto-mount and let Ubuntu claim that media space?

---

### Post by logos34 on 2009-05-20
[Here]("http://www.psychocats.net/ubuntu/mountlinuxhttp://www.psychocats.net/ubuntu/mountlinux") you go

---

### Post by dvfreelancer on 2009-05-20
> **logos34 said:**
> [Here]("http://www.psychocats.net/ubuntu/mountlinuxhttp://www.psychocats.net/ubuntu/mountlinux") you go

Page not found.

---

### Post by geirha on 2009-05-20
In Ubuntu, partitions get mounted on directories (as opposed to C:, D:, E: etc in windows), so for instance you can move the home directories over to the new partition, and then have it mounted as /home (very common setup). How much space is your current ubuntu partition?
```
sudo fdisk -l
df -h
```

---

### Post by lisati on 2009-05-20
> **dvfreelancer said:**
> Page not found.

Try [here]("http://www.psychocats.net/ubuntu/mountlinux")

---

### Post by dvfreelancer on 2009-05-20
> How much space is your current ubuntu partition?

I believe it's 2.4 gigs.

---

### Post by logos34 on 2009-05-20
> **dvfreelancer said:**
> Page not found.


soory, I must have double-pasted.

Here:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by geirha on 2009-05-20
> **dvfreelancer said:**
> I believe it's 2.4 gigs.

That's a little short, you won't be able to install much before it fills up. I think it would be better to resize your current partition instead.

---

### Post by dvfreelancer on 2009-05-20
Okay, I followed the process outlined here:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Everything seemed to go okay but I check the file system properties and it still says 124 megs of free space.  Do I have to reboot for the changes in fstab to be picked up?  

I made one mistake...typed hda4 instead of sda4, but I fixed that before assigning permissions or any of that.  

Here's the fdisk -l listing after I completed the steps:

> Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: *******

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        3088    24756165    7  HPFS/NTFS
/dev/sda3            4539        4864     2618595    5  Extended
/dev/sda4            3089        4538    11647125   83  Linux
/dev/sda5            4539        4842     2441848+  83  Linux
/dev/sda6            4843        4864      176683+  82  Linux swap / Solaris


This is a Latitude D610 and I really like it.  But it's got some odd solid state storage in it that's part of the file system.  That's where the free 11 gigs came from.  

If I get frustrated enough I'll blow away the partitions and install on the whole disk, but I'm trying to keep the dual boot capability.  It's nice for those very rare occasions when Windows would be convenient.  ;)

---

### Post by dvfreelancer on 2009-05-20
> **geirha said:**
> That's a little short, you won't be able to install much before it fills up. I think it would be better to resize your current partition instead.

I tried that.  The partition editor wouldn't let me.  I could shrink it but not resize it.  The only thing I could do was shrink the windows partition and reformat it as ext3, but I could move anything.

---

### Post by logos34 on 2009-05-20
> **dvfreelancer said:**
> I tried that.  The partition editor wouldn't let me.  I could shrink it but not resize it.  The only thing I could do was shrink the windows partition and reformat it as ext3, but I could move anything.

Is swap mounted?  It tries to automount it when you boot the live cd, locking up everything inside the extended partition, sda3 (which contains sda5,6)

In gparted go

>right-click on swap/sda6>swapoff

Delete sda4

now try to drag the left border of sda3, the extended partition, to the left to incorporate all the unallocated space.  Then grow / (sda5) to the left all the way.

---

### Post by dvfreelancer on 2009-05-20
Okay, I'll give that a shot.  Do I have to wipe that line in the fstab afterward?

---

### Post by logos34 on 2009-05-20
> **dvfreelancer said:**
> Okay, I'll give that a shot.  Do I have to wipe that line in the fstab afterward?

yes (glad you mentioned that), because otherwise it will throw an error on boot trying to mount 'sda4' which will no longer exist!

no need to edit menu.lst or fstab for the / line, because merely growing it does not change the partition # or UUID.

---

### Post by dvfreelancer on 2009-05-20
> **logos34 said:**
> Is swap mounted?  It tries to automount it when you boot the live cd, locking up everything inside the extended partition, sda3 (which contains sda5,6)

In gparted go

>right-click on swap/sda6>swapoff

Delete sda4

now try to drag the left border of sda3, the extended partition, to the left to incorporate all the unallocated space.  Then grow / (sda5) to the left all the way.

Okay, everything was great until I got to growing sda5 to the left.  It chewed on that a few minutes, then popped an error that something bad happened.  When I rebooted and checked, the file system says 111 megs of free space and the 11 gig partition is gone.  

Here's the new fdisk -l :

> Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        3088    24756165    7  HPFS/NTFS
/dev/sda3            3089        4864    14265720    5  Extended
/dev/sda5            3089        4842    14088973+  83  Linux
/dev/sda6            4843        4864      176683+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS


There's 320 gigs of space on sdb. I should try to reclaim some of that.  Gah, if I'd just paid attention to the partition size on the install.

---

### Post by logos34 on 2009-05-20
well it looks ok...

> /dev/sda2 * 7 3088 24756165 7 HPFS/NTFS
[COLOR="Blue"]/dev/sda3 3089 4864 14265720 5 Extended
/dev/sda5 3089 4842 14088973+ 83 Linux[/COLOR]
/dev/sda6 4843 4864 176683+ 82 Linux swap / Solaris

You're booted back into ubuntu, or still on the live cd?

---

### Post by dvfreelancer on 2009-05-20
> **logos34 said:**
> well it looks ok...


You're booted back into ubuntu, or still on the live cd?

Booted back to Ubuntu.  I'm going back to the fstab and remove the reference to sda4.  

But how do I reclaim that space for Ubuntu?  It's still not picking it up.

---

### Post by logos34 on 2009-05-20
so even after reboot df still doesn't reflect the change?  Because the partition table according to fdisk appears correct...

hmm...

---

### Post by dvfreelancer on 2009-05-20
File system still reporting 111 megs.  I may reinstall tomorrow. Didn't want to do that because I had the wireless working, which was kind of trick but it's a lot easier than trying to move partitions.

---


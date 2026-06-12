---
title: "Trying to change drive permissions and it keeps snapping back to old values"
date: 2009-05-23
forum: General Help
---

### Post by mjpatey on 2009-05-23
Hi, all-

I've run into this before, and have no idea how to solve it.  In Nautilus, I'm trying to change the permissions of a secondary internal drive.  My user owns it and has read/write permissions, but nobody else can address it in any way, not even root.  In order for me to access it, when I first installed it, I had to enter my user password, and checked the box to remember my authorization permanently.

Well now, I want everybody to be able to access it and read/write to it.  So in Nautilus, I try to open up permissions of all kinds for everybody, and as soon as I change a value, it snaps back to its original restrictive state.

Thinking maybe I don't have the authority to make these changes, I open a new Nautilus window as root (sudo nautilus).  The same result.

Any idea how to change the permissions of this drive?

Thanks for any insight!

-Mark

---

### Post by coffeecat on 2009-05-23
What is the filesystem on this "secondary internal drive": ext3, ntfs or fat32? If it's fat32 or ntfs, you can't change permissions because they are Windows filesystems which don't support Linux permissions. If the drive is mounted at bootup with entries in /etc/fstab, the permissions are set there. If you as first user can read/write to this drive, but other users can't, then fstab needs editing.

If the drive is formatted ext3, none of this applies.

**Edit:** although I don't understand why root can't access the drive. Perhaps you'd better post details of the drive. Post the contents of /etc/fstab and the terminal output of:

```
sudo fdisk -l
```

---

### Post by mjpatey on 2009-05-23
Well, that would explain it... it's formatted FAT32.  Would any of the info you requested still help?

---

### Post by coffeecat on 2009-05-23
The contents of /etc/fstab would still help. It's a long time since I've used a fat32 (vfat) partition on an internal drive, but I seem to remember that the Ubuntu installer set one of the options as "GID=46" and, again afaicr, GID=46 is the plugdev group. Perhaps your 'other' accounts don't belong to the plugdev group.

It's late here and I'm signing off soon, so I won't be able to check this thread until tomorrow, so I'll leave you with a couple of links about fstab. There might be something useful in them.

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

In fact, in the second one, there's something pertinent:

> 
[LIST]
[*]ntfs/vfat = permissions are set at the time of mounting the partition with umask, dmask, and fmask and can not be changed with commands such as chown or chmod.
[*]I advise dmask=027,fmask=137 (if you user umask=000 all your files will be executable). More permissive options would be dmask=000,fmask=111.
[/LIST]
Good luck.

---

### Post by mjpatey on 2009-05-23
coffeecat, thanks for all the info!  Before reading this post, I began composing a little history of my trouble with this drive, in case any of it is meaningful:

When this drive was being used externally (mounted in a USB enclosure), permissions weren't an issue, but toward the end of its stay in the enclosure, it started "hanging" at odd times.  This was also shortly after my wife connected it to her Windows laptop.  Its irregular performance led me to fsck it in Ubuntu, but I found no problems.  Then we re-connected it to my wife's laptop, which checked it for consistency on boot this time, found bad sectors and "repaired" them.  I, however, continued to have the same trouble with it in the enclosure on my Ubuntu system.  To eliminate the enclosure and its interface as a possible cause, I installed the drive internally via an IDE connection.  In this configuration, I can access and write to it myself, and it's mountable/unmountable in Nautilus, but one program doesn't seem to be able to see it at all:  Picasa, which is a program that runs on its own custom Wine install (separate from any Wine the user may haveinstalled).

If I get access to Picasa's own copy of winefile (which I think I can, it's just buried in tons of folders), maybe it has a utility to tweak drive permissions, if it can even see the drive.  I can't try any of this now, as I'm at work.

Thanks for all your info, and I'll post back tomorrow with any new info, and my /etc/fstab.  :-)

-Mark

EDIT:  That post from the forums looks perfect!  If only I were home now.  Suppose I could SSH into my home machine from here, but the IT folks probably wouldn't like that.

---

### Post by mjpatey on 2009-05-23
Also found this link, for anyone else looking to change permissions of a VFAT drive:

[http://www.sdconsult.no/linux/wine-doc/vfat.html](http://www.sdconsult.no/linux/wine-doc/vfat.html)

---

### Post by mjpatey on 2009-05-25
Here's my /etc/fstab:

```
 # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=7c481210-616a-4f0f-b93a-d851f9b8b334 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e7bfa954-c7e9-45d0-866e-9ac63a75a981 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```I composed a post a couple of days ago containing this info, but must not have posted it before my machine locked up.  As you can see, it sees my main system drive (sda7), swap (sda5), the CD-ROM, and a non-existent floppy.

EDIT:  What it doesn't show: two other partitions of my main system drive (which appear mounted in Nautilus and available to other apps), and the beleaguered VFAT drive in question (which also displays in Nautilus).  Sometimes, if I go to /media in Nautilus, it shows all three of these (Disk-2, Disk-1 and Disk, respectively), but sometimes it doesn't!

Could this be why Picasa can't see the drive, and if so, how do I fix that?

---

### Post by coffeecat on 2009-05-26
> **mjpatey said:**
> EDIT: What it doesn't show: two other partitions of my main system drive (which appear mounted in Nautilus and available to other apps), and the beleaguered VFAT drive in question (which also displays in Nautilus). Sometimes, if I go to /media in Nautilus, it shows all three of these (Disk-2, Disk-1 and Disk, respectively), but sometimes it doesn't!

Could this be why Picasa can't see the drive, and if so, how do I fix that?

If your vfat drive (or other partitions) is/are not in fstab then it won't get mounted on bootup and you won't have mount folders (disk*) in /media - yet. But any partitions not in fstab will show in the Places menu, or in 'Computer', and if you double-click on the icon for one of them, it will get mounted and the appropriate /media/disk* mountpoint will be created and a desktop icon will appear.

At least, that's what *should* happen, and what happens on my system. But if you're getting something different - well, I don't know. Also, if you can see three disk* folders in /mount, then you must have mounted them by double-clicking on the Places icons.

So - if you want all three mounted at bootup, you'll need three lines in fstab. If you make the mountpoints in /media, icons will appear on the desktop (unless you've disabled this in gconf-editor. If you use mountpoints in /mnt, you get no desktop icons and have to navigate to the mountpoint folder by Places > Computer > filesystem > /mnt. Some people prefer this. By the way, what filesystems are these other two partitions? If you want some help with fstab, post the output of:

```
sudo fdsik -l
```A hint that I find useful: if partitions are being mounted in folders called /media/disk* then they don't have partition labels. If, however, you give the partitions labels, the mountpoints will have the same name and desktop icons (if you mount in /media) will show those names. Let's say you have partitions with labels Music, Photos and Docs, then that is what will appear on the desktop (and/or in Places). You can add partition labels for all supported filesystem types by using Gparted - either install it or use the live CD.

By the way, the /media mountpoints are created on the fly if you have to mount them by double-clicking in Places, and are then deleted when the partition is unmounted - just as with USB devices. But if you add fstab entries, you need to create permanent folders in /media or /mnt first. And another useful tip!  :) When adding entries in fstab you don't need to reboot to see their effect. Simply:

```
sudo mount -a
```And they get mounted. If you've made a mistake, simply 'sudo umount /media/whatever', edit fstab and 'sudo mount -a' again.

I don't know about Picasa. That runs in wine, doesn't it? You can navigate your way around the Linux filesystem in a wine app, so Picasa should be able to see those drives so long as they are mounted, but Picasa is a bit peculiar.

---

### Post by rsdunker on 2009-05-27
I'm by no means an expert on linux so please feel free to correct any errors, but I've been fighting this as well and will share the bits of info I've dug up.

----------------------------------------------

When you make any changes to /etc/fstab first unmount the drive

**sudo umount *your drive mount point here***
mine would be   **sudo umount /data**

then re-read fstab and remount all drives by entering

**sudo mount -a**

This will save you from rebooting to see if your changes work.

-----------------------------------------------

As far as the problem you are having, it seems linux cannot store the permissions of vfat and ntfs file systems so all permissions are changed at the time of mounting.  This includes ownership.  No idea why adding rw,exec to the options doesn't give you full permissions or what they do do.  The 2 solutions I have found are to change the permissions when you mount the drive or take ownership when you mount the drive.

-------------------------------------------------------

Changing permissions in fstab seems to be backwards to normal.  You use the umask command to list permissions you do not want the drive to have.  For example to give full access to all I believe you would add this to the options section of fstab

**umask=000**
umask=077 would be the same as entering sudo chmod 700



The other option would be to take ownership by adding the following to fstab options

**uid=*your user name or id here***
or 
**gid=*group name or id here*** (not sure how to use this one)

----------------------------------------------------

I guess some consideration should be made to security when doing either of these, but that's above my head.  I will close this way to long of a post with a couple examples of my fstab to mount /dev/mdo to /data.

**/dev/mdo   /data   auto   user,auto,umask=000     0     0**
would mount to /data at boot, auto detect file system, allow users to mount/umount, will mount with **mount -a** command, set permissions to chmod 777.

[B]
/dev/mdo   /data   auto   user,auto,uid=johndoe     0    0[/B]
would mount to /data at boot, auto detect file system, allow users to mount/umount, will mount with **mount -a** command, and set owner to johndoe.

Hope this helps and like i said, I'm very new to this myself so double check my facts.

---


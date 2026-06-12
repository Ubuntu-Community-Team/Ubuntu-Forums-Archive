---
title: "[SOLVED] External hard drive mounts... but only sometimes"
date: 2008-01-11
forum: Desktop Environments
---

### Post by grahambo2005 on 2008-01-11
Hey all

I'm having an Issue with my external hard drive.

Its doesn't seem to mount all the time. Its connected to my PC pretty much all of the time and I use it to store media files etc. When I boot up my PC, 50% of the time it mounts with no problem. when i click places on the menu bar I can see it and I can go into it and play my media files etc.

but sometimes (like now) It does not mount and I cannot see it in "Places" and cannot access any of the files on it. I don't really know how to mount it manually, I'm going to have a read about it after this post.

does this happen to anyone else? the hard drive is connected so it not a stupid problem like that. Ive also tried plugging out the usb cable and plugging it back to try and get it to auto detect the hardware but it does not. "It _is_ set to auto detect hardware"

any info anyone has would be a great help... cheers

Graham

---

### Post by dabang on 2008-01-11
Please post your /etc/fstab. If the drive is mounted, where?

"Places" does technically not show "mounted" partitions, but drives/partitions that are available. If your drive doesn't show up there, my first guess would be that it didn't get initialized by the BIOS or something like that.
If you have one internal drive, the external drive could be something like /dev/sdb. If so, you could mount the first partition on that external drive with
```
sudo mount /dev/sdb1 /mnt
```
so "mount" works like this:
mount <device> <path_to_mount_point>

---

### Post by grahambo2005 on 2008-01-12
the fstab file as requested

  ```
GNU nano 2.0.6                                  File: /etc/fstab                                                                            

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=35d8afe5-d16d-43e7-9207-89399762cc6e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=32a612bf-31f2-488b-8a61-c20e098c5de1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Ive checked the media folder and the my computer folder also and it is not there.
I have 2 internal drives so Im not sure whether it woud be a good idea to execute that command

Graham

---

### Post by dabang on 2008-01-12
OK, Ubuntu is installed on your second harddrive (sdb) with /dev/sdb1 mounted as "/". How many internal drives do you have? But besides that, I think I'm right: if you don't see your external drive it hasn't been initialized correctly. Could be wrong, but I don't think it's a linux/Ubuntu related problem. I guess you already tried things like power cycling the external harddrive? Sorry, no other ideas right now... :(

---

### Post by grahambo2005 on 2008-01-12
Yeah I tried that

didnt work

this is very weird if it didnt work all the time I would understand that but the fact that it does and doesnt really is wrecking my head!

Im going to keep at it, there has to be something I can do to fix this!

Graham

---

### Post by grahambo2005 on 2008-01-12
Hi Dabang

I think I have figured out what the problem is. I went on your theory that it was not an Ubuntu problem so i turned off my PC removed the power cable also and did the same for my external drive.

I noticed something different on boot up (usually my bios displays what is connected VIA USB on boot up, it then looks to get info about the 500GB external drive I have connected.. this takes a while (about 30-40 seconds). The bios seems to know that it is a WD hard drive connected. this time however after completely removing the power it did not do this (just told me what types of device were connected, not the actual name and brand)

Booted up Ubuntu and low and behold my external hard drive is available. so its defo A bios problem. [I]m going to have to have a read on how to fix it. Its still strange though as it does not do this in windows Vista, the hard drive is always available regardless of what happens during boot up.

Im going to mark this thread as solved

I am also going to post the contents of the fstab file to see if you can see anything different or why this is happening.

Cheers

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=35d8afe5-d16d-43e7-9207-89399762cc6e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=32a612bf-31f2-488b-8a61-c20e098c5de1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

 
```

---

### Post by dabang on 2008-01-12
Thanks for your thanks! :)

So /dev/sda is your Windows Vista drive? OK, that has nothing to do with the USB drive problem, just wondering. If the USB drive is visible, you maybe see which device it is. I would think /dev/sdc then. You may then try to "really" mount partitions with the mount command.
Why this problem occurs with linux only, I don't know. I guess Windows initializes the USB harddrive itself and independently of the BIOS when booting. Or it's a bug in Ubuntu kernel.

/etc/fstab seems not different than before. This file is not written dynamically at boot. If not edited manually (or by a package) it'll stay the same.

---

### Post by robojock on 2008-04-03
i have the same problem with my WD 500gig external, I have to restart my pc a few times before it shows  up in ubuntu. How can i fix this?

---

### Post by ChazBudda on 2008-04-03
I had exactly the same problem....I have 2 internal hard drives:
 - disk 1, partition 1 = linux swap
 - disk 1, partition 2 = ubuntu root
 - disk 1, partition 3 = windows
 - disk 2 = files & documents
 - disk 3 = external eSATA drive used for media files

The trouble (in my case) was that when Ubuntu first installed & started it mounted the drives as follows:

/dev/sda1 (linux swap)
/dev/sda2 (ubuntu root)
/dev/sda3 (windows)
/dev/sdb1 (files)
/dev/sdc1 (external)

But after a couple of re-boots, the lettering changed and the file system was physically assigned different letters, e.g.:

/dev/sda1 (external)
/dev/sdb1 (linux swap)
/dev/sdb2 (ubuntu root)
/dev/sdb3 (windows)
/dev/sdc1 (files)

Note that the external drive is now regarded as the 'a' disk whereas before it was the 'c' disk.  Of course the effect of this was that the external drive (and windows + files) were no longer mounted (because the fstab entries were not in line with arbitrary sdx assignments).

The only reason I got away with Ubunti starting was because the initial fstab referenced the Ubuntu & swap partitions by their UUID (kind of like a fixed fingerprint value).

To resolve:
 - I gave each internal drive a unique label
 - and updated the fstab to reference drives with the LABEL= option
 - this fixed my mounting issues for the files and windows drives

 - The fstab didn't recognise the external drive's label (I presume because it's FAT)
 - so I commented out the reference to it in the fstab and rebooted a couple of times (checking each time with the fdisck command which letter it was assigned)
 - after a cople of reboots (with the internal drives referenced by their LABELs) the external drive seemed to settle on /dev/sda1
 - so I added it back into the fstab as /dev/sda1 and it's was recognised and mounted on the next reboot.

It's a workaround, granted, because the assignment of 'a' may change again for the external drive.  But it's been okay for a week or so now :) and worst case it's only the external drive that I need to manually re-mount (i.e. none of the internal partitions will ever unmount due to this letter re-shuffling because they're referenced by their LABELs).

---

### Post by robojock on 2008-04-03
will give it a try and let you know.

---

### Post by vanadium on 2008-04-03
I didn't find information on the file system of the external drive in this thread, but you should know that ntfs drives are not automatically mounted in Linux when they are not "clean". If you use Windows along with ubuntu, make sure that you always properly disconnect the drive in Windows, or, with the drive connected, shut down Windows completely (no hibernate!) before starting up Ubuntu. Even when only using Ubuntu, make sure you always properly unmount the drive by right-clicking and choosing "Unmount".

---

### Post by robojock on 2008-04-04
> **vanadium said:**
> I didn't find information on the file system of the external drive in this thread, but you should know that ntfs drives are not automatically mounted in Linux when they are not "clean". If you use Windows along with ubuntu, make sure that you always properly disconnect the drive in Windows, or, with the drive connected, shut down Windows completely (no hibernate!) before starting up Ubuntu. Even when only using Ubuntu, make sure you always properly unmount the drive by right-clicking and choosing "Unmount".
so would it be best to format the drive to ext3?

---

### Post by vanadium on 2008-04-04
> so would it be best to format the drive to ext3?

If you are only using Linux and you could temporarily safeguard the data somewhere else, then surely yes: it is best to use a native file system that is fully supported by the operating system.

However, this does not detract from my recommendation that whatever file system you use, you should take care of properly connecting and disconnecting the drive. Even then, any file system needs periodical checking for consistency.

---

### Post by robojock on 2008-04-04
just a dumb question is my external supposed to show up in fstab?

---

### Post by grahambo2005 on 2008-04-04
I have a simple solution for this issue

this problem is related to the mother board

when you boot up the machine (cold boot) and the External drive is plugged in to the machine and is connect to its power cable it takes a long time for the bios to boot up.

this is because its looking for the name of the drive (this takes about 30-40 seconds to do)

once booted up your external drive does not appear

if you restart your machine via the OS the bios boots up quicker as it already knows what its connected to. When the OS loads the external drive appears

So.

If when the machine is booted (cold) and the external drive is not connected to its power source its boots quickly, you can then plug in the power cable to your external drive (once the OS has loaded) and Ubuntu will detect it.

Simple solution = plug in your external drive only after Ubuntu has loaded (Im talking about the power cable and NOT the cable from the drive to the computer, you can leave that plugged in all the time)

Graham

---

### Post by robojock on 2008-04-07
i am gonna give it a try and see if it works

---


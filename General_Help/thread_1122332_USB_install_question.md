---
title: "USB install question"
date: 2009-04-10
forum: General Help
---

### Post by M4rotku on 2009-04-10
Hey Guys,

I recently bought an 8 gig flash drive.  Now, I am a 8.04 user, so I'm not familiar with the install-to-usb option of 8.10.  I assumed that I would be able to split the flash drive into two partitions of 4 gigs each and install Ubuntu on one of the partitions.  I was looking for something similar to how puppy linux is able to run from a flash drive.

I booted my newly burned 8.10 live cd and installed to the flash drive with no apparent problems.  I don't know if it's relevant or not, but I selected the option to reserve 1 gig of room for documents.  Then I unmounted the drive and repartitioned it using gparted.  I split it in half with all of the orange filling (representing the data) on the left half.  I reformated the other half into fat32.

When I rebooted, the live usb did not boot.  I went into gparted and checked it's flags and it is marked as able to boot.  Did I do something wrong or is the usb version just not supposed to work like that?  If it is not meant to work in such a manner, what would the recommended distro be that I can run from a usb drive?  I want something heavier than puppy.  It would really be nice to be able to have Ubuntu.  any advice is appreciated.

Much thanks,
M4rotku

---

### Post by M4rotku on 2009-04-12
Bumpity bump.  Much thanks to the 14 ppl who have looked at my question so far.

):P

---

### Post by M4rotku on 2009-04-13
Ok, update time.

I reformatted the drive into one partition again and installed the operating system again.  I booted the flash drive and everything appears to work fine.

I left 2.5 gigs of extra room and I was thinking of partitioning off the last 2 gigs, but I don't want to risk it not working again.

When I was reformatting, I saw that a few MB's of files had accidentally been transfered to the 2nd partition when I split it in half.  This is probably why it wouldn't boot.

Is there any way I can partition it in a manner that guarantees that no data will be split?

---

### Post by M4rotku on 2009-04-23
Update:

I managed to split the drive into two partitions without any problems.

However, I encountered an odd issue when I tried to use the extra partition as a regular flash drive with a windows machine.

When I plugged the flash drive into a Windows machine, the partition with the Ubuntu OS on it mounted as a cd, which I'm assuming the the intent.  The problem is that the other partition did not mount at all.  I know that it works b/c I've used it on my Ubuntu machine several times.

As far as windows could see, the drive did not exist.  This is a problem b/c the whole point of having the flash drive set up in this manner is so that I can have my portable Ubuntu and still have a working flash drive.

Does anyone know why this won't mount?  Is windows unable to see fat32?

much thanks,
M4rotku

---

### Post by M4rotku on 2009-04-24
bump

---

### Post by snowpine on 2009-04-25
My advice: wipe the USB drive, create the Windows partition as the first partition on the drive (farthest to the left in gparted), then the partition for your Ubuntu install, then finally use the USB creator to install Ubuntu. Windows for some reason only sees the first partition on the drive. :(

---

### Post by M4rotku on 2009-04-30
Thanks for that advice snowpine.  That explains a lot.  Will do.

---

### Post by dcstar on 2009-04-30
> **snowpine said:**
> 
.........
Windows for some reason only sees the first partition on the drive. :(

By design:

[http://www.msfn.org/board/index.php?act=ST&f=82&t=69211&st=0](http://www.msfn.org/board/index.php?act=ST&f=82&t=69211&st=0)

---


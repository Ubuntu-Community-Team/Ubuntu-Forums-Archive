---
title: "External USB Harddrive Not Recognized"
date: 2009-04-28
forum: General Help
---

### Post by stanjr on 2009-04-28
I have an external USB harddrive, formatted as ext3, that had been working under Ibex with the following line in my /etc/fstab:

UUID=225bd302-5067-452d-a380-6c2e5cdeb322 /media/disk ext3 user,relatime,errors=remount-ro 1 2

I used it for my bittorrent uploads/downloads using rtorrent.

I recently upgraded from Ibex to Jaunty yesterday and throughout the day I noticed that rtorrent kept shutting itself down.  I didn't realize at the time that it was probably the USB disk becoming unrecognized.

I restarted the computer and fsck ran automatically on the USB disk, but it errorred out with "fsck.ext3: Unable to resolve 'UUID=225bd302-5067-452d-a380-6c2e5cdeb322' fsck died with exit status 8."  Then it asked me to hit Ctrl-D to continue rebooting, then manually check the disk.

I couldn't get Jaunty to boot unless I unplugged the USB drive or commented out its fstab line: I could get Jaunty to boot first if I unplugged the USB drive, then any time after that if I then commented out the fstab line and had the USB drive plugged in.

When I get Jaunty to boot with the USB drive plugged in and the fstab line commented out, then un-comment the fstab line and do a "sudo mount -a" at the command line, I get this:

mount: special device /dev/disk/by-uuid/225bd302-5067-452d-a380-6c2e5cdeb322 does not exist

I've tried making the end of the fstab line 0 0, instead of 1 2, but that still doesn't work either.

Does anyone know what is going on or how to fix this issue?  I assume that fsck failed on it and caused some problems somehow and now that it can't be recognized, fsck can't be run on it even manually.

Help please!

---

### Post by kpkeerthi on 2009-04-28
The UUID might have changed. To get the UUID, run this command
```
sudo blkid
```
and use it in your fstab and then try with 'sudo mount -a'

---

### Post by stanjr on 2009-04-28
All I get with that are my two other internal drives:

/dev/sda1: UUID="a263a23a-51cb-4ff9-a515-25e35b69dba7" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="35fcdc42-8b01-487f-8217-8c47e9e0003b" 
/dev/sdb1: UUID="d60b506b-b25c-400c-9506-9020b7ebdd1e" SEC_TYPE="ext2" TYPE="ext3"

sda is my boot drive (with swap space) and sdb is a separate drive.  A UUID isn't showing up for the external USB drive.

As a matter of fact, it didn't look like my BIOS was recognizing the drive.  Could the drive be truly corrupt?  Is there a way to fix this?  I have a ton of data on it!!

---

### Post by stanjr on 2009-04-30
I have figured out the problem.  I opened the external USB drive and discovered that it is just a SATA drive with a USB interface.  I put the SATA into my computer (making it an internal drive), and all is good.  The USB interface must have screwed up!

It was a Fantom Drive product, but the internal drive was a Western Digital.

---


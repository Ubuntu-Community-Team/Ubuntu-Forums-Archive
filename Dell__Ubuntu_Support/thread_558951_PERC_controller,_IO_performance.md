---
title: "PERC controller, I/O performance"
date: 2007-09-24
forum: Dell  Ubuntu Support
---

### Post by bsilver on 2007-09-24
I have a 2950 with a RAID 5 container running 7.04.

I am running the free VMWare Server on it with one VM (guest is Windows 2000)

The virtual system is NOT being heavily utilized (virtual processors are at ~40 to 50 percent when it's in "heavy" usage, the host isn't really going above a load of 2 according to Top).

I believe I am seeing severe speed degradation in the guest OS since migrating that guest from a physical to virtual system, and it may be disk-related.  I am getting numbers like this after having the client run through some paces (to force some flushing of the cache):

 sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   896 MB in  2.00 seconds = 447.69 MB/sec
HDIO_DRIVE_CMD(null) (wait for flush complete) failed: Inappropriate ioctl for device
 Timing buffered disk reads:  104 MB in  4.62 seconds =  22.52 MB/sec
HDIO_DRIVE_CMD(null) (wait for flush complete) failed: Inappropriate ioctl for device
$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   880 MB in  2.00 seconds = 440.08 MB/sec
HDIO_DRIVE_CMD(null) (wait for flush complete) failed: Inappropriate ioctl for device
 Timing buffered disk reads:   32 MB in  3.01 seconds =  10.64 MB/sec
HDIO_DRIVE_CMD(null) (wait for flush complete) failed: Inappropriate ioctl for device

$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   804 MB in  2.00 seconds = 402.00 MB/sec
HDIO_DRIVE_CMD(null) (wait for flush complete) failed: Inappropriate ioctl for device
 Timing buffered disk reads:   22 MB in  3.02 seconds =   7.28 MB/sec
HDIO_DRIVE_CMD(null) (wait for flush complete) failed: Inappropriate ioctl for device

************
What's going on?  Anyone else see this and have a fix for it?

---

### Post by sr20ve on 2007-09-24
removed

---

### Post by bsilver on 2007-09-24
I'll need to find the firmware update.

I'm sorry, what's TOE?

---

### Post by sr20ve on 2007-09-24
removed

---

### Post by TechZilla on 2008-06-27
same problem

what is "HDIO_DRIVE_CMD(null) (wait for flush complete) failed: Inappropriate ioctl for device"?? 

1. what does it mean
2. how do i fix it

---


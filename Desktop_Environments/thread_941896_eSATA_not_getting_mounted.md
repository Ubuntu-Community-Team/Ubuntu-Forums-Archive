---
title: "eSATA not getting mounted"
date: 2008-10-08
forum: Desktop Environments
---

### Post by stbub on 2008-10-08
I've got a Vantec NexStar Hard Drive Dock.

If I plug it in using eSATA, the drive doesn't get mounted.

I see /dev/sdg and /dev/sdg1 devices appear when I plug in, and disappear when I disconnect.

However:
 
```
 $ id
uid=0(root) gid=0(root) groups=0(root)
$ fdisk /dev/sdg

Unable to read /dev/sdg
$ hdparm -i /dev/sdg

/dev/sdg:
 HDIO_GET_IDENTITY failed: No message of desired type
$ hdparm -i /dev/sdg1

/dev/sdg1:
 HDIO_GET_IDENTITY failed: No message of desired type
$ mount /dev/sdg1 /d
mount: you must specify the filesystem type
$ mount -t ext3 /dev/sdg1 /d
mount: wrong fs type, bad option, bad superblock on /dev/sdg1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

If I use the same drive and drive dock, but with USB instead of eSATA, the drive gets mounted correctly.

Any help on what to look for much appreciated.

The motherboard is an ASUS P5W DH Deluxe, and the eSATA is on the (dreaded*) JMicron JMB363.

(*) With Hardy I was finally able to use the internal SATA port, but I still can't use the PATA ports, and, well, so far, I can't use the eSATA :-(

---

### Post by stbub on 2008-10-28
Looks like it works with the new kernel in intrepid.

---

### Post by tofudrifter on 2009-07-22
I plan to get one of these, am currently using jaunty. Thanks for the update.

edit: Works perfectly on jaunty connected via esata cable.

---


---
title: "External Hard Drive Unmountable"
date: 2009-02-18
forum: General Help
---

### Post by TheForkOfJustice on 2009-02-18
I have an external hard drive. It should still be usable but cannot mount anymore. Likely due to disk errors of some sort.

I do not care for the data that is on it so recovering it isn't a priority.  I would be happy just to be able to mount it so I can erase everything on it with gparted.

I just want my hardware back.

Help please.

---

### Post by drs305 on 2009-02-18
Does your system *see* the drive at all when it is powered?
```
sudo fdisk -l
```

If so, gparted doesn't need to mount it to remove the current partitions and allow you to reformat/repartition it.

---

### Post by pickboy87 on 2009-02-18
I don't mean to sound dumb, but have you tried the Live CD of Gparted? Does it not show in there? Is it possible to try it on a Windows based computer and see if it shows up there just so you can reformat it? Does the HDD light up or sound like it's working, just not showing up? Can you hook the drive up via IDE or SATA instead of USB and reformat it/test it that way...maybe the case is not working properly with the USB?

---

### Post by TheForkOfJustice on 2009-02-18
> **drs305 said:**
> Does your system *see* the drive at all when it is powered?
```
sudo fdisk -l
```

If so, gparted doesn't need to mount it to remove the current partitions and allow you to reformat/repartition it.

sudo fdisk -l does not show the device in its list

I also get this message when I use dmesg

> [23128.128025] usb 5-6: new high speed USB device using ehci_hcd and address 11
[23143.220047] hub 5-0:1.0: unable to enumerate USB device on port 6
[23145.224005] ehci_hcd 0000:00:10.4: force halt; handhake f887e014 0000c000 00000000 -> -110

---

### Post by TheForkOfJustice on 2009-02-19
> **pickboy87 said:**
> I don't mean to sound dumb, but have you tried the Live CD of Gparted? Does it not show in there? Is it possible to try it on a Windows based computer and see if it shows up there just so you can reformat it? Does the HDD light up or sound like it's working, just not showing up? Can you hook the drive up via IDE or SATA instead of USB and reformat it/test it that way...maybe the case is not working properly with the USB?

There is no case. This is not an internal drive in an encasement but a USB-only external backup drive.  Namely, the Maxtor OneTouch.

On Windows, one partition out of two mounted.  The contents couldn't be seen even with ifsdriver installed.  I tried reformatting the one detectable partition to NTFS but it wouldn't complete even though the progress bar went to 100% without interruption.

I tried the most recent gparted livecd and was finally able to delete the damaged partitions.  However, now it won't let me create new partitions and will often not be able to detect my drive at all after working with it once.  Essentially, I have a blank drive that's unwritable.

The lights on the drive work fine and it will act as expected but...
- It makes warm-up clicking noises more often than it should when I try to partition it.
- If it is on and plugged in while I boot my system it will stall at the BIOS screen.

I'm going to try and use the diagnostic software from the manufacturer and try and do a low-level format.  If I can be given any other advice that would be great.

I'll report my findings with the diagnostic software.

---

### Post by shane2peru on 2009-02-20
Please do share about your experiences so we know about the compatibility of the Maxtor OneTouch external hdd.

Shane

---

### Post by TheForkOfJustice on 2009-03-08
> **shane2peru said:**
> Please do share about your experiences so we know about the compatibility of the Maxtor OneTouch external hdd.

Shane

So far, so bad.  No success. 

I tried the HDD Low Level Format Tool from [http://hddguru.com/](http://hddguru.com/) but it eventually caused a system freeze, which was an odd behaviour.

They are windows tools but they are useful.  I'm going to try more of them someday.

---

### Post by shane2peru on 2009-03-08
Wow, I think you have a dud of an external drive.  I had forgotten about this post and actually bought the same drive, Maxtor one Touch, mine is the 500GB, and I did have to reformat it because I don´t use Windows, however all went well.  It works like a charm for me.  You should look into returning it.  

Shane

---

### Post by TheForkOfJustice on 2009-03-08
> **shane2peru said:**
> Wow, I think you have a dud of an external drive.  I had forgotten about this post and actually bought the same drive, Maxtor one Touch, mine is the 500GB, and I did have to reformat it because I don´t use Windows, however all went well.  It works like a charm for me.  You should look into returning it.  

Shane

It's actually quite an old drive so returning it is not a possibility.  It is likely damaged but I'm trying to be absolutely sure.  No point on throwing it out if I can revive it with some TLC

---

### Post by shane2peru on 2009-03-09
> **TheForkOfJustice said:**
> It's actually quite an old drive so returning it is not a possibility.  It is likely damaged but I'm trying to be absolutely sure.  No point on throwing it out if I can revive it with some TLC

Well that is true.  I guess if you can still use half of it´s space that is better than nothing. Hope you can get it. :D

Shane

---

### Post by Therion on 2009-03-09
I have a Maxtor One Touch 500GB as well and it's quite well behaved on my Hardy-based system; has been for some time now.  

Maybe try DBAN'ing that bad boy of yours?

[http://www.snapfiles.com/get/dban.html](http://www.snapfiles.com/get/dban.html)

(Using an alternate dl site since the homepage is 404'ing at the moment.)

---


---
title: "unable to mount volume....please help"
date: 2008-12-30
forum: Desktop Environments
---

### Post by eshant_engineer on 2008-12-30
drive other than filesystem are not mounting giving this ERROR :-

---

### Post by Zack McCool on 2008-12-30
Not to seem to dismissive, but did you try the suggestions given in the error message?  Unless you have a drive failure, those are the most likely solutions.  This usually happens when you have either an unclean Windows shutdown, or a USB drive the was unplugged without being unmounted first.

---

### Post by eshant_engineer on 2008-12-30
> **Zack McCool said:**
> Not to seem to dismissive, but did you try the suggestions given in the error message?  Unless you have a drive failure, those are the most likely solutions.  This usually happens when you have either an unclean Windows shutdown, or a USB drive the was unplugged without being unmounted first.

first option not working

followed second option but now facing a new error
  Cannot mount volume.
  You are not privileged to mount the volume 'DISK1_VOL3'.

---

### Post by taurus on 2008-12-30
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda5
sudo mkdir /media/sda5
sudo mount -t ntfs-3g /dev/sda5 /media/sda5
df -h
```

---

### Post by stderr on 2008-12-30
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda5
sudo mkdir /media/sda5
sudo mount -t ntfs-3g /dev/sda5 /media/sda5
df -h
```

ntfsfix... that was it :popcorn:

I was trying desperately to remember what it was called for about 10 minutes before I scrolled down to see taurus' post :D

Very handy little script.

---

### Post by akelsall on 2008-12-30
Dang, this is the second time tonight I've looked at posts, hoping to help people, but in turn end up helping myself :lolflag:

I have problems from time to time with my USB flash drive (which I have dual-partitioned - half NTFS and half ext3). The NTFS partition seems to get hosed up sometimes. I'll give ntfsfix a try next time.

Thanks!

Andy

---

### Post by taurus on 2008-12-30
> **akelsall said:**
> Dang, this is the second time tonight I've looked at posts, hoping to help people, but in turn end up helping myself :lolflag:

I have problems from time to time with my USB flash drive (which I have dual-partitioned - half NTFS and half ext3). The NTFS partition seems to get hosed up sometimes. I'll give ntfsfix a try next time.

Thanks!

Andy

Just make sure you use the safely remove hardware (little icon on the bottom right corner) to unmount the drive first before you unplug it from the machine while you are in windows.  

You also need to unmount it, clicking the icon on your desktop, before you unplug it in Linux too.

---


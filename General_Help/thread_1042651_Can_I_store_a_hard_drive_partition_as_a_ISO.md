---
title: "Can I store a hard drive partition as a ISO?"
date: 2009-01-17
forum: General Help
---

### Post by MR.UNOWEN on 2009-01-17
Hello, I'm wondering If I can (through Ubuntu) store a hard drive partition as an ISO and maybe at a latter time replace that partition using the ISO?

If so..

What do I need to install through synaptic package manager?

If it's text based, what are the commands I need to know?

Is there's any issues if the partition is windows?

---

### Post by pastalavista on 2009-01-17
Search the repositories (add-remove) for Gmount-iso. Be sure to use an upper case 'G' ;)

edit: you will also need 'genisoimage'... also from the repos

---

### Post by x33a on 2009-01-18
here are the instructions for making an hard disk image.

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by MR.UNOWEN on 2009-01-18
I'm a little overwhelmed with options. The reason I was asking how to back up a partition is because I know windows is going to screw up and I don't want to go through the hassle of reinstalling and in one of my computers, they're on the same hard drive, so if I do have to reinstall windows, its going to screw up Ubuntu as well.

So first of all does Gmount-iso permanently mount to that point (as in files are actually written to that point) or is it just there for the moment? Basically if I mount it, I want to be able to reboot and have windows run on it. Also I don't know how to use genisoimage.

Second, I'm confused with all those other options, a lot of them deal with networking and encryptions, so I'm just confused with that.

[SIZE="3"]**Can someone provide a simple how to for backing up and restoring a single partition on a hard disk? I just want a simple solution.**[/SIZE]

---

### Post by mssever on 2009-01-18
I don't think you want an iso. I think you just want an image. Here's what I did last time I did this (as best as I remember). I'm assuming for the sake of this example that the partition in question is /dev/sdb1. Modify as necessary:
```
sudo umount /dev/sdb1
dd if=/dev/sdb1 of=/path/to/image/file.img bs=512  # you might need sudo here
```If you need to split the image file up for some reason, you can use the split command to split it and ```
cat piece1 piece2 piece3 > full_file.img
```to rejoin it.

To mount the image: ```
sudo mount -t ext3 -o defaults,loop image_file /mount/point
``` Substitute the correct filesystem type for ext3.

EDIT: To restore a partition from an image, I assume the following would work, though I've never tried it: ```
sudo dd if=/path/to/image/file.img of=/dev/sdb1 bs=512
```Of course, adjust sdb1 as necessary.

---


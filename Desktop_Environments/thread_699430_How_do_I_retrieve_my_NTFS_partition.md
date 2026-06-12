---
title: "How do I retrieve my NTFS partition"
date: 2008-02-17
forum: Desktop Environments
---

### Post by eshkar on 2008-02-17
Hey guys, I am a nub to Ubuntu and Linux, it is an amazing system, I am leaving windows for this, much nicer system. I have a 300 gig SATA drive that has three partitions on it, one for media, one for running all of my windows programs and also has all of my documents on it, and another smaller one for Virtual memory, now when I installed Ubuntu (7.10)  on another spare hard drive I had and attached my SATA as an extra hard drive Ubuntu automatically saw my media partition and and my Virtual memory partition, but my other partition with all of my documents on it and another 145 gigs of storage is no were to be found, how do I get it?
Also how do I auto-mount my SATA partitions on startup once I retrieve it?
Thanks

---

### Post by kaiju on 2008-02-18
```
sudo lshw -businfo -C disk
``` and
```
sudo fdisk -l
```
will show you what devices and partitions you have on your system. you can then add the missing ones to /etc/fstab so they will be mounted at bootup.
(always make a backup copy before editing important files: "sudo cp /etc/fstab /etc/fstab.original")
you can edit your fstab with
```
sudo gedit /etc/fstab
```
(you can do a little search here if in doubt about what parameters to use for the different file systems)
when you are done, you can mount everything listed in /etc/fstab with
```
sudo mount -a
```

---

### Post by eshkar on 2008-02-19
dunca

---


---
title: "n00b question: Clone drive?"
date: 2006-10-03
forum: Desktop Environments
---

### Post by Duo Maxwell on 2006-10-03
I'm in need of moving up to a bigger HD, I'm looking at the [Seagate ST3320620AS]("http://www.newegg.com/Product/Product.asp?Item=N82E16822148140") and would like to clone over the entire install on the current 80Gb HD in the box now, I've done this before on my iBook using Carbon Copy Cloner but I don't know how to do this in any other OS, let alone on my AMD Ubuntu box.

---

### Post by bazzer on 2006-10-03
Several options are available - searchy for dd for the really basic (but powerful) way, or if you want a cool way to clone a drive and restore without too much effort, have a look for the [System Rescue CD]("http://www.sysresccd.org/"), which I use with a USB drive to blat images back and forth...

---

### Post by Duo Maxwell on 2006-10-03
That'll let me just plug in the new drive, format it clone over shutdown, unplug the 80 and when I turn on be booting off the 320Gb?

---

### Post by bazzer on 2006-10-04
Well not exactly, what I do to restore a drive is as follows:
Plug USB drive in
Boot to Rescue CD
mkdir /mnt/usb
mount /dev/sda1 /mnt/usb
cd /mnt/usb
sfdisk --force /dev/hda < partition-file
run_qtparted [and format the partitions just created]
partimage [and copy the drive image back to the new drive]
grub
  root (0,0)
  setup (hd0)
  quit
Reboot

Obviously you'll need to make a partition file (hint - use sfdisk /dev/hda > partition-file), and an image of your drive (with partimage) before you can restore it, and in my experience, if the new drive is bigger than the old one you'll need to fix the partition sizes in qtparted as you go.

I'm afraid there are so many variables here, you'll have to dig the manuals. But, it's quite good when you get the hang of it, you'll understand how linux treats partitions and drives....

---


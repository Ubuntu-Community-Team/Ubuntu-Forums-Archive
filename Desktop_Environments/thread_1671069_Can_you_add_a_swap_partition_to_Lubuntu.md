---
title: "Can you add a swap partition to Lubuntu?"
date: 2011-01-19
forum: Desktop Environments
---

### Post by M_Mynaardt on 2011-01-19
Hi!

I have a live/persistent installs of Lubuntu 10.04 on a USB-HDD.  It's on a 320 GB portable drive.  I've partitioned it so that 80 GB is for the Lubuntu live install and the remaining 240 GB is another partition dedicated to storing **stuff**.  So this USB-HDD is doing double duty.

The thing is, I was paying so much attention to making the persistent install work without making a mess of the boot loader (I did that in the past; twice!) that I had overlooked the fact my live install does _not_ have a swap sartition on it.  I just assumed (incorrectly) that the swap partition on would just be part and parcel of the installation.  Can anyone tell me of a way to ***add*** a swap partition to each of my live installs?  Without losing any data or anything like that.

It's probably not doing any harm not having a swap partition, but I'm assuming that my live install would be that much more efficient with it.

Thanks!

---

### Post by gordintoronto on 2011-01-19
If you have not run out of memory, you don't actually need a swap partition.

You could boot from a Gparted LiveCD and shrink the data partition, then turn the free space into a swap partition.

---

### Post by M_Mynaardt on 2011-01-19
> **gordintoronto said:**
> If you have not run out of memory, you don't actually need a swap partition.

You could boot from a Gparted LiveCD and shrink the data partition, then turn the free space into a swap partition.

That takes a bit of worry off if a Swap Partition isn't actually _needed_!

Do you know if that Gnome Disk Utility can do any of that resizing stuff, if I feel I ***really really*** have to?

Thanks!

---

### Post by SeijiSensei on 2011-01-19
You don't need a partition to create swap.  You can use a file within the operating system instead as described [here](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/).  Just remember to prefix the commands with "sudo" since Ubuntu doesn't support root logins.

---

### Post by ssulaco on 2011-01-20
> **M_Mynaardt said:**
> That takes a bit of worry off if a Swap Partition isn't actually _needed_!

You will need a swap partition if you suspend-to-disk.....
nevermind, I failed to see "live/persistent installs.....320 GB portable drive"

---

### Post by lance bermudez on 2011-01-25
do all this in the same spot in the termanal the example is in /
cd /
sudo dd if=/dev/zero of=/swapfile bs=1M count=2048
sudo mkswap /swapfile
sudo swapon /swapfile

will make a 2gb swap file in / the last command will turn on the swapfile and to turn it off do sudo swapoff /swapfile if you want to have it turned on and off when you login then add the below to the end of your fstab file in /etc/fstab you will have to be sudo to do it. sudo gedit /etc/fstab

/swapfile none swap sw 0 0

---

### Post by M_Mynaardt on 2011-01-25
> **lance bermudez said:**
> do all this in the same spot in the termanal the example is in /
cd /
sudo dd if=/dev/zero of=/swapfile bs=1M count=2048
sudo mkswap /swapfile
sudo swapon /swapfile

will make a 2gb swap file in / the last command will turn on the swapfile and to turn it off do sudo swapoff /swapfile if you want to have it turned on and off when you login then add the below to the end of your fstab file in /etc/fstab you will have to be sudo to do it. sudo gedit /etc/fstab

/swapfile none swap sw 0 0


Cool!  I'll give that a go and see what happens!

Thanks!

---

### Post by cascade9 on 2011-01-25
If you do setup a swap partition (or file) on your USB HDD, set the swapiness very low (even to '0').  

USB HDDs have poor bandwidth compared to internal HDDs, and USB does use some CPU resources. If the system decides to unload a program from RAM to swap its going to take a while, and slow down anything else you are doing on the system.

---


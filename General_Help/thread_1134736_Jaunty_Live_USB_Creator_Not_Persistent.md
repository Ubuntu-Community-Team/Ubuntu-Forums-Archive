---
title: "Jaunty Live USB Creator Not Persistent"
date: 2009-04-23
forum: General Help
---

### Post by max.goedjen on 2009-04-23
Hey Guys,
Just updated my machines to 9.04, and thought it'd be nice to put it on my flash drive as well. I downloaded the live cd for 9.04, and set the persistence amount to 2GB in the live usb creator, but it just seems to skip right over it (progress indicator skips from 25% to done), and no changes are saved on the usb drive. Anyone else having this issue/know of any workarounds?

---

### Post by HankB on 2009-04-23
Try formatting your USB drive first. Some of these tools don't work well if the drive already has stuff on it.

If that's not the issue... sorry, I cannot help. 

-hank

---

### Post by max.goedjen on 2009-04-23
Nope, it was formatted, (tried formatting/installing twice), that's not the issue. It just seems to be skipping creating the persistent overlay.

---

### Post by jimv on 2009-04-23
If you have a 4gb+ drive, you can install ubuntu straight onto it like a normal hd.

---

### Post by max.goedjen on 2009-04-24
Tried again with a 1GB persistence, seems to take. Haven't had time to experiment very thoroughly (each process takes a while, obviously), but I'd guess the limit for persistence is 2047MB.

---

### Post by dcstar on 2009-04-24
> **jimv said:**
> If you have a 4gb+ drive, you can install ubuntu straight onto it like a normal hd.

It is not an "install", it is creating a USB install device.

---

### Post by dcstar on 2009-04-24
> **max.goedjen said:**
> Tried again with a 1GB persistence, seems to take. Haven't had time to experiment very thoroughly (each process takes a while, obviously), but I'd guess the limit for persistence is 2047MB.

Did it create a second FAT32 partition?

---

### Post by jimv on 2009-04-24
> **dcstar said:**
> It is not an "install", it is creating a USB install device.

I'm saying that he can install Ubuntu onto the thumbdrive instead of messing with the persistence.

---

### Post by dcstar on 2009-04-24
> **jimv said:**
> I'm saying that he can install Ubuntu onto the thumbdrive instead of messing with the persistence.

A USB system created by the tool is **not** a standard install, it is a "Live" Ubuntu install CD on a USB instead of a CD.

It has things set up to use the characteristics of the USB device correctly (RAM disk, minimum writes etc), which a standard install onto any SD device does not.

---

### Post by iminj on 2009-04-24
+1 to the original problem reported by max.goedgen

I did the LiveUSB Creator install (9.04 to a formatted 8GB flash drive). The 1st attempt, I used all the available space for the storage file (casper?) - and persistence failed.

On the 2nd attempt, I decided to stay under 4GB, so I chose 3.9 - still no persistence.

Looks like a bug to me.

---

### Post by pi.boy.travis on 2009-04-24
+1  Here is my thread: [http://ubuntuforums.org/showthread.php?t=1135732](http://ubuntuforums.org/showthread.php?t=1135732)

I'm having the exact same issue.  There aren't any open bug reports for usb-creator in launchpad right now.  Should one be filed?

---

### Post by dcstar on 2009-04-26
> **iminj said:**
> +1 to the original problem reported by max.goedgen

I did the LiveUSB Creator install (9.04 to a formatted 8GB flash drive). The 1st attempt, I used all the available space for the storage file (casper?) - and persistence failed.

On the 2nd attempt, I decided to stay under 4GB, so I chose 3.9 - still no persistence.

Looks like a bug to me.

I now remember using the USB creator (unsuccessfully) months ago trying get persistence to work, but gave up.

I then just created one without any persistence space, then manually created an EXT2 partition labelled "casper-rw" and on boot-up I had a system with persistence!

---

### Post by pi.boy.travis on 2009-04-26
> **dcstar said:**
> I now remember using the USB creator (unsuccessfully) months ago trying get persistence to work, but gave up.

I then just created one without any persistence space, then manually created an EXT2 partition labelled "casper-rw" and on boot-up I had a system with persistence!


Did you have to edit Syslinux(bootloader)?

---

### Post by steveleader on 2009-04-26
hey!
i've got the same problem here. no matter how big the file should be, after copying the systemfiles it skips to the end, and doesn't create a file.
my pendive is a 8gb one.

---

### Post by Haywood on 2009-04-27
Looking at the file structures of a USB Startup disk created with Ubuntu 8.10 & Ubuntu 9.04, it looks like a persistence file in the USB Startup disk made with 9.04 is not even created in 9.04, no matter what size it is.
I did find this [http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/]("http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/"). Followed the instructions, tested it with the 2GB casper-rw  download and it works. Including adding programs (Truecrypt, KeepassX), data files, hyperlinks, and users.  I also disabled the automatic login and timed login.
I also just down loaded the 3GB casper-rw file and extracted it to the root of a USB Startup disk that had been created with the USB Startup Disk utility on Ubuntu and everything seemed to work as advertised.

---

### Post by steveleader on 2009-04-27
yeah, i did the same today. i created a usb startup disk with the live image and created the casper-rw file myself afterwards. you can either do it the way explained in the tutorial on [http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/) or you scroll down and get a file, which only has to be copied to the root folder of the usb drive.
works fine :guitar:

---

### Post by pi.boy.travis on 2009-04-27
Thanks for the links!  I didn't know you could change the size later.

---

### Post by Myst3 on 2009-05-03
> **dcstar said:**
> I now remember using the USB creator (unsuccessfully) months ago trying get persistence to work, but gave up.

I then just created one without any persistence space, then manually created an EXT2 partition labelled "casper-rw" and on boot-up I had a system with persistence!

I think i forgot the step. When i boot up, The casper-rw partition was showing up on my desktop.

Here my partition on my 8gb Apacer pendrive :
1gb fat32 partition
5.6gb EXT3 casper-rw partition
1.0gb EXT3 home-rw partition
46mb swap partition

---


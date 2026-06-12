---
title: "Access Files On USB Key From USB Booted Ubuntu"
date: 2009-04-05
forum: General Help
---

### Post by jason331 on 2009-04-05
I just created a bootable USB Ubuntu installation and it works great but I am having trouble accessing the files stored locally on the USB key itself once I boot from the key. There does not appear to be a way to browse the FAT32 partition on the key (same partition as the Ubuntu live files) to access other files I have saved on that partition.

Any ideas how I can mount the local USB key from a USB-booted Ubuntu live session so that I can browse to files stored on it?

I am using 8.10 desktop and used the guide from [PenDriveLinux]("http://www.pendrivelinux.com") for my persistent bootable installation.

---

### Post by jason331 on 2009-04-06
Bueller? Anyone?

I'm just trying to find a way to save files onto my USB key's single FAT32 partition and then access those files when booted from the USB key into Ubuntu. When I boot from the USB key (live session) I don't see a way to mount the local USB key as a folder I can browse.

Any ideas at all?

---

### Post by anjilslaire on 2009-04-06
I tried that once, only I was booted via a USB key and was trying to take a backup from the hard drive to the live key I was using. Talk about a mess ;)

However, it *should* not need to be mounted as a usb device, really. It's not once in the sense you're thinking anymore, it is the root drive of your system while booted as a live environment.
Try digging around in /home/ubuntu/, or somewhere similar

---

### Post by jason331 on 2009-04-06
I think the "/" directory and all folders beneath are virtually created via the filesystem.squashfs file but I could be wrong. My USB-booted Ubuntu is the same as a live CD session except it is running from a USB key and I can save my settings in a casper-rw file on the root of the key. 

Just for grins, however, I tried booting from the key and browsing around the filesystem but did not see any of my files. Here is what my USB key looks like when viewed from Windows:

[IMG]http://www.jasonsconsulting.com/images/USBKey.JPG[/IMG]

---

### Post by jason331 on 2009-04-06
The only occurrence of this problem I can find after countless hours of Googling is [this one]("https://bugs.launchpad.net/ubuntu/+bug/93074").

It seems to me this should be treated like I were just trying to browse the contents of the live CD when booted off of that same live CD.

---

### Post by jason331 on 2009-04-06
Nevermind, answered my own question...

```

sudo mkdir /mnt/usb
sudo mount -t vfat /dev/sda1 /mnt/usb

```

Files on the USB key are now browse-able.

---

### Post by Dilligaf on 2009-04-18
You should see your files in /cdrom/ off of root

Mike

---


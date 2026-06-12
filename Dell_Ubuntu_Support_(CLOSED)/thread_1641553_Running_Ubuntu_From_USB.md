---
title: "Running Ubuntu From USB"
date: 2010-12-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zkush on 2010-12-09
So I have Ubunto on my USB flash drive and I can get it to run. The only thing is, I can't access the internet. I have a Dell Wireless 1397 WLAN Mini-Card. I don't want to install Ubunto to the hard drive, I only want to run it from USB. Is it possible for me to use the USB as a hard drive so I can successfully use the drivers to access the internet?

---

### Post by C.S.Cameron on 2010-12-09
If you do aa Full install to USB you can do anything that an install to a desktops HDD can do... (only slower).

---

### Post by fjgaude on 2010-12-09
> **zkush said:**
> So I have Ubunto on my USB flash drive and I can get it to run. The only thing is, I can't access the internet. I have a Dell Wireless 1397 WLAN Mini-Card. I don't want to install Ubunto to the hard drive, I only want to run it from USB. Is it possible for me to use the USB as a hard drive so I can successfully use the drivers to access the internet?

I think you will have to have a LAN connection to install the wireless driver you need. You don't have to have a full install, but need to be on the Internet to download it. If you can do that you can run from the USB, but each time you boot up you will have to do the LAN event again. Bummer.

What I did once with 10.10 was install onto the USB, get the driver which stays on the writeable USB and I was good to go without further issues.

Let us know if you need help.

---

### Post by gibbylinks on 2010-12-09
How did you create the USB stick ?

If you create it from a running Ubunutu system using "Startup Disk Creator" there is an option to use all the memory on the stick to save setting etc. You need to check the radio button for "stored in extra space" and push the slider all the way over to the right for maximum space.

This will create a "persistent" area on the stick.

If you then boot from it connected to the net you should be able to download and install the drivers.

see also [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) for other ways.

---

### Post by zkush on 2010-12-09
> If you do aa Full install to USB you can do anything that an install to a desktops HDD can do... (only slower).

How do I do a full install?


> **gibbylinks said:**
> How did you create the USB stick ?

If you create it from a running Ubunutu system using "Startup Disk Creator" there is an option to use all the memory on the stick to save setting etc. You need to check the radio button for "stored in extra space" and push the slider all the way over to the right for maximum space.

This will create a "persistent" area on the stick.

If you then boot from it connected to the net you should be able to download and install the drivers.

see also [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) for other ways.

I used UNetbootin to put Ubuntu onto my USB stick.

---

### Post by fjgaude on 2010-12-09
To do a full install onto a USB drive, using Ubuntu 10.10: put the liveCD with 10.10 on it into the CD/DVD reader, let it get to the "try" or "install" screen, click, instal, then let it get to the point where you are asked what partition to use. Say, "manual", and then scroll down the screen of partitions to get to the last one, which should be a **sr1** type drive, your USB.

Make sure you have the USB (formatted to FAT32) plugged-in before you boot the liveCD that has Ubuntu on it.

I believe this works with 9.10, 10.4 and 10.10, at least it did for me.

Let us know what happens.

---

### Post by ppv on 2010-12-09
Universal usb installer is another GUI based tool to create live usb sticks. It also mostly has a persistence option where you could just tell it to create a persistent stick. You may also specify the size of the persistent storage.

---

### Post by C.S.Cameron on 2010-12-09
> **zkush said:**
> How do I do a full install?


Step by Step for 10.10:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
(Optional partition for use on Windows machine)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 4GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 6 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 8 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB, same size as RAM), Beginning and "Use as" = "swap area" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---


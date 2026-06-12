---
title: "[SOLVED] Can I boot my PC from a USB drive?"
date: 2008-12-27
forum: General Help
---

### Post by tinker123 on 2008-12-27
Hi;

I have Ubuntu 8.04 running on a 6 year old PC.  I would like to make a bootable USB stick with Ubuntu 8.10 on it.  I checked the bios on my computer.  In the boot/boot priority section it has "removable devices" listed, but in that section the only removable device there is an old floppy drive.

Does this mean I can't boot from a USB thumb drive?

If so, is there anything I can do about it short of getting a new computer?

Thanks in advance for any information.

---

### Post by Monotoko on 2008-12-27
If its 6 years old i dont think there is much chance of getting it work.
Only PC's 2 years old and newer have the capibility to boot from USB, its a rather new thing

---

### Post by sedawk on 2008-12-27
First, you can check if there is a newer bios for your
motherboard that adds new features like booting USB floppy
or USB harddisk.

Second, you can also check if bootable floppies are only listed
for removable media or also for "normal" devices.
Then "removable floppy" might be a USB floppy drive.

Third, if removable media means a USB floppy drive you
might be lucky to boot from an usb stick too.
But that usb stick has to be formatted like
a floppy, that is without a partition table.
(called "superfloppy", when formatting with
 mkdosfs see option "-I")

(I think I have a PC from 2001 that can at
 least boot USB floppy.)

---

### Post by tinker123 on 2008-12-30
This site has the easiest directions for installing Ubuntu ( & other distros ) onto USB drives:

[http://www.pendrivelinux.com](http://www.pendrivelinux.com)

Also there are directions for making a "boot to USB" CD if your PC like mine is too old to do it.  Once the CD starts to boot, it hands booting over to the USB drive.

This is better for me as fewer people, including me have floppy drives ( mine broke years ago ).

I will look into upgrading my bios too.

---

### Post by Icebear on 2008-12-30
I  have a 4 year old computer and I can not boot from the usb drive. But I have a ubuntu already on my computer and wanted to have one on a usb hard drive to paly and break.

I found out that I could load the linux kernel from grub then I had the drivers needed and I could load ubuntu from the usb drive

I did a regular install from a Ubuntu Live CD
I installed and choose the destination to be the USB drive (USB drives are normally /dev/sdb1)replace the number to what is correct with your setup)
**Just be before clicking OK** to start the install click "advanced" and select where you want the GRUB loader. Select the USB disk to avoid overwriting the existing grub menu on the internal disk.

Then I booted to my normal ubuntu on the internal drive (at the moment I could not load the usb) 

Then I made a new directory in the /boot folder

sudo mkdir /boot/usbboot

then for making life easy I to copied the initrid.img-2.6.27-9-generic and  vmlinuz-2.6.27-9-generic from the boot folder on the usb drive to my home folder  
then copied them to my new folder into /boot/usbboot

sudo cp  initrid.img-2.6.27-9-generic /boot/usbboot
sudo cp  vmlinuz-2.6.27-9-generic /boot/usbboot

then I had to edit my grub menu list

sudo /boot/grub/menu.lst

then I added on the bottom a new entry




title		usb	kernel 2.6.27-9-generic

root 		(hd0,5)

kernel		/boot/usbboot/vmlinuz-2.6.27-9-generic root=/dev/sdb5

initrd		/boot/usbboot/initrd.img-2.6.27-9-generic

boot

to find the right root I looked at my normal ubuntu entry and copied that because the kernal is at the same spot.

In the kernel line you need to find the listing for your usb drive in the normal ubuntu
I did a sudo fdisk -l and worked it out (you can also use the uuid number instead) [B]then you will need to change the sdb5 to where your new install is.
[/B]
Make sure your vmlinuz and initrd.img have the same number. Also when there is a update and if a new kernel is added you will need to copy the new files over and change it in your grub. **That is why my vmlinuz and initrd.im numbers will be different from your base install you need to put the numbers you copied in your menu.lst**.

---


---
title: "no BIOS support for USB = no boot from USB.?"
date: 2008-12-04
forum: General Help
---

### Post by unxzst on 2008-12-04
Is there any hope for running a Ubuntu from a USB drive, if my old BIOS does not support USB booting? Any chance someone might have created a boot CD with USB drivers?

What if boot from USB is disabled, and BIOS is password-protected? Any way to run from USB then?

---

### Post by Jose Catre-Vandis on 2008-12-04
Two ways, depending on how you want to do it.

1. boot from CD then from your Ubuntu on USB
   [www.pendrivelinux.com](www.pendrivelinux.com) has the isos you may need

2. follow my howto to shift the ISO over to your hard drive and grub (assumes a working grub on your HDD)
   [http://ubuntuforums.org/showthread.php?t=992426](http://ubuntuforums.org/showthread.php?t=992426)

---

### Post by unxzst on 2008-12-05
i'm going to give pendrivelinux another shot, so far i havnt been succesfull.

what if the computer i'm trying to boot is a school computer, and i dont want to write anything to the HD? can i run this from a livecd?

---

### Post by Jose Catre-Vandis on 2008-12-06
yes, the persistent usb install from pendrivelinux and via the usb creator on Ibex is non destructive (unless you start mounting the HDD on the host PC and fiddle!)

---

### Post by unxzst on 2008-12-06
persistent yes, but not expandable. some packages fail to install, some just won't work. it uses something called casper, i think that may be the problem.

---

### Post by gregphil on 2008-12-06
I had this problem, I wanted to update the internal disk to KDE4 but keep a KDE 3.5 installation on an external USB disk. My BIOS (5 years old) did not have a boot from USB option.

A simple solution, someone on the forums suggested, is this: copy the necessary boot files from the USB disk to the root of a disk you CAN boot from, and then tweak the grub menu.lst file.

Specifically:
1) Boot from the regular Ubuntu or Kubuntu Live! CD
2) Select install and pick the destination as the USB disk
3) Just be before clicking OK to start the install click "advanced" and
select where you want the GRUB loader. Select the USB disk to avoid overwriting the existing grub menu on the internal disk.
4) Once the install is complete you won't be able to boot to it (yet) because the BIOS does not support USB drives during the boot process.

5) Boot to a different linux distro or OS and then copy the kernel image files* from the USB disk /boot to the /boot directory of your regular boot drive.
6) Then EDIT the active grub menu.lst on the regular boot disk to add a section for the new USB installation.  This is not hard because you can just copy the lines from the menu.lst in the USB disk /boot/grub/menu.lst.  
7) The final TRICK is to change the USB disk's entry "root" line to **point at** the location of **the copies** of the kernel files **instead of** at the kernel files on **the USB disk**. Leave the UUID's pointing at the USB disk.

For example my working grub menu.lst looks like:
************************************************************************
## ## End Default Options ##

title        Microsoft Windows XP Professional
root        (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

title        Ubuntu  8.10, kernel 2.6.27-9-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=3196e3f5-d538-4a64-aad8-b3eda368d85b ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Kubuntu 8.10, kernel 2.6.27-9-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=8441227a-acd7-4bda-9aaa-d74251eee147 ro quiet splash
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title           Kubuntu 8.04.1, kernel 2.6.24-22-generic
**root            (hd1,0)**
kernel          /boot/vmlinuz-2.6.24-22-generic root=UUID=d93ea397-d388-4bd3-8cfb-b8a2c5e3c0cb ro quiet splash
initrd          /boot/initrd.img-2.6.24-22-generic
savedefault
boot
**********************************************************************
Notice how the final entry (the USB install) points at (hd1,0) which is my regular boot drive, instead of at the USB disk.  I have Windows Xp on the primary IDE disk, Ubuntu and Kubuntu and separate sada disks, and kbuntu 3.5 on an external USB disk.  The BIOS is set to SCSI boot (sada drive) and for some reason chooses hd1 instead of hd0 as the boot disk.  In any event this all works and was easy to install.  However you do need to remember to copy the kernel files from the /boot directory fo the USB disk  to the /boot directory of the real boot drive each time the USB kernel gets upgrades.  To be safe I just copy all the kernel files, but I don't think every one is needed.

*kernel image files:
abi-2.6.24-22-generic
config-2.6.24-22-generic
initrd.img-2.6.24-22-generic
System.map-2.6.24-22-generic
vmlinuz-2.6.24-22-generic

Good Luck!

---

### Post by unxzst on 2008-12-08
thanks, gregphil! i will try what you have suggested. 
my problem is booting at school, where i don't have access to the HD, so I'm trying to do this from a CD.

---

### Post by Jose Catre-Vandis on 2008-12-19
> **unxzst said:**
> persistent yes, but not expandable. some packages fail to install, some just won't work. it uses something called casper, i think that may be the problem.

In my experience, this seems to be related to the amount of persistent space you create. It's scary how much disk space installed packages take up (plus the deb files in /var/cache/apt/archive).

Give yourself a chance and make your persistence space as big as possible, minimum 1GB. Try to customise a flash drive install on a 1GB stick just doesn't give you many options...

To check your free persistent space issue this command at the command line:
```
df -lh
```
and look at the rootfs line

---


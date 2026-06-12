---
title: "Grub loading  - Error 15"
date: 2007-08-29
forum: Dell  Ubuntu Support
---

### Post by ctheodore on 2007-08-29
I received this error after installing Ubuntu Server to replace an already working install of Ubuntu (regular). In trying to resolve the above error, I received the steps that follow from another link on how to make a Boot CD:  MY QUESTION IS HOW DO I GET TO THE FIRST STEP. Where do I get the "syslinux" package?  Please help me figure this out.

**HOWTO: Make a Ubuntu Boot-CD (Like a boot floppy)** 

--------------------------------------------------------------------------------

This will make a boot cd which is similar to a boot floppy. It bypasses grub, but still uses your partitions. Really only useful if you mess up grub, or copy your installation to a new hard drive and need to reinstall grub. It's not a full O/S on CD. Just the kernel. It's always nice to have in case something gets messed up.

**( 1 ) Install syslinux (package).**

( 2 ) make a directory called bootcd

( 3 ) copy /usr/lib/syslinux/isolinux.bin to bootcd

( 4 ) copy desired kernel image from /boot to bootcd/linux. Example:
cp /boot/vmlinuz-2.6.10-4-386 bootcd/linux

( 5 ) copy desired initrd.img from /boot to bootcd/initrd.img. Example:
cp /boot/initrd.img-2.6.10-4-386 bootcd/initrd.img

( 6 ) edit bootcd/isolinux.cfg and place the following line
DEFAULT linux initrd=initrd.img ro root=<your-root-dev>
Where, <your-root-dev> will be something like /dev/hda1. If you don't know your root device, look at your current grub config in /boot/grub/menu.lst.

( 7 ) make your iso image via (you should be one directory below bootcd).
mkisofs -o bootcd.iso -b isolinux.bin -c boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -J -hide-rr-moved -R bootcd/ 

( 8 ) burn the image to CD.

( 9 ) Test it.

---

### Post by logos34 on 2007-08-29
> I received this error after installing Ubuntu Server to replace an already working install of Ubuntu (regular). In trying to resolve the above error, I received the steps that follow from another link on how to make a Boot CD: MY QUESTION IS HOW DO I GET TO THE FIRST STEP. Where do I get the "syslinux" package? Please help me figure this out.

You might want to try the suggestions here first (i.e. SuperGrub cd):
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)


If you still want syslinux there's a deb in the repos:
[B]
sudo apt-get install syslinux[/B]

Or use the official Gnu guide to making a GRUB boot CD:
[http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html)

---


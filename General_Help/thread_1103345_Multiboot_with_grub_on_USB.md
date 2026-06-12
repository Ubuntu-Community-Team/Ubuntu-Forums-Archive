---
title: "Multiboot with grub on USB"
date: 2009-03-22
forum: General Help
---

### Post by mokbuntu on 2009-03-22
Hi guys,
  I have been trying to setup a USB drive with a partition that has Partition Magic in one fat16 partition with GRUB installed in the MBR.
The other partitions that i have live cd images of Fedora 10, Jaunty alpha 6 and gOS. I have setup menu.lst to boot these images.  However, during the middle of the boot process, it drops down to a basic shell.  Happened in Fedora.  gOS and Ubuntu dropped down to some basic bash prompt.  Not sure what i am doign wrong.  When i try to reboot again, the MBR in the usb is gone.  I have to reinstall grub.

Here is the menu.lst
[I][INDENT]title  Console (Boots to the shell)
kernel /pmagic/bzImage noapic  root=/dev/ram0 init=/linuxrc vga=normal sleep=0 consoleboot ramdisk_size=25000 keymap=us
initrd /pmagic/initrd

title gOS Gadgets 3.1
root (hd0,5)
kernel /gos-3.1/casper/vmlinuz file=/gos-3.1/cdrom/preseed/ubuntu.seed boot=casper quiet splash ubiquity/reboot=true noprompt -- loglevel=0
initrd /gos-3.1/casper/initrd.gz

title Ubuntu - Jaunty Jackalope - Alpha 6
root (hd0,5)
kernel /Ubuntu-Jaunty-a6/casper/vmlinuz file=/Ubuntu-Jaunty-a6/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --
initrd /Ubuntu-Jaunty-a6/casper/initrd.gz
[/INDENT][/I]
The file system in hd0,5 is JFS.  Could that be causing this issue?

---

### Post by Rallg on 2009-03-22
Don't know about JFS, but here is a possibility: The MBR directs the boot process to read GRUB from some location. That location might be on one of the partitions other than (hd0,0). Note that on the USB, hd0 is the USB itself, not your hard drive. In any case, perhaps the GRUB menu.lst is not the one you think it is? That is, perhaps the MBR is directing toward GRUB on (hd0,n) with n not equal to 0, which has an incompatible menu.lst?

Have a look at /boot/grub/menu.lst in each partition, and see if there is any oddity.

As I wrote, that is just a possibility.

---


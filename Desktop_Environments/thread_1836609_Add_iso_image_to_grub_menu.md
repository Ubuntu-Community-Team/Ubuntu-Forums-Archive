---
title: "Add iso image to grub menu"
date: 2011-08-31
forum: Desktop Environments
---

### Post by DeadEnd on 2011-08-31
I want to add ghost4linux .iso file to the grub menu.
I am struggling to create the correct entry to add to /etc/grub.d/40_custom.

From what I can gather the image contains ramdisk.lzma.

Unfortunately the examples I have found so far do not contain any references to this image type.

Any pointers to how this menu entry would look to boot g4l from the grub menu ?

thanx

---

### Post by grahammechanical on 2011-08-31
I do not think that Grub will load an iso image. This is what the sourceforge site says about goast4linux

> G4L is a hard disk and partition imaging and cloning tool. The created images are optionally compressed and transferred to an FTP server or cloned locally.

It is not an operating system.

I guess that you burn the iso to CD or DVD and run from the CD drive to create the cloned image of the drive. Which you then burn to disc.

Regards.

---

### Post by DeadEnd on 2011-08-31
> **grahammechanical said:**
> I do not think that Grub will load an iso image. This is what the sourceforge site says about goast4linux



It is not an operating system.

I guess that you burn the iso to CD or DVD and run from the CD drive to create the cloned image of the drive. Which you then burn to disc.

Regards.

I have used grub menu to start the boot process with quite few distro.iso files.

I decided to use clonezilla live instead and leave ghost 4 now (sic) by modifying a grub menu entry I found in this thread.

I have the .iso file located at /boot/clonezilla.iso

[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

   menuentry "Clonezilla live" {
   set isofile="/boot/clonezilla.iso"
   loopback loop $isofile
   linux (loop)/live/vmlinuz boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run=\"ocs-live-general\" ocs_live_extra_param=\"\"  
   ocs_live_keymap=\"\" ocs_live_batch=\"no\" ocs_lang=\"\" vga=788 ip=frommedia nosplash toram=filesystem.squashfs findiso=$isofile
   initrd (loop)/live/initrd.img
  }

All is well and booting fine.

BTW:
I add the iso files to grub menu along with other customisations and tools then remastersys the system as a live cd/dvd then use the startup disk creator to add it to a 4GB thumb drive and burn to DVD.

This gives me a useful tool to aid me in repairing and cloning computers.

 .

---


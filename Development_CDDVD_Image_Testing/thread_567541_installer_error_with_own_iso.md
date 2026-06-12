---
title: "installer error with own iso"
date: 2007-10-04
forum: Development CD/DVD Image Testing
---

### Post by kreativchaos on 2007-10-04
Hi,

I want to know what went wrong:

I mounted the ubuntu iso with

mount -o loop in /mnt/iso

then I copied everything to another dir and tried to create the iso from the content of this dir (I added another distribution too on this DVD to have both on one DVD)

cp -r /mnt/iso/* /dir/

mkisofs -o ../../sda3/multiboot_isos/debian.iso -r -J -no-emul-boot -boot-load-size 4 -boot-info-table -b isolinux/isolinux.bin -c isolinux/boot.cat -V 'Debian 4.0 r1 i386 Bin-1' debian

(I also tried LOTS of other parameters)

But the problem is:

The installer does not accept the CD. It boots but it then says that the CD is invalid. He says:
"The CD-ROM does not seem to contain a valid 'Release' file, or that file could not be read correctly'.

On terminal 4 I can see the following error message.

Detected CD 'Ubuntu 7.04 "feisty fawn" - Release i386 (20070415)
Error reading Release file; unable to determine distribution

---


---
title: "Installing Grub on partition not MBR"
date: 2006-08-28
forum: Desktop Environments
---

### Post by kq6up on 2006-08-28
I want to install Ubuntu over my old Slackware partition.  I use my windows nt (XP) bootloader to load Linux and FreeBSD on this box.  I would like to keep it that way.  This means I need to install the bootloader on the partition that Ubuntu will dwell on (not the MBR), and tell nt loader where to find the bootloader for Ubuntu.  Any suggestions?

Chris Maness

---

### Post by mlind on 2006-08-29
Ubuntu installer doesn't allow you to do that, so make sure you skip GRUB install part if doing a fresh install.

Take a look at grub manual
[http://www.gnu.org/software/grub/manual/grub.html#Installation](http://www.gnu.org/software/grub/manual/grub.html#Installation)

> 
If you want to put GRUB into the boot sector of a partition instead of putting it in the MBR, specify the partition into which you want to install GRUB:

*     grub> setup (hd0,0)*


I recommend to backup necessary bits from that partition before doing this.

---


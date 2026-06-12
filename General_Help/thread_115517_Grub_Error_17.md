---
title: "Grub Error 17"
date: 2006-01-10
forum: General Help
---

### Post by eqisow on 2006-01-10
So I recently installed Kubuntu 5.10 over my old Ubuntu installation and upon booting Grub gives me an error 17. Error 17 means:

17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

The grub config files were misconfigured. No biggy, grub always recognizes my drives wrong; one sata and one ata. They should now be correct, however. I have included both as attachments. Kubuntu is on sda1 (reiserfs), windows is on sda2 (ntfs), and hdd1 (fat32) is storage.

Any ideas guys?

---

### Post by eqisow on 2006-01-10
OK, so I'm now under Knoppix 3.9. I ran GRUB from the command line and typed 'root' and got '(fd0): Filesystem type unknown, partition type 0x0' as output. Why would it have the floppy as root? How can you change it?

---

### Post by eqisow on 2006-01-10
So I found how to edit the root in grub and then felt stupid because I just had a simple syntax error. Anyway, typing root (hd0,0) gives:

Error 21: Selected disk does not exist

However, I know the disk exist. My old Ubuntu install always booted from hd0,0. The disk isn't dead either; it's fully accessible from Knoppix.

Feeling a wee bit lost..

Edit: Perhaps running grub from inside Knoppix is a no no since it has the 'root' of my real install at /mnt/sda1? When I type grub at the Knoppix CLI am I running the grub on Kubuntu or Knoppix? Does it even matter? If that is the problem, how would I go about running the Kubuntu grub?

Edit again: Pressing c at the grub error screen doesn't take me to the CLI, though I thought it was supposed to.

---

### Post by eqisow on 2006-01-10
I tried deleting menu.lst from the grub directory, as I found info saying the absence of this file caused grub to boot directly to the command line. However, I received the same error still could not reach the grub CLI. I am so lost. :(

---

### Post by ubuntu27 on 2006-01-21
***bump!**

---


---
title: "Ubuntu/Mint Boot Problem"
date: 2009-05-30
forum: General Help
---

### Post by cottfcfan on 2009-05-30
I recently installed Linux Mint 7 alongside Ubuntu to give it a spin.
 I installed startup manager and set Ubuntu as the default OS.
I then stupidly set the grub timeout to 0.
 Now I can`t boot back into Mint, and as it has priority over the Ubuntu Grub Menu, nothing i do in Ubuntu changes the Grub Menu.
 Any ideas how I can boot back into Mint to change things?

---

### Post by Yellow Pasque on 2009-05-30
Use a livecd?

---

### Post by cottfcfan on 2009-05-30
If I use the Mint live cd, can i open a Terminal and amend the grub Menu as Normal or do i have to run any commands 1st?

---

### Post by combatwombat_nz on 2009-05-30
Mount the harddisk when running the live cd, then use the following method:

gksu gedit /media/sda1/boot/grub/menu.lst

That will get you a superuser text editor to control the meu.lst file, which has the timeout value set in it.

Make the changes, save. Unmount the harddisk. Restart pc.

PS: /media/sda1 may not be exact for your situation, it could be something else.

---

### Post by cottfcfan on 2009-05-30
Thanx combat,

I`ll try that later.

---

### Post by pastalavista on 2009-05-30
Grub should still be in your Ubuntu file system unless you specifically chose to install it in Mint. So just edit it as usual ```
gksu gedit /boot/grub/menu.lst
``` If Mint isn't listed, that means you changed the boot drive. You can edit it while in Ubuntu, no live CD necessary... if it's on the Mint drive, just edit it there. Add the file path before /boot/grub. To find which drive it's on, ```
sudo fdisk -l
``` and look for the drive with the boot * asterisk.

---

### Post by cottfcfan on 2009-05-30
Thanx pastalavista,

I must have changed the boot file because its not listed in Ubuntu, so i`ll try your suggestion 1st, and if that fails, go down the live cd root.

---

### Post by cottfcfan on 2009-06-01
SOLVED - Thanx guys,
Used the live CD mounted the drive and edited the boot file thru the terminal. Easy when u know how.

---

### Post by seydou on 2009-06-01
> **cottfcfan said:**
> SOLVED - Thanx guys,
Used the live CD mounted the drive and edited the boot file thru the terminal. Easy when u know how.

Small piece of advice - if you play like that often, consider creating bootable CD with just grub on it, so you might use that and boot from grub command line anything you want. This is faster than booting live cd.

This is the short howto:

[http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html)

---


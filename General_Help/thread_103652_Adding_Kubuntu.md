---
title: "Adding Kubuntu"
date: 2005-12-14
forum: General Help
---

### Post by canadianwriterman on 2005-12-14
I'm currently dual-booting with Windows XP on hda and Ubuntu on hdb. My current Ubuntu install is perfect and working smoothly.

I was thinking of keeping Ubuntu as is, but trying Kubuntu and upgrading it to Dapper to play with.

Can I install Kubuntu on hdb, sharing the drive with Ubuntu? Will GRUB rewrite to allow me the three boot options: WinXP/Ubuntu/Kubuntu?

---

### Post by NotJustANewbie on 2005-12-14
You should just be able to write:
```
sudo apt-get install kubuntu-desktop
```

and reboot into Ubuntu. Then at GDM, instead of Gnome, choose KDE in the session chooser (at bottom of GDM).

Hope it works.

---

### Post by tjabri on 2005-12-14
If you install Kubuntu on hdb and during install allow it to install GRUB to hda's master boot record, it will update the grub menu list to reflect all currently installed OS's on your drives. So you will have the choice you want. 

Only down side is that since you're installing an experimental OS and running /boot on that experimental OS's partition, if something happens and you loose your grub menu list on hdb's /boot folder, then you're SOL. 

The safest thing to do is decline installing grub during install and manually update your current /boot/grub/menu.lst with the new entries for Kubuntu.

However, having tested Dapper, it seems fairly safe to just let it install grub for you and do the work. If you have any problems, you can always boot from a Breezy CD's rescue mode into your Breezy partition and do install-grub to fix the problem.

---

### Post by tit4tat on 2005-12-14
Ok, I installed Kubuntu according to the step above. The surprise was that I got K* applications on Gnome. I din't loke it.

How do I undo everything? K* applications and all.

Thnx.

---

### Post by aysiu on 2005-12-14
[QUOTE=tit4tat]Ok, I installed Kubuntu according to the step above. The surprise was that I got K* applications on Gnome. I din't loke it.

How do I undo everything? K* applications and all.[/QUOTE] Follow the instructions in [this HowTo](http://www.ubuntuforums.org/showthread.php?t=96048)

By the way, if you want Ubuntu Breezy and Kubuntu Dapper, you can do a triple-boot. Just have one partition for Windows, one for Breezy, and one for Dapper. You can easily add the Dapper partition to the Grub menu in Breezy with some copy and paste.

---


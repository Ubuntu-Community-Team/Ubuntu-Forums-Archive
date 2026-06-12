---
title: "Dual-boot Ubuntu/XP laptop with Truecrypt &amp; dm-crypt gives Error 17"
date: 2009-02-05
forum: General Help
---

### Post by Oddity on 2009-02-05
Not sure where to put this thread so I'm sticking it here...

My setup is as follows:
sda1 - Fully encrypted XP system partition (NTFS), courtesy of Truecrypt
sda2 - /boot (only partiton on my drive that's actually unencrypted!)
sda3 - Ubuntu. Here I used dm-crypt and created 3 logical volumes: root, swap and home.
sda4 - Contains my files and documents (FAT32), entire partiton is encrypted with Truecrypt.

After installing Ubuntu and updating, I just booted into XP and had Truecrypt encrypt the XP system partition and overwriting Grub. I then booted Ubuntu from a CD, copied the TC bootloader to a file on /boot, and reinstalled Grub. I then used chainloading to get Grub to load the TC bootloader when XP is selected from the boot menu.

And no I don't actually need this kind of paranoid setup - I'm just doing it for kicks.

Anyway, I booted into XP - worked fine. Booted into Ubuntu - worked fine. But a while later I got "Error 17: Cannot mount selected partition" when trying to boot into Ubuntu. After a few if and buts, I managed to reinstall Grub and Ubuntu worked fine again... but now the error has returned.

It's sorta... inconvenient to reinstall Grub everytime I want to use Ubuntu, so can anyone please help a *stooopid* linux newbie out? Pretty please?

---

### Post by legalizemeth on 2009-03-14
> **Oddity said:**
> 
I then booted Ubuntu from a CD, copied the TC bootloader to a file on /boot, and reinstalled Grub. I then used chainloading to get Grub to load the TC bootloader when XP is selected from the boot menu.
Could you elaborate on these steps please?  I'd like to try this same setup - I have a currently unencrypted Windows partition and a dm-crypted Ubuntu setup on the same disk.  I'd like to use Truecrypt to encrypt the entire Windows partition, but keep my current dual-boot capability.  Grub has always seemed a little like black magic to me.

And sorry, I can't help with the error 17. :(

---

### Post by mrsteveman1 on 2009-03-14
To make your life easier you should probably just leave the truecrypt bootloader on the disk as the first one that loads, install grub to the /boot partition and let truecrypt find it when you hit esc to boot another partition. Things should work without a problem then.

I don't recall what error 17 is by try that first.

---


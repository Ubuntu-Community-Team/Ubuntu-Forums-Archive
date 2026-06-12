---
title: "Need help reinstalling GRUB after installing Windows OS"
date: 2009-05-20
forum: General Help
---

### Post by lgp171188 on 2009-05-20
Hi all,
I have a multiboot machine which used to run Debian Etch and Windows XP, and without saying, I often had to reinstall Windows XP after which I will have to reinstall GRUB again. I often used OpenSolaris LiveCD which has a GRUB prompt when booted. I pressed 'c' to go into the command prompt of GRUB and did a 'find /boot/grub/stage1' for which I got a partition like (hdX,Y). Then I did a 'root (hdX,Y)' and 'setup (hd0)' and GRUB would get installed.

Sometimes, I used to boot into Ubuntu live and do a 'grub-install /dev/sda' to fix it. But now with recent versions of Ubuntu (I had this issue in Intrepid and Jaunty) and Debian Lenny these well-documented procedures do not seem to work.

When I do a 'find /boot/grub/stage1' in the grub prompt, it gives a 'file not found error' and when i do a 'grub-install' command it says it can't find the '/boot/grub/stage1 and etc. etc.'. But the files are there safe in the linux partition, which I confirmed by booting into the LiveCD and mounting the partition.

How to install GRUB now? I noticed that these problems weren't there with older versions of distros. Has something changed in newer distros that I am unaware of?

Thanks in advance.

---

### Post by Legace on 2009-05-20
Are you using a EXT4 filesystem? If so, you need to use a distro Live CD that supports GRUB with EXT4 (like Jaunty).

---

### Post by lgp171188 on 2009-05-20
> **Legace said:**
> Are you using a EXT4 filesystem? If so, you need to use a distro Live CD that supports GRUB with EXT4 (like Jaunty).
No I am not using ext4. I use ext3 filesystem in my Debian Lenny and Ubuntu Intrepid installations.

---

### Post by KhurramM on 2009-05-20
U can use the recovery mode of your installation CD

OR

try super grub disk

It will hopefully do what u require here.

Hope this helps u

---


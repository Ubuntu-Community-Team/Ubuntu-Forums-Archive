---
title: "Grub cannot find /dev/sdc6"
date: 2022-06-20
forum: Desktop Environments
---

### Post by Geoff_Lane on 2022-06-20
After a bit of a disaster with my main operating system was trying to manually boot an old system to get back to an Ubuntu Desktop.

Now I am generally OK with booting manually from grub command prompt but problem today, after using ls to find the correct partition for /boot I then set root.  gave the linux kernal location followed by root/dev/sdc6

Gave the initrd location then boot, all looked promising but then got message timed out waiting for /root as it couldn't find /dev/sdc6

Now the initial ls shows hd2,msdos6 so have I missed entering an important insmod as there is no sd* listing in ther /dev directory.

Geoff

---

### Post by oldfred on 2022-06-20
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO which may not be as current.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)   &           
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Geoff_Lane on 2022-06-22
Thanks for reply, was unable to get Bootinfo summary report as I was having all sorts of problems.  My old system was legacy boot and not UEFI, I eventually used Super Grub2 installed on a USB key to boot this disk.

Oddly, I had used this disk the day before and shut down normally, following day got Grub Rescue> prompt.   Super Grub2 managed to boot it, did an update-grub, seemed to find everything OK, rebooted and Grub Rescue> [B]again.
[/B]
Installed GRUB using grub-install (or maybe install-grub) and now all working fine, no idea how I lost it initially.

Geoff

---


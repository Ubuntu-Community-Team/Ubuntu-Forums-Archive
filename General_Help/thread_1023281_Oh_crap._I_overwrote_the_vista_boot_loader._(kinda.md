---
title: "Oh crap. I overwrote the vista boot loader. (kinda)"
date: 2008-12-27
forum: General Help
---

### Post by Andy218 on 2008-12-27
Well there you have it. I overwrote the vista boot loader... kinda. 

I installed Hardy to a thumbdrive via the install feature. (it showed up as an HDD.) Then i try to boot vista and it says grub bootloader... ERROR 25.

Then i'm like Ohhhh ****! But then iu pluged the thumbdrive in, grub loaded, and i booted to vista!!!!!! :):):):):)

So, grub is like installed partialy on the two drives?

I am really screwed up here.

I need to like reinstall the vista boot loader while still being able to boot to linux!

---

### Post by caljohnsmith on 2008-12-27
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---

### Post by midnightfox2 on 2008-12-28
Supergrub disk will restore windows bootloader.

I think you just made the same mistake as I did some time ago.
You installed grub to your first hard drive and ubuntu to your flash drive.
The menu.lst is on the flash drive, that's why it freaks out when you startup without the flash drive.

---

### Post by Sef on 2008-12-28
> Supergrub disk will restore windows bootloader.
[URL="http://supergrubdisk.org"]
Super GRUB Disk link[/URL].

---


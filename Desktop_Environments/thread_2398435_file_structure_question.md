---
title: "file structure question"
date: 2018-08-12
forum: Desktop Environments
---

### Post by Lloydb39 on 2018-08-12
I have an old Dell laptop I was running Elementary OS on, and it worked well but crashed. Took out the drive and hooked it up to another one running Xubuntu to see if I could recover files. It mounted and showed "efi" and "grub" folders and a bunch of vmilinux files but I could find "home" or any documents anywhere. What did I do wrong?

---

### Post by TheFu on 2018-08-12
If you'll post the partition table and any LVM things, perhaps we could help.
grub and efi are there to boot.
vmlinux is the kernel that gets booted, normally it is in /boot/

```
fdisk -l
```
and/or 
```
lsblk
```
output would be helpful.  Use *code tags*, like I have, so the output is readable and lines up.

---

### Post by Lloydb39 on 2018-08-13
Different problem now. I went ahead and formatted the old disk drive. Now it won't mount in Ubuntu and won't show in Windows File Explorer. I used the file format for "all machines" that was in the disk manager. I think I used Gpartition.

---

### Post by deadflowr on 2018-08-13
You mean you used this (or saw this window when formatting the disk:
[ATTACH=CONFIG]280720[/ATTACH]
If so, that's gnome-disks, perhaps this might give you hope:
[https://ubuntu-mate.community/t/disks-utility-formatting-problem-what-tool-to-use-when-formatting-a-usb-drive/5772/2]("https://ubuntu-mate.community/t/disks-utility-formatting-problem-what-tool-to-use-when-formatting-a-usb-drive/5772/2")

---


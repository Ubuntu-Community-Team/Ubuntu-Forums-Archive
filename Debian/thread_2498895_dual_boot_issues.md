---
title: "dual boot issues"
date: 2024-07-02
forum: Debian
---

### Post by darklight0093 on 2024-07-02
[FONT=Arial]hello I am a user of the think pad t440. I wanted to dual boot Debian and windows but after installing it it doesn't show up in my bios or windows ms config. I have tried setting bootmgr in bcdedit but It still doesn't work. I hope that you can help resolve this[/FONT][FONT=Arial]The link to the pastebin is [/FONT]
[FONT=Arial][https://paste.ubuntu.com/p/GmjpCpmM5x/](https://paste.ubuntu.com/p/GmjpCpmM5x/)[/FONT]

---

### Post by oldfred on 2024-07-02
You have UEFI installs of Windows & Debian.
You also have multiple older UEFI boot entries, ubuntu & refind.
And Lenovo shows many of its entries in UEFI. Lines starting at #30 in report.

Does Debian entry in UEFI menu work when you select it? Often f12 but Lenovo does not always use f12 for UEFI one time boot menu.
Does Windows boot from UEFI boot menu?
Does Windows boot from grub menu?

Is UEFI set to boot in UEFI boot mode?
Some Lenovo's have this:
The Device Guard BIOS setting locks down the boot order to internal HDD/SSD only.
You may need to change a setting in UEFI.

Lenovo T450 Problem with boot repair GRUB - Boot Lock issue
[https://ubuntuforums.org/showthread.php?t=2494747](https://ubuntuforums.org/showthread.php?t=2494747)
Lenovo Locked UEFI/BIOS setting:
[https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg](https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg)

Older, but shows UEFI screens:
[https://tothepoles.co.uk/2017/11/16/lenovo-t470p-ubuntu-16-04-install-notes/](https://tothepoles.co.uk/2017/11/16/lenovo-t470p-ubuntu-16-04-install-notes/)

---

### Post by coffeecat on 2024-07-02
*Thread moved to **Debian** sub-forum.*

---


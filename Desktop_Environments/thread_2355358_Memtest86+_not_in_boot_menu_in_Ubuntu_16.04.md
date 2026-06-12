---
title: "Memtest86+ not in boot menu in Ubuntu 16.04"
date: 2017-03-12
forum: Desktop Environments
---

### Post by deepakdeshp on 2017-03-12
Hello,
I had the required files for memtest86+ but did not get the grub menu option for memtest86 in Ubuntu 16.04.
I also executed ```
  sudo apt-get install memtest86+ 
``` which indicated that the package is already installed.
How do I get to execute memtest during boot time?

Thank you in anticipation

---

### Post by sudodus on 2017-03-12
memtest86+ is a 16-bit program. It works in BIOS mode, but not in UEFI mode. I would guess that you boot in UEFI mode, and then you will not have the option to run it.

If you boot your computer in BIOS mode from an Ubuntu DVD or USB drive made from the Ubuntu iso file, you will have the option to run memtest86+ in the syslinux boot menu.

Press a key, when you see the two small icons at the bottom of the screen, and you will arrive at a menu, where you can select the line

**Test memory**

with the arrow keys and then press the Enter key.

---

### Post by deepakdeshp on 2017-03-20
Thank you for your detailed answer. I tried to go to the BIOS mode, but unsuccessful.In nBIOS there are many options I changed a coupls of them but still wasnt able to find the memtest option.

---

### Post by sudodus on 2017-03-20
Did you try to boot from a live system (in a DVD disk or USB pendrive) created from an Ubuntu desktop iso file?

If your computer does not boot in BIOS mode, you will not be able to boot the open source memtest86+ program. But memtest has also developed into commercial program, that works in UEFI mode. There is a free version (as in free beer) but the source code is not open.

See this link, [http://www.memtest86.com/](http://www.memtest86.com/)

---


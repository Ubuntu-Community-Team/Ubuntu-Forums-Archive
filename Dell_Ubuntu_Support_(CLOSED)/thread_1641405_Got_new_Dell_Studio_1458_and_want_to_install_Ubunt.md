---
title: "Got new Dell Studio 1458 and want to install Ubuntu 10.10"
date: 2010-12-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by paragkalra on 2010-12-09
Hi,

I believe this might be the most common question now but still.

I have just got Dell Studio 1458 and with Windoze 7 pre-installed.

Its just 4 hours old and still I want to start with Ubuntu 10.10 (its not that I have Windoze but I love Ubuntu more)

But I want to have Ubuntu dual boot with Windoze 7. 

Since my Windoze 7 came with 1 C drive and one hidden recovery drive (which I can see only under disk management), please let me know the best and safest way to keep Ubuntu 10.10 dual boot with my original (and legal) Windoze 7

By the way I have received some drivers and utilities DVD with the laptop.

---

### Post by fjgaude on 2010-12-09
As I recall, Windows comes with a utility that lets you change the size of partitions. Look into the menu called something like Computer Management and there is a disk utility. With it change the size of the Windows partition, making it half the size it presently is. Something like that. Then...

Exit, put the install CD for 10.10 in the DVD reader and install. You will have the option of picking what partition you wish to use. Use the one that is empty.

After that reboot and you will see the grub startup screen that permits you to select either Windows or Ubuntu.

You could instead just let Ubuntu decide to install the OS side-by-side with Windows. Start the install and carefully read the options as you go.

Let us know if all goes as planned. If not, check back with us.

---

### Post by cnbiz850 on 2010-12-12
In the middle of Ubuntu install process (before you select partition), it allows you to resize/create partitions without demaging Windows files.

---


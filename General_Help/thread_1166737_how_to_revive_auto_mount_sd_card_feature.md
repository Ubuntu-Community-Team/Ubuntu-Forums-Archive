---
title: "how to revive auto mount sd card feature"
date: 2009-05-22
forum: General Help
---

### Post by gnulab on 2009-05-22
Hi,

I've uninstalled the program Mirage, managed to get my sound working, add swap partition, tried installing usb gsm modem. After that, my SD card won't auto-mount anymore like before. Not only my SD card, but NTFS formatted partitions aren't visible from the default file manager.

Checked thru the partition editor, it said that the NTFS formatted partitions are not mounted. Couldn't mount it either, the option is greyed out.

I would like to be able to browse my SD card & ntfs partition without having to go to the terminal and mount those partitions manually, how do I do it?

Please advise.

Henry

---

### Post by gnulab on 2009-05-22
UPDATE: apparently, it's the UUID that's causing havoc.
Could someone care to enlighten why introducing a UUID (Universally Unique Identifier) wreck the auto mount feature of ubuntu 9.04?

-------------------------------------------------------------
I've managed to find out what's causing it.

I made the following entry in the /etc/fstab
#UUID=5980e450-0c5e-443b-b558-2aaa23d3ed4f
#/dev/sda6    none        swap    sw        0    0

I commented that out, and everything is back to normal.

I followed the steps outlined here
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
Except that I added UUID, will try if commenting out UUID will make any difference.

But for now, I'm happy.

Henry

---


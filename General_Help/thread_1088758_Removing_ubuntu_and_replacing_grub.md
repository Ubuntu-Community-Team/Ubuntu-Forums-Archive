---
title: "Removing ubuntu and replacing grub?"
date: 2009-03-06
forum: General Help
---

### Post by khr on 2009-03-06
I was quite happy with Gutsy and Hardy, so I installed Ubuntu 8.10 on this laptop to be dual-booted with Vista.

I have 3 partitions. The first one having the Vista operating system, the second being formatted as NTFS and the last one was for Ubuntu 8.10. After I installed Ubuntu, I configured GRUB so I could boot up Windows Vista too. Now I'm planning to reformat the third partition as NTFS, as I need the space for some games. :P
But if I reformat the third partition, won't that delete GRUB too? How do I go back to using the "vista bootloader"?

---

### Post by azzamite on 2009-03-06
I hope you get an answer for this, I've been wondering the same for quite some time now.

As for a hint, there's a command in Windows that allows you to repair the boot sector of your windows machine, replacing grub. Unfortunately I could not find it.

---

### Post by namegame on 2009-03-06
If it were me, I would boot into Vista and download a program called "EasyBCD" Link: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

It is a program that makes editing Vista's bootloader rather simple. It supports multiple Operating Systems, including Linux and other versions of Windows.

I've used it many times before and it has never failed me.

---


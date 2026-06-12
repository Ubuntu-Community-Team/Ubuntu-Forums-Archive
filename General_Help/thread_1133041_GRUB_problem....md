---
title: "GRUB problem..."
date: 2009-04-22
forum: General Help
---

### Post by ansabhailte on 2009-04-22
I have a 4GB PNY Attache flash drive. I have it partitioned into 3 FAT32 partitions. the second has ubuntu (from the 8.10 live usb installer) and the third has backtrack 4 (live via unetbootin). i installed grub onto the first partition, and then configured it for my settings. however, when i boot into backtrack, it says "init: illegal runlevel (null)" and wont go any further. what is going on? how can i fix this? sorry for posting this here but i figured its a grub question. my backtrack section in my menu.lst reads as follows:

title		Backtrack
root            (hd0,2)
kernel          /boot/vmlinuz root=UUID=49EF-5D74 ro quiet
initrd          /boot/initrd.gz
boot

---


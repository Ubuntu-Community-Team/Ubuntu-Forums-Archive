---
title: "Error 13: Invalid or unsupported executable type"
date: 2008-12-31
forum: General Help
---

### Post by kaoskorruption on 2008-12-31
I had Ubuntu on my laptop for awhile, and now I decided I needed to put Windows Vista on as a dual boot. I resized my Ubuntu ext3 partition, created a new ntfs partition for windows, and made the ntfs partition the boot partition. I then installed windows just fine. After that I put ubuntu back as the boot partition so that I could use grub. When I try to start windows from grub, I get the error "Error 13: Invalid or unsupported executable type." 

This is the section in my menu.list:
```
title		Windows Vista
rootnoverify	(hd0,2)
makeactive
chainloader +1
```

Here is my harddrive geometry:
```
geometry (hd0)
drive 0x80: C/H/S = 30401/255/63, The number of sectors = 488397168, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x82
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 2,  Filesystem type unknown, partition type 0x7

```

Anybody know how to fix this?

Thanks!

---

### Post by caljohnsmith on 2008-12-31
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---


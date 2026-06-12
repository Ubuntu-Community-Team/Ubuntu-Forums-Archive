---
title: "deleted initrd.img and vmlinux"
date: 2009-02-16
forum: General Help
---

### Post by sailingboarder on 2009-02-16
So I had a dual boot system, with ubuntu 8.10 and windows xp
I found myself facing an audio/video project, so I decided to install ubuntustudio 8.04_64 as well.
I had a separate /boot partition, which I reformatted when installing studio, thus deleting my regular ubuntu images. I feel that if I just download the appropriate files and place them in /boot, i can configure grub to load my regular os correctly
does anyone know where i can download the kernel images that i need?

---

### Post by cariboo on 2009-02-16
You may be able to get away with reinstalling the kernel you were using to restore the files you deleted eg:

```
sudo apt-get reinstall linux-image-2.6.xx-generic
```

where 2.6.xx is the kernel version you where using.

Jim

---


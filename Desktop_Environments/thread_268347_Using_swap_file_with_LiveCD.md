---
title: "Using swap file with LiveCD"
date: 2006-09-30
forum: Desktop Environments
---

### Post by jreyes on 2006-09-30
It is possible use a file in a FAT32 partition as a swap file with the LiveCD (not a hard drive install)? If so, which steps are needed to do it? This is my first time using a Linux distro, by the way.

---

### Post by BoneKracker on 2006-09-30
I don't believe so.

I've had two Linux installations share swap space, and I've heard of sharing BSD swap space with Linux, but I haven't heard of using Windows/DOS partitions for Linux swap.

---

### Post by jreyes on 2006-09-30
Ok, well thanks anyway

---

### Post by lha on 2006-09-30
Mount that fat32 partition somewhere (eg. /mnt/myfat), create a swap file in it (dd if=/dev/zero of=/mnt/myfat/swapfile bs=1024 count=65536) and create a swap file system in the file (mkswap /mnt/myfat/swapfile). Finally, activate your new swap file (swapon /mnt/myfat/swapfile). If you want more than 64 MB of swap space, change the number in "count=65536" to something bigger.

---

### Post by jreyes on 2006-09-30
Ok, let me give a try

---

### Post by BoneKracker on 2006-10-01
Well, there we go.  That's what I like about Linux.  I learn something new every day.  Sorry.

---


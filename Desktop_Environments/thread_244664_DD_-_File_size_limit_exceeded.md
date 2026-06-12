---
title: "DD - File size limit exceeded"
date: 2006-08-26
forum: Desktop Environments
---

### Post by cmiller on 2006-08-26
I'm trying to use dd to make an image of a dvd, but am getting File size limit exceeded error when I hit 4gbs. I am writing the file to a ext3 external hard drive. I used mke2fs -j -O dir_index /dev/sda to format the drive. Any ideas how I can fix this?

---

### Post by cmiller on 2006-08-26
I tried the same operation with sudo, but the same result... :confused:

---

### Post by cmiller on 2006-08-26
The problem doesn't seem to be ulimit.

chris@chris-laptop:~$ ulimit
unlimited

---


---
title: "Problem compiling all programs"
date: 2006-07-13
forum: Desktop Environments
---

### Post by h-kan on 2006-07-13
When ever I try compile something I get an error message after a while that looks like this:

:~/Downloads/aircrack-ng-0.6$ make
gcc -g -W -Wall -O3 -D_FILE_OFFSET_BITS=64 src/aircrack-ng.c src/crypto.c src/sha1-mmx.S src/common.c -o aircrack-ng -lpthread
In file included from src/aircrack-ng.c:33:
/usr/include/unistd.h:530:27: /usr/include/bits/confname.h: Input/output error
In file included from src/common.c:6:
/usr/include/unistd.h:530:27: /usr/include/bits/confname.h: Input/output error
make: *** [aircrack-ng] Error 1
:~/Downloads/aircrack-ng-0.6$

This error message shows no matter what program im compiling!

---

### Post by philippe_carlo on 2006-07-13
Seems like there are troubles reading your FS. Maybe you should make sure your filesystem is not corrupt by running fsck. Also make sure your partitions are not full.

---

### Post by h-kan on 2006-07-13
I have only used 37% of the disk and no error when running fsck.
And no problem whith precompiled stuff, it's just when im compiling manualy.

---


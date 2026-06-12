---
title: "Misterious directory disapearance"
date: 2006-01-06
forum: Desktop Environments
---

### Post by skyhorse on 2006-01-06
Hi,

A directory just vanished before my eyes...

I moved it to ".." and it just disappeared!

Here's my log:
```

skyhorse@skybuntu:~/.cvscedega/drive_c$ l
total 24
drwxr--r--   6 skyhorse skyhorse 4096 2006-01-07 00:29 .
drwxr--r--   3 skyhorse skyhorse 4096 2006-01-07 00:29 Program Files
drwxr-xr-x   2 skyhorse skyhorse 4096 2006-01-07 00:27 Guild Wars
lrwxrwxrwx   1 skyhorse skyhorse    7 2006-01-07 00:27 WINDOWS -> windows
drwxr--r--  11 skyhorse skyhorse 4096 2006-01-07 00:26 windows
drwxr--r--   4 skyhorse skyhorse 4096 2006-01-06 20:34 ..
drwxr--r--   5 skyhorse skyhorse 4096 2005-11-02 19:12 My Documents
skyhorse@skybuntu:~/.cvscedega/drive_c$ mv Guild\ Wars/ ../old_drive_c/Program\ Files
mv: cannot move `Guild Wars/' to `../old_drive_c/Program Files': No such file or directory
skyhorse@skybuntu:~/.cvscedega/drive_c$ mv Guild\ Wars/ ..
skyhorse@skybuntu:~/.cvscedega/drive_c$ l
total 20
drwxr--r--   5 skyhorse skyhorse 4096 2006-01-07 00:29 .
drwxr--r--   5 skyhorse skyhorse 4096 2006-01-07 00:29 ..
drwxr--r--   3 skyhorse skyhorse 4096 2006-01-07 00:29 Program Files
lrwxrwxrwx   1 skyhorse skyhorse    7 2006-01-07 00:27 WINDOWS -> windows
drwxr--r--  11 skyhorse skyhorse 4096 2006-01-07 00:26 windows
drwxr--r--   5 skyhorse skyhorse 4096 2005-11-02 19:12 My Documents
skyhorse@skybuntu:~/.cvscedega/drive_c$ cd ..
skyhorse@skybuntu:~/.cvscedega$ l
total 172
drwxr-xr-x   4 skyhorse skyhorse  4096 2006-01-07 00:27 .
-rw-r--r--   1 skyhorse skyhorse  1351 2006-01-07 00:27 system.reg
-rw-r--r--   1 skyhorse skyhorse    80 2006-01-07 00:27 userdef.reg
-rw-r--r--   1 skyhorse skyhorse   354 2006-01-07 00:27 user.reg
drwx------   2 skyhorse skyhorse  4096 2006-01-07 00:27 wineserver-skybuntu
-rw-r--r--   1 skyhorse skyhorse 90581 2006-01-07 00:27 ftfontcache
-rw-r--r--   1 skyhorse skyhorse 13613 2006-01-07 00:26 cachedmetrics.:0.0
lrwxrwxrwx   1 skyhorse skyhorse    28 2006-01-07 00:24 drive_c -> /home/skyhorse/.wine/drive_c
-rw-r--r--   1 skyhorse skyhorse 11136 2006-01-07 00:23 config
-rw-r--r--   1 skyhorse skyhorse 11136 2006-01-07 00:22 config~
drwxr-xr-x  72 skyhorse skyhorse  4096 2006-01-07 00:21 ..
drwxr-xr-x   5 skyhorse skyhorse  4096 2006-01-07 00:21 old_drive_c
-rw-r--r--   1 skyhorse skyhorse    33 2006-01-07 00:21 oldreg.md5
-rw-r--r--   1 skyhorse skyhorse    22 2006-01-07 00:21 reglog

```

"Guild Wars" just vanished...

Interestingly enough, "df" reports 

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2             24351384  18450676   4663704  80% /home


but my "System Monitor" in gnome reports 5.6Gb free (75% Use). The difference is about right for guild wars directory.

This partition is of type ext3

/dev/hda2 on /home type ext3 (rw)

I am running:

Linux skybuntu 2.6.12-9-686 #1 Mon Oct 10 13:25:32 BST 2005 i686 GNU/Linux


Any ideas?

---

### Post by skyhorse on 2006-01-06
*doh*

This is what happens when you try to do anything when half-asleep...

nevermind, mistery solved...

ta,

sky

---


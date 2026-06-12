---
title: "Nautulis tweaks"
date: 2008-11-07
forum: Desktop Environments
---

### Post by cheics on 2008-11-07
(ubuntu 8.10)

I recently discovered the great **mhddfs**; a phenomenal way for us pack rats to accumulate a bunch of drives together at a high level. 

(check it out here [http://debaday.debian.net/2008/05/25/mhddfs-join-several-real-filesystems-together-to-form-a-single-larger-one/]("http://debaday.debian.net/2008/05/25/mhddfs-join-several-real-filesystems-together-to-form-a-single-larger-one/"))



I am having issues in making it look pretty though...

(in blue) After having used mhddfs to 'combine' my 1TB (972GB) and 500GB drives together into 'HEAP', I would like to have the 1TB and 500GB entries disappear from nautulis while still being able to use HEAP.
mhddfs uses fuse to create a VFS; in this case HEAP, from any two folders; in this case /dev/sda3 and /dev/sdb5 or something. I can't mount devices with mhddfs so I cannot umount the drives.


In my attached screen shot circled in red; due to the theme I am using I have some ugly unmount arrows for all of my drives. I would like to only have the unmount arrow for my CD-ROM drive, or failing that, none at all and use terminal or right-click to unmount.



I looked through most the keys using gconf-editor in apps/nautulis and did not find an appropriate tweak



Thanks in advance to the guru who answers this w/o RTFM!... cause I did and had no luck :(

---

### Post by cheics on 2008-11-16
...not sure of the correct protocol in ubuntu forums for this... prehaps a repost is in order but

*Bump*

---


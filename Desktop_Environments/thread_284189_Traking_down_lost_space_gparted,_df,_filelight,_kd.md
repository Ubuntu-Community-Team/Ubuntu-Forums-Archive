---
title: "Traking down lost space: gparted, df, filelight, kdirstat all disagree"
date: 2006-10-25
forum: Desktop Environments
---

### Post by tigerstripedcat on 2006-10-25
I seem to be missing some space on my hard drive, or I'm not understanding the reporting correctly:

* "df" shows:
jmorris@faye:/$ df /dev/hda2
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2             11535376  10447112    502296  96% /

* gparted shows:
Partition     filesystem    mountpoint  size     used      unused
/dev/hda2      ext3         /          11.18Gib  10.14Gib 1.04Gib

* filelight shows
7.0Gib total for / with 

* kdirstat shows 
7.13GB for /

Why does the total size of these methods disagree?  I did have some journal corruption that I fixed with e2fsck, so maybe it's something to do with that.  Or maybe these kde apps don't read something very important.  This is sort of important to me, because I'm running out of space and I'd like to make sense of a 4bg difference.

Thank you so much for your help.
TSC

---

### Post by tigerstripedcat on 2006-10-25
anyone?

---


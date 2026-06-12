---
title: "Problems downloading full repositories to make a dvd for ubuntu"
date: 2006-01-10
forum: General Help
---

### Post by Pezque on 2006-01-10
Hi all, I´m trying to download all ubuntu repositories to make a dvd for home and I´m not able to complete the download. Last time at 62 % it stopped. The command I use is:

$debmirror --nosource -m --passive --host=archive.ubuntulinux.org --root=ubuntu/ --method=ftp --progress --dist=breezy --section=main,multiverse,universe --arch=i386 ubuntu/ --ignore-release-gpg

If I wanna resume (I´m no sure I can) the error is: releasing 1 pending lock... at /usr/lib/perl5/LockFile/Simple.pm line 182.
How could I resume? Is it possible or I may download at the begining?

Thanks all for your continuos help!!
MIGUEL

---

### Post by dragonfyre13 on 2006-01-10
You  might also want to try it in synaptic. If you select everything you want to download, you can select the "download files only" check box. Make sure to clear the cache, and make sure you can fit it all on a DVD. Last time I checked, you couldn't even fit all of main on a DVD, and universe is massively bigger than that.

---

### Post by bagel on 2006-01-10
Isn't there a Ubuntu DVD to download? Maybe not complete, but it should contain a nice collection anyway. (-;

Ciao, bagel

---

### Post by eddiewalker on 2006-01-11
From ubuntulinux.org:  "The archive is currently about 110 GB"

Try the DVD releases section at the bottom of this link:  [http://www.ubuntulinux.org/download](http://www.ubuntulinux.org/download)

---


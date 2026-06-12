---
title: "New HDD - XFS yes or no?"
date: 2009-02-05
forum: General Help
---

### Post by c-shadow on 2009-02-05
I bought a new 640 GB HDD and need some advice about FS...
The drive would be in one partition intended for storage of media files (music, video) and torrent downloads. Mostly larger files, but sometimes i dl a torrent of 7GB with 16k files in it (ebooks) :-)
I have 2x320 GB SATA drives on ext3 and don't like he performance - slow deletion of files, preallocation in azureus takes quite some time (even with noatime mount option and dir_index). It tends to fragment too with some other torrent clients that don't play nicely with preallocation,...
So i thought about giving XFS a try, any suggestions about this FS, formatting, mount options?
Or is there some other FS more suitable than XFS?
I read about XFS but have no experience with it.
Thx

---

### Post by hyper_ch on 2009-02-06
XFS is good for larger files. I think that would be a good use of it. However if you are not really sure what to do, stick with ext3 :)

---

### Post by thechris on 2009-02-13
XFS is typically my FS of choice.  however, I've notice severe problems with amd64 and XFS in some kernel versions.  of note, 2.6.27 seems to hate it.  I was able to brick a fresh 8.10 install with "apt-get upgrade".

For 32bit, i've used XFS (with gentoo) for years.  mainly because, for years, ubuntu has not allowed / on xfs.  really, most 64b installs have worked with XFS as well.  even despite gentoo's "you will die" warnings for xfs, it has worked well.

JFS is another interesting choice, but error -22 kept me away from it.  some odd file names would cause errors (typically non-US characters).

---

### Post by Sorivenul on 2009-02-13
For large-file storage, XFS is hard to beat. If it gives you a headache stick with ext3.

I personally use JFS for my storage, but I don't deal with massive amounts of large files.

---

### Post by c-shadow on 2009-02-13
Ok, I went with XFS and it works great for storage. / and /home are stil on good old ext3. Vuze preallocates 20 GB of continuous data in about one second, that's hard to beat. Deletes the same amount of data in a heartbeat too. :-)

---


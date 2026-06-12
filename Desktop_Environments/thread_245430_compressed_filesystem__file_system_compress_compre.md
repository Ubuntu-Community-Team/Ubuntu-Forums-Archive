---
title: "compressed filesystem / file system compress compression"
date: 2006-08-27
forum: Desktop Environments
---

### Post by syadnom on 2006-08-27
i have been searching all over to find a way to have a writable compressed filesystem in ubuntu/linux

ideally i would function like so

mount -o loop image.tar.gz /mount/point/

i would prefer to compress the image in one of the following formats
tar.gz
tar.bz2
rar
zip/Z

this image MUST be writable so the squashfs technique wont work for me :(

squashfs is exactly what i want but writable...
with squashfs i can take 1 CD worth of data and put that into the squashfs image, then mount and access the data.  the only differect is that i need to be able to write to the image also.

any help would be much appreciated

---

### Post by lance bermudez on 2007-06-09
i would like to have a compressed root file system. So that i can fix ubuntu on a 545mb hard drive with gui and printer. that is all that is needed. i know i could use some other linux but the person it is for only likes ubuntu linux so that will not be possible also they only know a little linux that is another reason why they like ubuntu.

---

### Post by Impaque on 2008-02-02
There nothing like that on Linux, nothing stable at least. Go ZFS on FreeBSD?

---

### Post by Impaque on 2008-02-02
Compression example video:

[http://people.freebsd.org/~pjd/misc/zfs/zfs_compression.swf](http://people.freebsd.org/~pjd/misc/zfs/zfs_compression.swf)

---

### Post by Masoris on 2008-05-29
I'm also waiting this. It seems very nice for my temporary torrent folder. I want to save my disk space.

---

### Post by Masoris on 2008-06-18
[http://code.google.com/p/fuse-zip/](http://code.google.com/p/fuse-zip/)

I found one. It names 'fuse-zip', but I not sure is it stable enough to use.

---

### Post by diaa on 2008-07-06
Recently I found 2 read/write compressed filesystems for Linux, one is [compFUSEd]("http://www.biggerbytes.be") and the other is [fusecompress]("http://miio.net/fusecompress/")
the following article explains how to setup and use compFUSEd:
[Save disk space - use compFUSEd to transparently compress filesystems]("http://www.linux.com/feature/137234")

Another interesting link that I just found:
[All compressed filesystems based on FUSE]("http://fuse.sourceforge.net/wiki/index.php/CompressedFileSystems")

---


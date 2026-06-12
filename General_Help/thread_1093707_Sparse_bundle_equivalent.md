---
title: "Sparse bundle equivalent"
date: 2009-03-11
forum: General Help
---

### Post by bernardd on 2009-03-11
Is there a linux equivalent to the Apple Sparse Bundle disk image format?

The attractive features of the sparse bundle format are:

1) Reduced size
The sparse bundle disk image only takes up roughly as much space as the files it contains. This helps a lot for any remote backups.

2) Segmented content
The disk image is actually a container for smaller segments (8MB files).

3) Supports strong encryption
AES 128 and 256 can be used to encrypt the segments (not the whole disk image).

These three features allow very efficient incremental backups of encrypted disk images. If a handful of files changed on the disk image, only the segment that contain them need to be backed up. On other disk image formats, the whole monolithic file containing everything needs to be backed up each time.

Unfortunately, Sparse Bundle don't seem to be documented by Apple. The most I could find is here [http://developer.apple.com/documentation/Darwin/Reference/ManPages/man1/hdiutil.1.html](http://developer.apple.com/documentation/Darwin/Reference/ManPages/man1/hdiutil.1.html)

Has anyone found something similar under Linux?
Thanks
Bernard

---

### Post by Zerocool3001 on 2009-05-23
Sparse images and sparse bundles are quite awesome. Unfortunately Linux doesn't quite have anything that comes close to them. Your best bet might be try a [FUSE]("http://apps.sourceforge.net/mediawiki/fuse/index.php?title=Main_Page") filesystem. There are [versioned file systems]("http://apps.sourceforge.net/mediawiki/fuse/index.php?title=VersioningFileSystems") that act quite like Time Machine. I'd also be willing to bet that there are sparse file systems that store information in small blocks for each copying/update.

If you decide you like any of the filesystems, you can use it across both your Macs and Linux machines FUSE in built into most Linux variants and [MacFUSE]("http://apps.sourceforge.net/mediawiki/fuse/index.php?title=Main_Page") is available for Macs.

If you have trouble finding anything send me a PM and I'd be happy to help.

---


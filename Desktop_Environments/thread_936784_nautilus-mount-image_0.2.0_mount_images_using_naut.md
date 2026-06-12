---
title: "nautilus-mount-image 0.2.0: mount images using nautilus' contextual menu"
date: 2008-10-03
forum: Desktop Environments
---

### Post by calvin.ngei on 2008-10-03
This package adds an entry to Nautilus' contextual menu to mount or unmount selected image file. Image file can be in iso9660/udf format, or NTFS, VFAT, XFS, ReiserFS, Reiser4, JFS, EXT2, EXT3, EXT4, Minix, HFS, HFS+, and nero image. I modified version 0.1.1 which can only mount/unmount iso file and released this new version. Enjoy.:guitar:

ATTENTION:
1. After installation logout and relogin is needed.
2. To unmount a mounted image file, just right click the image file that had been mounted, choose "umount" and that will be ok, the mount point will be deleted automatically, and the loop device associated with the image file will be freed. Right click desktop icon and choose "umount" will fail.

The attachment is a tar.bz2 package containing a deb file and an rpm file.

---


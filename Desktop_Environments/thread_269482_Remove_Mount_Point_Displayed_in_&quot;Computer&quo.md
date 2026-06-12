---
title: "Remove Mount Point Displayed in &quot;Computer&quot;"
date: 2006-10-01
forum: Desktop Environments
---

### Post by yishai on 2006-10-01
I recently followed the instructions provided by the "Unofficial Ubuntu 6.06 (Dapper Drake) Linux Starter Guide" ([http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)) to "...mount Windows partitions (NTFS) on boot-up, and allow users read and write access" (section 16.5). I wanted read/write access to an NTFS partition where I store my basic files.

This partition is mounted at location '/files', and this is reflected in /etc/fstab and /etc/mtab.

Having completed the instructions in section 16.5 however, I found that there was now an icon/link to this partition in my "Computer" folder, and yet when I try to access this partition from here, I receive the error:

"Unable to mount the selected volume" (Details: "mount: according to mtab, /dev/hda2 is already mounted on /files")

I'm thinking this has to do with the ubuntu behaviour of automatically displaying non-user mountable physical volumes which are mounted in the 'media' folder (cf. [http://ubuntuforums.org/showthread.php?t=185059)](http://ubuntuforums.org/showthread.php?t=185059)). However, as this partition is not mounted in the media folder, I cannot access it from this link in my "Computer" folder...

Is there a way to remove this icon/link from the "Computer" folder (or at least to have it point to '/files' as opposed to, I'm assuming, '/media/files')?

(P.S. Could this problem have to do with my failing [initially], to personalise the terminal code offered in section 16.5 - namely, "sudo mkdir /media/windows, sudo cp /etc/fstab /etc/fstab.bak, gksudo gedit /etc/fstab"?... obviously I didn't need to make a windows directory in the media folder as the NTFS partition to be given read/write access was already mounted at location '/files')

---


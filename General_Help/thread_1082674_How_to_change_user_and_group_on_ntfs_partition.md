---
title: "How to change user and group on ntfs partition"
date: 2009-02-28
forum: General Help
---

### Post by steviefordi on 2009-02-28
I've been trying to change permissions on a directory (and some files) that is stored on a partition of my HD that is mounted from fstab at startup. It's my Windows partition so naturally is ntfs.

Everything on this partition seems to belong to user 'root' and group 'plugdev'. When I run '**sudo chown *user file***' I get no errors but nothing changes. The file is still owned by root and plugdev.

Any help would be appreciated.

---

### Post by hyper_ch on 2009-02-28
you can't... ntfs doesn't support unix permissions.

---

### Post by bodhi.zazen on 2009-02-28
Moved to general help.

Ownership and permissions on a FAT or NTFS partition are set at the time you mount. These settings are applied uniformly to the entire file system, so you can not set them for an individual directory or file.

See : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by steviefordi on 2009-03-01
Ok thanks guys. I'll stop trying now.

---


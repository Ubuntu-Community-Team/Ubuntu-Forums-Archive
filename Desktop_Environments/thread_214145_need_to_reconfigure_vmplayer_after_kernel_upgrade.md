---
title: "need to reconfigure vmplayer after kernel upgrade"
date: 2006-07-12
forum: Desktop Environments
---

### Post by evilhomer on 2006-07-12
but vmware-config.pl isn't found.  that's how i did it when i compiled from source.  now i have vmplayer installed via apt-get.

i also tried dpkg --reconfigure but no luck.

---

### Post by evilhomer on 2006-07-12
hmm, after looking around, found this:

[http://www.mail-archive.com/dapper-changes@lists.ubuntu.com/msg11807.html](http://www.mail-archive.com/dapper-changes@lists.ubuntu.com/msg11807.html)

looks it says you shouldn't have to reconfigure after kernel upgrade.  i'm changing the title.

this is the error i get:

> Could not open /dev/vmmon:
No such file or directory
Please make sure that the kernel module vmmmon is loaded

It was working fine before the upgrade.

---

### Post by evilhomer on 2006-07-12
ah, I see this post: [http://ubuntuforums.org/showpost.php?p=1244947&postcount=20](http://ubuntuforums.org/showpost.php?p=1244947&postcount=20)

:(

---


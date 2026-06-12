---
title: "Cleaning up after a hard reset"
date: 2006-02-19
forum: Desktop Environments
---

### Post by QwUo173Hy on 2006-02-19
After my system locked up, I was left with no choice but to pull the plug. What do I need to do to clean up after this? Mandriva used to alert me during the subsequent boot and cleanup devices nodes and so on. I'm paraniod that my system will be broken after this.

Regards,
Jarlath

---

### Post by QwUo173Hy on 2006-02-20
Well, I've since learned that the ext3 filesystem used by ubuntu doesnt require such checking after a power fail, because it keeps a journal of the filesystem. How effective it is I dont know. But I have switched my filesystems to ext3 using this article
[http://www.troubleshooters.com/linux/ext2toext3.htm](http://www.troubleshooters.com/linux/ext2toext3.htm)

---

### Post by Jucato on 2006-02-20
i think the fsck command is linux's counterpart to chkdsk stuff. Also, ubuntu performs a routine check every 30th time a partition is mounted.

---


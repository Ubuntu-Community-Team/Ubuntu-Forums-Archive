---
title: "I need some HALP"
date: 2009-03-28
forum: General Help
---

### Post by 3startuna on 2009-03-28
Ok So I installed ubuntu (yay) been running it now for awhile and am very pleased. During the install I discovered a hidden partition on it, that contained the viao recovery files. I deleted that partition, and made another partition one formated as Ext2 and one as ext3. 

I have ubuntu on the ext3 partition. 

So anyway, I decided since I wasnt using the ext2 partition for anything to delte it and merge it with the ext3 to get more space.

I deleted the partition fine etc. But when I start my OS ubuntu is still searching for the ext2 partition. How do i tell it its no longer there, and stop it from checking for that partition?

---

### Post by HermanAB on 2009-03-28
Here you go:

$ sudo gedit /etc/fstab

and delete the offending entry.

---

### Post by 3startuna on 2009-03-28
thank you for the fast response

---


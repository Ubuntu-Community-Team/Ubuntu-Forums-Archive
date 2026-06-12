---
title: "New Filesystem"
date: 2006-09-05
forum: Desktop Environments
---

### Post by brucevangeorge on 2006-09-05
How do I change the filesystem that Ubuntu uses?

Does the filesystem have to be in place before Ubuntu is installed or can the current one be changed?

I'm thinking jfs for the main partition and XFS for the swap. How do I do this?

---

### Post by taurus on 2006-09-05
You can't use xfs for swap!!!  Swap is swap and if you look at your /etc/fstab, you would know that...

---

### Post by tturrisi on 2006-09-05
good artice re debian file systems here:
[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

key point for me is that there are many many tools-utilities-software for extX file systems and less for reiser, xfs, jfs...

---

### Post by brucevangeorge on 2006-09-05
Yes, but how do I change the filesystem? And how do I get Ubuntu to work with it?

---

### Post by brucevangeorge on 2006-09-05
bump

---

### Post by closet geek on 2006-09-05
It's not a smart idea to try and change the filesystem type of an installed system. If you really must use: [http://gentoo-wiki.com/HOWTO_Convert_Filesystems](http://gentoo-wiki.com/HOWTO_Convert_Filesystems)

Of course rm -rf * would be quicker.

cg

---


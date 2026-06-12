---
title: "Can't view NTFS partition (Solved)"
date: 2005-12-02
forum: Desktop Environments
---

### Post by bathini on 2005-12-02
Friends

I am trying to view my NTFS partition but I get

You do not have the permissions necessary to view the contents of "hda2".

When I try to click on the mounted partition. I am not sure how to go about fixing this. 

Thanks

Bathini

---

### Post by aysiu on 2005-12-02
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by Ampersand on 2005-12-02
To run nautilus as root, run
```
gksudo nautilus
```
either from a terminal or the 'run application' box (from pressing Alt and F2) and you should be able to access it.

---

### Post by aysiu on 2005-12-02
P.S. NTFS is read-only in Linux.

---

### Post by bathini on 2005-12-02
Thanks a lot, I can now read NTFS. I used the gksudo nautilus command. Its okay if I can not write, because I know I would damage the NTFS partition. 

;) 

Bathini

---


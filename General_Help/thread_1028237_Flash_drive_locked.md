---
title: "Flash drive locked"
date: 2009-01-02
forum: General Help
---

### Post by sumpm1 on 2009-01-02
Hey guys I am having a problem with a microsd card here. Every time I insert the microsd (flash card) all of the folders come up locked and I am unable to modify any of the contents. Everything was working fine on this card recently. What could be the problem?

---

### Post by linux_tech on 2009-01-02
you could transfer the files off it, reformat it, move the files back on

---

### Post by Tomatz on 2009-01-02
Change the permissions of the files on the drive to be owned by you.

Use nautilus as root to do this. Just type the following into a terminal:

```
gksu nautilus

```
Then r click on a folder in the root of the flashdrive and click ***properities, permissions***. Then change the owner to you and ***apply to enclosed files***.

---

### Post by timcredible on 2009-01-02
that happens when you have errors on the media (maybe you removed it without doing an unmount?).  run a dosfsck on it.

---


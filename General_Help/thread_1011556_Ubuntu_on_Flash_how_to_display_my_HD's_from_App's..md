---
title: "Ubuntu on Flash how to display my HD's from App's."
date: 2008-12-14
forum: General Help
---

### Post by speed32219 on 2008-12-14
I have Ubuntu Hardy on a 4 GB flash.  Works great, but when I run an application like dvd copy or K9 copy I can not save the files to a HD.  I can transfer files back and forth from the ntfs hd's (XP) using Navigator but the App's just do not show any HD's attached in the system.  Everything points to the Flash.

---

### Post by DGortze380 on 2008-12-14
> **speed32219 said:**
> I have Ubuntu Hardy on a 4 GB flash.  Works great, but when I run an application like dvd copy or K9 copy I can not save the files to a HD.  I can transfer files back and forth from the ntfs hd's (XP) using Navigator but the App's just do not show any HD's attached in the system.  Everything points to the Flash.

Are you sure the drives are mounted?

Can you post the output of 

```

cat /etc/fstab

```

---


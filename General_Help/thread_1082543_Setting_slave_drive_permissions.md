---
title: "Setting slave drive permissions"
date: 2009-02-27
forum: General Help
---

### Post by Indy452 on 2009-02-27
I actually need to remove permissions for my slave. I finally found it and now when I go to open it I get this dang "permission denied" message. I am unable to grant myself (admin) the permission to use my own slave hard drive.  Does anyone know how I can get this hd mounted and up and running with my own permissions?

Neal

---

### Post by taurus on 2009-02-27
What filesystem is that drive and where do you mount it to, mount point?  If it's ext3, then can change the ownership of the mount point from root to your login name.

Assuming it is mounted to /media/sdb1 and your login name is indy, you would do something like

```
sudo chown -R indy:indy /media/sdb1
ls -la /media
```

---


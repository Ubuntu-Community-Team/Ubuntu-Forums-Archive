---
title: "Getting file permissions"
date: 2009-05-15
forum: General Help
---

### Post by jbumgar on 2009-05-15
I'm trying to rename my Xorg.conf file but gedit says I don't have permission to do it.  How do I get the permission to do it?

---

### Post by prem1er on 2009-05-15
> **jbumgar said:**
> I'm trying to rename my Xorg.conf file but gedit says I don't have permission to do it.  How do I get the permission to do it?


```
sudo vi /etc/x11/xorg.conf
```

---

### Post by prem1er on 2009-05-15
Before you edit that file, I suggest you back it up first.

---

### Post by glotz on 2009-05-15
Your user doesn't have write privileges in that folder so you must become super user, that is use sudo. And if you want to run a graphical program as a super user, use gksu. vi is a bit tricky to use. Perhaps just```
gksu gedit /etc/x11/xorg.conf
```

---


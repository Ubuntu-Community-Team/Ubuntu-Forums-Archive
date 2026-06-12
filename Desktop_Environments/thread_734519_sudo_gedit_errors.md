---
title: "sudo gedit errors"
date: 2008-03-24
forum: Desktop Environments
---

### Post by Jeztastic on 2008-03-24
Hi

sudo gedit in KDE and Xubuntu generates this error message:

```
root@server:/home/jez# gedit smb.conf

(gedit:5732): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

It also opens gedit in all 4 desktops in Xubuntu. Having done a search it seems Gedit is a bit buggy, but has anyone found a workaround? Can't find one on search...

Thanks,

Jez

---

### Post by rainwalker on 2008-03-25
Try```
gksudo gedit
```instead, but only in Gnome (I don't think gksudo works in KDE or XFCE, but you could still try it)

---

### Post by chewearn on 2008-03-25
In KDE, gksu is replaced by kdsu.
In Xubuntu, it's same as in Ubuntu Gnome.

---

### Post by angry_johnnie on 2008-03-25
Why don't you try kdesu instead of sudo?

Also, replace gedit with kate, which is KDE's default text editor.

If you're using XFCE, I think it'll be mousepad.

---


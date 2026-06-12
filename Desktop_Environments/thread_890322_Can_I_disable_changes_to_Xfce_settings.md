---
title: "Can I disable changes to Xfce settings?"
date: 2008-08-14
forum: Desktop Environments
---

### Post by timkoop on 2008-08-14
I'm running Xubuntu 8.04 on our family computer, and our little kids love to play around on it.  It is not uncommon to find the panel missing or unhelpful changes like that.  Is it possible to somehow disable this or require a password as if it were a security setting?

Thanks.

--
Tim

---

### Post by mali2297 on 2008-08-16
You can use *kiosk mode*, see [http://wiki.xfce.org/howto/kiosk_mode](http://wiki.xfce.org/howto/kiosk_mode).

To create and edit the file /xdg/xfce4/kiosk/kioskrc, use the command
```

gksudo mousepad /xdg/xfce4/kiosk/kioskrc

```
Add entries like
```

[xfce4-panel]
CustomizePanel=%admin

```
This makes it so that only users in the *admin* group are allowed to customize the panel. 

I suggest that you create a special user account for your kids which does not belong to the *admin* group.

---


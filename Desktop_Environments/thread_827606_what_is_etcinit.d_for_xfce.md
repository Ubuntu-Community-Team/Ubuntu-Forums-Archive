---
title: "what is /etc/init.d/? for xfce"
date: 2008-06-12
forum: Desktop Environments
---

### Post by Xiong Chiamiov on 2008-06-12
So, for stopping gdm, I can run
```

sudo /etc/init.d/gdm stop

```
and for kdm
```

sudo /etc/init.d/kdm stop

```
but what is it for XFCE?  I thought it would be
```

sudo /etc/init.d/xdm stop

```
but that's not it.  In fact, there isn't much starting with "x" in init.d:
```

pearson@pearson-linux-1337ness:~$ ls /etc/init.d/x*
/etc/init.d/x11-common  /etc/init.d/xserver-xorg-input-wacom

```

---

### Post by sdennie on 2008-06-12
Doing an:

```

apt-cache show xubuntu-desktop

```

Says that it depends on gdm so, I assume it just uses gdm with a custom theme.

---

### Post by Xiong Chiamiov on 2008-06-12
Ah, that makes sense, since it's so GNOME-like.  I have all 3 installed, so I didn't even think about that.  You're always a help vor.

---

### Post by sdennie on 2008-06-12
Glad to help.  On another note, there is actually an xdm but, it's the old school display manager that people struggled to get to work long ago and finally settled on just typing "startx".  ;)

---


---
title: "How to install Gnome on Server Edition Ubuntu 6.10 [Resolved]"
date: 2007-02-03
forum: Desktop Environments
---

### Post by explorer1979 on 2007-02-03
Dear all,

How to install Gnome on Server Edition Ubuntu 6.10

Need enter what command to do this?

Thank for your time.

---

### Post by aysiu on 2007-02-03
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by explorer1979 on 2007-02-03
aysiu,

Thank you very much

---

### Post by coastdweller on 2007-02-03
Thanks from me too! =)

---


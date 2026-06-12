---
title: "X Window won't work!"
date: 2007-02-05
forum: Desktop Environments
---

### Post by mystman on 2007-02-05
I was trying to install Beryl on my 1.2ghz Celeron, 512mb RAM, ATI Radeon 7000, Ubuntu 6.10 system.  When I ran beryl or beryl-manager my system would crash and I would have to go in to a terminal or reboot.  So I removed the beryl startup script.  Now X Window won't start.  Any ideas?


Andy

---

### Post by taurus on 2007-02-05
<Ctrl><Alt>F2.  Log in and then run

```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by mystman on 2007-02-05
Thanks.  I'll try that when I get home.

---


---
title: "Missing xorg-config &amp; xorgcfg"
date: 2005-12-06
forum: Desktop Environments
---

### Post by deaz on 2005-12-06
Clean Ubuntu 5.10 Installation and it seems like some programs are missing :(

```
root@deaz:/home/deaz# xorg-config
bash: xorg-config: command not found
root@deaz:/home/deaz# xorgcfg
bash: xorgcfg: command not found

```

Sudo'ed the commands first but same error. I tryed to login as root and see if it would help but without luck.

X.org is working and running...
Tryed google'ing around but without any luck, sorry. Hope you can help me with this problem :confused: 

- Bedst Regards, Deaz

---

### Post by Ampersand on 2005-12-06
Hi
The equivelent of xorgcfg is running
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by deaz on 2005-12-06
Thanks, worked :)

---


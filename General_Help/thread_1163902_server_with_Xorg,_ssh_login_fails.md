---
title: "server with Xorg, ssh login fails"
date: 2009-05-19
forum: General Help
---

### Post by Tobiask on 2009-05-19
hi there,

i have a ubuntu 8.04 minimal inst. an amd64
i installed ubuntu-desktop pakets and gdm
i rebooted the machine 

now i cannot login via ssh, gives me an errormessage like this:

```
Server refused to allocate pty
/usr/bin/X11/xauth:  creating new authority file /root/.Xauthority
stdin: is not a tty
```

my fstab looks like this:
```
devpts               /dev/pts    devpts     mode=0620,gid=5         0 0

```

i tried to fix this via MAKEDEV, a tty is present, but not a pty...

any idea?

---

### Post by Tobiask on 2009-05-20
nobody an idea?

---


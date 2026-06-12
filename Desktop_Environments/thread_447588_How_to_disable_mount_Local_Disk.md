---
title: "How to disable mount *Local Disk*?"
date: 2007-05-18
forum: Desktop Environments
---

### Post by HolyJoe on 2007-05-18
I'd upgrade to ubuntu 7.04 that's beautiful. But, it mount the *Local Disk* on startup and stand on my desktop. My question is how to disable it when startup.

Thanks.

---

### Post by taurus on 2007-05-18
You can edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and place a # in front of the entry (partition) that you don't want to mount at boot.  Save it and reboot.

---

### Post by HolyJoe on 2007-05-18
Thank you for your reply.

But, In fstab's man page, I saw " fstab is only read by programs, and not written". Can I directly edit this fstab by hand?

---

### Post by taurus on 2007-05-18
Yes, you need to edit /etc/fstab as root since only root can edit it, not you--regular user.

```
gksudo gedit /etc/fstab
```

---

### Post by HolyJoe on 2007-05-18
It's ok. Thank you very much.

---


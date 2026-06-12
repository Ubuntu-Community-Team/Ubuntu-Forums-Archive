---
title: "sudo kate error"
date: 2006-01-04
forum: General Help
---

### Post by pjman on 2006-01-04
Does anyone know why I can't start kate with root access? I get this error:

```

pjman@home:~$ sudo kate /etc/X11/xorg.conf
Password:
Error: "/var/tmp/kdecache-pjman" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
kate: ERROR: Communication problem with kate, it probably crashed.
pjman@home:~$

```

Thanks!

---

### Post by Adrian on 2006-01-04
Use "kdesu" instead of "sudo". Sudo doesn't work with Kate.

---

### Post by pjman on 2006-01-04
Cool, thanks.

---

### Post by bored2k on 2006-01-04
Or just use sudo kwrite

---


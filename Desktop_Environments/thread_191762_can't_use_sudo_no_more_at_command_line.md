---
title: "can't use sudo no more at command line"
date: 2006-06-07
forum: Desktop Environments
---

### Post by lime4x4 on 2006-06-07
here is the error i'm getting 

john@kubuntu:~$ sudo apt-get update
john is not in the sudoers file.  This incident will be reported.
john@kubuntu:~$


This just started to day

---

### Post by aysiu on 2006-06-07
Boot into recovery mode. You'll be root. Then type ```
cp /etc/group
nano /etc/group
``` Add *john* to the *admin* group and the *adm* group.

---

### Post by nanotube on 2006-06-07
[QUOTE=aysiu]Boot into recovery mode. You'll be root. Then type ```
cp /etc/group
nano /etc/group
``` Add *john* to the *admin* group and the *adm* group.[/QUOTE]
you appear to be missing destination filename for your cp command. it should be
```
cp /etc/group /etc/group.backup
```

---

### Post by aysiu on 2006-06-08
Thanks for the catch, nanotube.

---


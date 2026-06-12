---
title: "shutdown only for sudoers"
date: 2005-12-10
forum: Desktop Environments
---

### Post by moment on 2005-12-10
Hello,
Does anybody know how I can set my ubuntu server to shut down from Gnome only by sudoers? I know that in terminal it can only be done by root but in Gnome you can easliy halt the system and it doesn't ask for the root password.

cheers
Hamid

---

### Post by khc on 2005-12-10
If you make the shutdown command non-executable by anyone but root, gnome won't let you shutdown the system, iirc anyway.

---

### Post by moment on 2005-12-10
[QUOTE=khc]If you make the shutdown command non-executable by anyone but root, gnome won't let you shutdown the system, iirc anyway.[/QUOTE]

I changed the permissions of /sbin/shutdown non executable for others and still I can shutdown the computer via Gnome. I remembre that I was able to do this in SuSE so there must be a way I reckon.

---

### Post by moment on 2005-12-17
Ok just in case anybody is interested to know:
Apparently there is no way to ask for the password if a user halts the system from gdm. But you could disable this feature completely by turning off the "SystemMenu" variable in "/etc/gdm/gdm.conf":

```

SystemMenu=false
```

---


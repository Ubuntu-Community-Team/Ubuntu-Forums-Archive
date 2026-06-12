---
title: "Deleted admin group (KUBUNTU)"
date: 2008-12-30
forum: General Help
---

### Post by lune on 2008-12-30
I accidentally deleted my admin group and now I can't use sudo.

How do I restore or add the admin group back?

---

### Post by taurus on 2008-12-30
Boot into recovery mode from GRUB menu and add your username back to group admin.

```
adduser <username> admin
```
Then reboot.

```
shutdown -r now
```

---


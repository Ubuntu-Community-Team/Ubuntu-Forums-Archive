---
title: "HELP With Nautilus"
date: 2009-02-16
forum: General Help
---

### Post by Adrenochrom3 on 2009-02-16
hey thanks for reading. Im having problems with my nautilus. whenever i open it, it never asks me for my password. so it makes it kinda hard to move files to places where i need them. how do i fix this problem?

thanks

---

### Post by cariboo on 2009-02-16
NAutilus will never ask you for a password. If you need to access files you don't have privileges  to you can press Alt-F1 and type:

```
gksu nautilus
```

This will open nautilus as root.

Jim

---

### Post by Tim Sharitt on 2009-02-16
If you are needing to move files with root privileges, you need to start it from the terminal or by hitting Alt-F2 and enter
```
gksu nautilus
```

---


---
title: "change to GDM"
date: 2008-10-26
forum: Desktop Environments
---

### Post by varunkant on 2008-10-26
Hello everyone
                 I am using Ubuntu 8.04. Plz tell me how can i make GDM to my default display manager...


thanks

---

### Post by fornix on 2008-10-26
What is your default currently?

---

### Post by benerivo on 2008-10-26
If you install gdm then it should ask you which display manager you want to use. If gdm is already installed, then you can edit```
/etc/X11/default-display-manager
```and change the first and only line to read```
/usr/bin/gdm
```

---


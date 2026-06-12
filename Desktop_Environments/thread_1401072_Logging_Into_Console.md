---
title: "Logging Into Console"
date: 2010-02-07
forum: Desktop Environments
---

### Post by jade1138 on 2010-02-07
Is there a way to set up Ubuntu with the option to log into a command prompt instead of a GUI?

---

### Post by alarme on 2010-02-07
-> System - Admin - Services
disable gdm

To start a graphic session, at the command prompt:
$ su /etc/init.d/gdm start

---


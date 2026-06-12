---
title: "shutdown script"
date: 2009-04-14
forum: General Help
---

### Post by rapchee on 2009-04-14
hi
i have network mounts with fusesmb and with 'normal' cifs mount and sometimes i forget to umount them, which means the shutdown slows down. i think it would be better to automate this somehow. how can i achieve this?

---

### Post by apmcd47 on 2009-04-14
> **rapchee said:**
> hi
i have network mounts with fusesmb and with 'normal' cifs mount and sometimes i forget to umount them, which means the shutdown slows down. i think it would be better to automate this somehow. how can i achieve this?

I've no idea how to use fusesmb, but assuming you can unmount all with, say: 
```
fusesmp unmount -all
```
put the command into a script which can be named */etc/rc3.d/K99fusesmb_unmount*. Remember to make it executable.

Andrew

---


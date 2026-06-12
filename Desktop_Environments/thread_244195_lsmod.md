---
title: "lsmod"
date: 2006-08-26
forum: Desktop Environments
---

### Post by petervdv on 2006-08-26
lsmod shows a lot of  drivers loaded
how do I get rid of the ones I don't need?

---

### Post by elettronicha on 2006-08-26
If the driver is built in kernel, you have to recompile the kernel without the support for that driver. If the driver is a module you have to release or to blacklist that (I think).

---

### Post by petervdv on 2006-08-26
ok, thnx
but how can I know if it's compiled in or not?

---

### Post by Woei on 2006-08-26
> **petervdv said:**
> ok, thnx
but how can I know if it's compiled in or not?

Compiled in drivers do not show in the output of lsmod. Moreover, most modules loaded by ubuntu are indeed necessary, and based on hotplug support. Blacklisting of certain modules can be accomplished by adding the correct module name in /etc/modprobe.d/blacklist. But really, be careful about which module you blacklist. You could end up with a nonbooting system, or worse, a system that boots without critical support like, for example, the module that controls the fans for your processor.

---

### Post by mejy on 2006-08-26
To add to what Woei said,  there will be no noticable performance gain and it could well cause problems with future updates unless you know what your doing.

---


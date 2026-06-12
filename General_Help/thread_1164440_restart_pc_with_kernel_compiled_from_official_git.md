---
title: "restart pc with kernel compiled from official git"
date: 2009-05-19
forum: General Help
---

### Post by biasquez on 2009-05-19
hi, i'm compiled kernel jaunty from official ubuntu kernel git and i edit only option relative to support 4 gb of RAM. everything works fine exempt when i reboot my system: i see blank screen, i can't see grub and i can't choose anything and system restart again with default kernel...

---

### Post by Concrete on 2009-05-19
> **biasquez said:**
> hi, i'm compiled kernel jaunty from official ubuntu kernel git and i edit only option relative to support _4 gb of RA_M.

Whats default value?

Try 3gb...

---

### Post by biasquez on 2009-05-19
> **Concrete said:**
> Whats default value?

Try 3gb...

fixed, this error depends on kexec-tools ([https://bugs.launchpad.net/ubuntu/+source/kexec-tools/+bug/364889](https://bugs.launchpad.net/ubuntu/+source/kexec-tools/+bug/364889))

---


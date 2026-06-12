---
title: "No more desktop effects after jaunt installation"
date: 2009-04-23
forum: General Help
---

### Post by fs3rp4 on 2009-04-23
Hello!

I installed jaunt on a Dell inspiron 1525 full Intel with Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller.

I can't enable the desktop effects. 

Someone had this problem too?

---

### Post by Peter09 on 2009-04-23
Check System->Administration->Hardware Drivers

Have you a driver waiting to be enabled?

---

### Post by fs3rp4 on 2009-04-23
> **Peter09 said:**
> Check System->Administration->Hardware Drivers

Have you a driver waiting to be enabled?

Nope. Intel uses only non-proprietary drivers.

---

### Post by pappfer on 2009-04-23
Unfortunately your card is blacklisted.

You can edit your /usr/bin/compiz file to remove it from the blacklist and then you'll be able to use desktop effects. But it's not recommended, it's been blacklisted for a reason! So do it at your own risk!

---

### Post by fs3rp4 on 2009-04-23
> **pappfer said:**
> Unfortunately your card is blacklisted.

You can edit your /usr/bin/compiz file to remove it from the blacklist and then you'll be able to use desktop effects. But it's not recommended, it's been blacklisted for a reason! So do it at your own risk!

I won't. Thank you.

---


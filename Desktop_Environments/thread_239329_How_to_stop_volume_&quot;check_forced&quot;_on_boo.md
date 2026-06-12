---
title: "How to stop volume &quot;check forced&quot; on boot?"
date: 2006-08-19
forum: Desktop Environments
---

### Post by jnoreiko on 2006-08-19
Nearly every time I boot, one of my partitions requires a check -- the booter drops from the graphical screen to the text version, and says something like:

> /dev/ mounted 30 times without being checked, check forced

Since I'm mounting a few partitions, I manage to get this message about every other time I boot.
How do I prevent this from happening?

---

### Post by slimdog360 on 2006-08-19
[http://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/]("http://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/")
ta da

---

### Post by jnoreiko on 2006-08-19
That was fast! Thanks :)

> is very reasonable for a desktop, which is seldom rebooted

Er... I boot mine every time I want to use it. I haven't dared try hibernating it yet.

---

### Post by slimdog360 on 2006-08-19
read it again, is says that its reasonable to have the force check thing is you sledom reboot. But for laptop users etc its not so cool.

---

### Post by jnoreiko on 2006-08-19
I got it.

I'm just questioning the assumption that desktop machines are left on 24 hrs a day. Some us care about the environment :)

---


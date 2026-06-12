---
title: "can i change the number of rc.local in /etc/rc2.d to make it start earlier?"
date: 2008-12-23
forum: General Help
---

### Post by andrewwg94 on 2008-12-23
i have a command in /etc/rc.local. i want to make it start before GDM does. if i just rename /etc/rc2.d/S99rc.local to a number before 30, can I make it run earlier? or will that mess up everything?

please help thanks!

note: i'm on a PPC64 PlayStation 3.

---

### Post by dcstar on 2008-12-23
> **andrewwg94 said:**
> i have a command in /etc/rc.local. i want to make it start before GDM does. if i just rename /etc/rc2.d/S99rc.local to a number before 30, can I make it run earlier? or will that mess up everything?


You do not rename existing System files, you create a new one for your own purposes.

---


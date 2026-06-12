---
title: "Reducing the number of virtual terminals"
date: 2006-08-15
forum: Desktop Environments
---

### Post by sparks40 on 2006-08-15
How can I reduce the number of virtual terminals from 4 to 2. I tried commenting out the appropriate "getty" lines in /etc/inittab for numbers 3,4,5 and 6 but that does not seem to do it. Is there another control file that must be changed.

TNX

---

### Post by mlind on 2006-08-15
> **sparks40 said:**
> How can I reduce the number of virtual terminals from 4 to 2. I tried commenting out the appropriate "getty" lines in /etc/inittab for numbers 3,4,5 and 6 but that does not seem to do it. Is there another control file that must be changed.

TNX

That should do it. If you didn't reboot afterwards, you need to execute **/sbin/init q** to make the changes apply.

---

### Post by sparks40 on 2006-08-15
TNX for the response. Unfortunately, after executing commenting the getty's out and execuiting /sbin/init q, the number of virtual terminals is still four. It's got me stumped!

---


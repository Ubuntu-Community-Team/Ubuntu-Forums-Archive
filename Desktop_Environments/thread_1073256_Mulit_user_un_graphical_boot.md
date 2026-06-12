---
title: "Mulit user un graphical boot"
date: 2009-02-18
forum: Desktop Environments
---

### Post by Vishal Agarwal on 2009-02-18
I have installed the desktop environment in my server. Now my server is getting booted into X windows by default. But I wanted it to boot normally so that when ever it is required, I can use th X command to go to X environment. How can I change it.

---

### Post by Vishal Agarwal on 2009-02-18
can any one help ?

---

### Post by zika on 2009-02-18
> **Vishal Agarwal said:**
> I have installed the desktop environment in my server. Now my server is getting booted into X windows by default. But I wanted it to boot normally so that when ever it is required, I can use th X command to go to X environment. How can I change it.
it is a custom to allow 24 hours for others to read a post and answer to it.

if I were in Your place I would use **sysv-rc-conf** (install it if You do not have it) to switch off gdm. that way You would get CLI prompt at boot and You could enter X with *startx* when You want to. switching gdm off would make automount and similar stuff disappear from X but that can be solved with ```
*/etc/init.d/gdm start*
``` before *startx* ...

---


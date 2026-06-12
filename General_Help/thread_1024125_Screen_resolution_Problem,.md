---
title: "Screen resolution Problem,"
date: 2008-12-28
forum: General Help
---

### Post by slappymoe66 on 2008-12-28
I have ubuntu 8.4, I changed the screen resolution to something my monitor doesnt reoccognize. Now i can't see anything after I log on.

 

I think I need to change the resolution without logging in, any ideas or other methods?

---

### Post by linux_tech on 2008-12-28
In console type ```
xrandr
```
that will show you the available resolutions.
then type ```
xrandr -s 1024x768
```
**substitute whatever shows up as available resolution for 1024x768

---

### Post by slappymoe66 on 2008-12-28
K I fixed it by running the failsafe terminal.

Thanks.

---

### Post by linux_tech on 2008-12-28
ok, glad to hear you got it working

---


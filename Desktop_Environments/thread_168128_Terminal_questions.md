---
title: "Terminal questions"
date: 2006-04-29
forum: Desktop Environments
---

### Post by 255MP on 2006-04-29
I have used other distro of linux, but this one is slightly different for the terminal window. When I try to run a program like xmms, I would type:

xmms &

This would allow me to run my program even if I decide to close the terminal window after xmms has been opened. For some strange reason, whenever I close my terminal window, my xmms application gets killed. Is there something I have to config to get this to work?

If not, should I reconfig my bash file or something to have terminal always loaded when my session boots up?

---

### Post by bluevoodoo1 on 2006-04-29
Try...

nohup xmms

nohup xmms & ...will let you still type in the terminal (or close it and xmms will still be there)

---

### Post by 255MP on 2006-04-29
Thank you.

It is slightly weird, but I guess it will do.

---

### Post by Sef on 2006-05-01
Thank you Bluevoodoo1.  I helped me to resolve that problem.

---

### Post by bluevoodoo1 on 2006-05-01
[QUOTE=Sef]Thank you Bluevoodoo1.  I helped me to resolve that problem.[/QUOTE]


:)

---


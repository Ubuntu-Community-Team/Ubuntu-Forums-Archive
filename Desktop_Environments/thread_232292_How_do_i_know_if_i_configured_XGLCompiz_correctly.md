---
title: "How do i know if i configured XGL/Compiz correctly?"
date: 2006-08-08
forum: Desktop Environments
---

### Post by someguyouknow on 2006-08-08
i am not sure if i am even in XGL.....

---

### Post by louis_nichols on 2006-08-08
well... to find out wether Xgl is started is to issue the command:

```
ps ax | grep X
```
and see if it shows up. The ther way would be to simply try starting compiz...

---

### Post by someguyouknow on 2006-08-08
>  5483 tty7     SLs+   4:14 /usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-tXvchI
 7207 ?        RL     0:04 Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer
 7421 pts/1    R+     0:00 grep X


am i to assume that it is working right now?.....

---

### Post by louis_nichols on 2006-08-08
well... not really. I'm not sure, but thet first row, I think it shouldn't be there. I have kind of the same problem...

Did you try starting compiz? I assume you used a howto, which almost certainly explained that part, too.

---

### Post by someguyouknow on 2006-08-08
lol.....
it was definately not set up right cause it kill X
but i got that back now.....
gotta retrace to see where i went wrong....
i dont suppose you know if i am able to "redo" everything without having any problems?.....

---

### Post by louis_nichols on 2006-08-08
sorry... as i said, i have a very similar problem myself :(

---

### Post by someguyouknow on 2006-08-08
lol.....
its all good.....
thanks for the help you did give.....
every little bit helps!!!

---


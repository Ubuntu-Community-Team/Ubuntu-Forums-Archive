---
title: "cannot run x-apps as a root...."
date: 2005-05-03
forum: Desktop Environments
---

### Post by rw30 on 2005-05-03
hi

every time I try to run some x-application as a root I get an error [some problems with connectin to x server]
there is no problem when I run the app as a non-root user

does anybody know how to fix it  ? 

os: ubuntu 5.04 with KDE [kubuntu ?  :  )]

regards,

rw30

---

### Post by matthieufecteau on 2005-05-03
Maybe your problem is with the loopback interface not starting at boot.  It was my problem.

Read the second post of this thread to look further : [http://www.ubuntuforums.org/showthread.php?t=29637&highlight=loopback](http://www.ubuntuforums.org/showthread.php?t=29637&highlight=loopback)

---

### Post by mlmurray on 2005-05-03
Well, I know there is a more permanent solution, but just typing: 
"xhost +localhost" should enable you to run programs as root.

I'm sure someone else knows what script/config file controls this behaviour.

---

### Post by %hMa@?b&lt;C on 2006-06-01
the actual command is 
```
xhost +local:
``` 
the colon is necessary
-jeff

---


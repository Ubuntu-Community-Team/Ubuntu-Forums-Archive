---
title: "Question about Xsessions and XGL"
date: 2007-11-07
forum: Desktop Environments
---

### Post by TheIrishGuy on 2007-11-07
Hello

I have managed to start a 2nd Xsession on tty8 using the following command

```

/usr/bin/startx /usr/bin/startkde -- :3 > /dev/null &

```

so i now have Gnome XGL running on tty7 and KDE w/out XGL on tty8

i have tried to run the following command to start XGL on tty8 but its resulting in a window being drawn to my current session 

```
Xgl :4 -accel xv.pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama > /dev/null &
```

my understanding on it is normally X runs on 0 and XGL on 1, due to layering?

since the other x is running on 3 i thought incrementing to 4 would be the logical step, but obviously there is more to it.

why wont the above command work? am i missing something?

---


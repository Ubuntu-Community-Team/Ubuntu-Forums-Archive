---
title: "window manager"
date: 2012-01-24
forum: Desktop Environments
---

### Post by nsu freak on 2012-01-24
Hi,

I seem to have a problem with my window manager XFWM4.

There are no buttons - whole screen and x on the right top of windows and also the name of the window on top is missing.

Also I seem to not be able to have more than one workspace

It seems the problem is unsolvable.

Can anybody help?

---

### Post by Toz on 2012-01-24
Hello and welcome to the forum.

Try pressing Alt-F2 and running the following command:
```
xfwm4 --replace
```

If that doesn't solve the problem, try deleting your ~/.cache/sessions directory and logging out and back in again.

---

### Post by nsu freak on 2012-01-25
Thank you! that was very helpful!

---

### Post by 23dornot23d on 2012-01-25
Are you working ok now ....

sudo apt-get install xfce4-panel

alt+f2

xfce4-panel

Should bring up the panel if its missing .... can you do a screenshot .... or is it working ok now ..... ?

Other than that try re-installing xf4wm from synaptic or the software center .....  :confused:

---


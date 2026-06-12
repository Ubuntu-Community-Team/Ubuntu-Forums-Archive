---
title: "Window Problems in Ubuntu &amp; XGL/Compiz"
date: 2006-08-23
forum: Desktop Environments
---

### Post by rocketfu on 2006-08-23
Hey all,

1)I just installed XGL/Compiz on a fresh Ubuntu install. Now I cannot resize windows. When I rollover the corner of a window the mouse icon changes but when I click and drag there is no effect. In addition, the resize option of the popup on the lower bar has no effect. I can still move and max/min windows though.:-k 

2)Also, whenever I open a new terminal it appears partially off the screen (upper right corner) with the title bar hidden out of the screen. :confused: 

Any ideas?

Thanks in advance.

btw it's my first install of ubuntu and xgl (it kicks ***!) :twisted:

---

### Post by art on 2006-08-23
do you have resize plugin loaded?

---

### Post by jasonlfunk on 2006-08-23
I have the similar problem but I haven't been able to figure it out. It is something about Compiz's window manager not starting right I think. Notice if you start metacity, everything works fine.

---

### Post by yeehawjared on 2006-08-26
I have the exact same problem.  All the title bars are missing, so I can't move any windows around.  Anyone figure out why?  I'll try starting up metacity in an XGL session

---

### Post by axle_foley00 on 2006-08-31
> **yeehawjared said:**
> I have the exact same problem.  All the title bars are missing, so I can't move any windows around.  Anyone figure out why?  I'll try starting up metacity in an XGL session

Same problem here also, however metacity doesn't help.

---

### Post by someguyouknow on 2006-08-31
same problem on Kubuntu. Its starting to look like its by design maybe.  Could there possible be a simple command, such as holding Ctrl and clicking, that will allow you to resize or move windows in Compiz?

---

### Post by axle_foley00 on 2006-08-31
> **axle_foley00 said:**
> Same problem here also, however metacity doesn't help.

This is what I get when I run metacity:

> Window manager warning: Screen 0 on display ":1.0" already has a window manager; try using the --replace option to replace the current window manager.

And if I run *metacity --replace* it no longer uses XGL and goes back to normal.

Any ideas about this?

---

### Post by someguyouknow on 2006-08-31
If i am not mistaken, when you do a replace, you are actually replacing the window manager that was there. So metacity --replace is just replacing XGL with the normal configuration.

---

### Post by someguyouknow on 2006-09-02
found a solution....
install cgwd themer.
there you can get the bar at the top. it has some pretty cool themes too.

---


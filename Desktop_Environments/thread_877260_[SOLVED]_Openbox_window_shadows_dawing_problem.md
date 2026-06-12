---
title: "[SOLVED] Openbox window shadows dawing problem"
date: 2008-08-01
forum: Desktop Environments
---

### Post by andrewjoy on 2008-08-01
I have recently switched to openbox ( form gnome) and i must say i love it, i have been able to smooth out all but one of the problems i have had however one still remains i think i know whats causing it but i could be wrong however i have no idea how to fix it.

What the problem is when i open certain windows the shadow on the edge of them will remain on the window/ desktop image below until sum thing is "moved" over them with another window say for example Firefox.

the only things i load along with openbox are the folowing 
(note the gnome settings daemon is disabled)
xcompmgr
feh
avant-window-navigator

most of the windows that leave the shadow are animated windows like the pop ups form the dock ect however its not limited to that as the terminal emulator does the same. I think the problem is that x does not "redraw" the desktop unless its its updated as if i open the windows / pop ups in question over say a video or 3d game there is no shadow left behind as its updated frequently is there any way to force the desktop to re draw itself at a set interval ?
 
Thanks for your time.

---

### Post by Keare on 2008-08-14
I noticed this too when I ran xcompmgr and then used gnome-terminal with openbox. I see that you changed the title to be solved, what solution did you find?

Thanks :)

---

### Post by zephyrus17 on 2008-08-17
I too, have this problem. I would like to learn of the solution too

---

### Post by andrewjoy on 2008-08-17
been off the forms a bit so not checked this post the sollution i found was to change the flags in the config form -c to -C 

so 

```
xcompmgr -C -t-5 -l-5 -r4.2 -o.55 &

```

---

### Post by zephyrus17 on 2008-08-17
I have ```
xcompmgr -cC -t-3 -l-5 -r5
```
and the problem still persists

---

### Post by andrewjoy on 2008-08-18
> **zephyrus17 said:**
> I have ```
xcompmgr -cC -t-3 -l-5 -r5
```
and the problem still persists


no the flag is -C not -cC

---

### Post by andrewjoy on 2008-08-18
Positing error delete please

---


---
title: "Desktop Icons, Menu Bars, Menu, Panels Everything Gone"
date: 2011-05-01
forum: Desktop Environments
---

### Post by atul1412 on 2011-05-01
Hello
 
This is my second day with ubuntu 11.04. First impression was great but now I have a problem.
I tried to change the desktop switcher to rotate cube and I had installed compiz fusion. So I went to compiz setting, I looked for rotate cube and I ticked it. When I did this a couple of windows asking about enableing and disableing poped up, and unfortunatley I clicked them without reading. I assumed they were just interface related.
 
Know when I Restarted my laptop I don't have any main menu bar, or tool bar at the top of the desktop nor application icons on my left.
 
its really hactic 4 me Nw..
 
Thank you

---

### Post by vanadium on 2011-05-01
You will need to reset compiz and unity settings. Switch to a text terminal by pressing Ctrl+Alt+F1. Login there, and issue the following commands.
```

gconftool-2 --recursive-unset /apps/compiz-1
unity --reset

```
You better reboot now
```

sudo reboot now

```
and Unity should now launch properly when the system is ready again.

---

### Post by atul1412 on 2011-05-01
Thanks a Lotttttttttttt....
It worked... Really Haapy Now.. Thank u soooo Much...

---


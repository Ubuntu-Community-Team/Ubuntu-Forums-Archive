---
title: "Ubuntu top and bottom panel"
date: 2008-07-03
forum: Desktop Environments
---

### Post by ubockto on 2008-07-03
has gone missing, how do i get it back? I cant get access to terminal, unless someone knows of a keyboard shortcut?

---

### Post by aysiu on 2008-07-03
Does Alt-F2 work? If so, type ```
gnome-panel
``` in the Run dialogue that appears.

---

### Post by ubockto on 2008-07-03
nope, doesnt work

---

### Post by VMC on 2008-07-03
> **ubockto said:**
> nope, doesnt work

What doesn't work, getting a Terminal or type gnome-panel didn't reset the panels.

I wonder if you can type just Alt+F2 and then enter "gnome-panel".

---

### Post by ubockto on 2008-07-03
oh sorry, the run prompt when I pressed the Alt+F2 keys

---

### Post by VMC on 2008-07-03
If you type Crtl+Alt+F1 you will be entered into a virtual Terminal. Type this:

```
ps -x|grep gnome
```

See if any gnome info come back

You then type Crtl+Alt+F7 to go back.

---

### Post by ubockto on 2008-07-03
[IMG]http://img129.imageshack.us/img129/1472/ubuntumsglm9.jpg[/IMG]

this is the message i get when i type ps -x|grep gnome

do you know how i can uninstall the video driver?

---

### Post by ubockto on 2008-07-03
and it rears its ugly head again, thanks

---

### Post by ubockto on 2008-07-03
i typed sudo-get install gnome-panel, also, there was updates that were available via the ctrl-alt-f1 (terminal) using > 
sudo aptitude upgrade

and a restart and hey presto, it is now back

---


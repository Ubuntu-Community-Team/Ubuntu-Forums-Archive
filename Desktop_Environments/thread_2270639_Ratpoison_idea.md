---
title: "Ratpoison idea"
date: 2015-03-24
forum: Desktop Environments
---

### Post by Tristan_Williams on 2015-03-24
Xubuntu 14.10
Xfce 4.12
Ratpoison 1.4.6

How can I do one of the following:
[LIST]
[*]Replace Xfwm with Ratpoison as the WM, but still using Xfce everything else 
[*]Add a panel to Ratpoison 
[/LIST]

---

### Post by Bucky Ball on 2015-03-24
You could control+alt+F1, remove xfwm, sudo apt-get install ratpoison, control+alt+F1 and reboot or:

```
sudo reboot -h now
```

If things break, repeat but remove Ratpoison and install xfwm. xfwm is the window manager so, theoretically, it shouldn't effect or remove any of your xfce4 stuff. But you don't know until you try.

---

### Post by v3.xx on 2015-03-24
You may not need to remove xfwm.  Pull up synaptic and see what it breaks.

I use a terminal command to change wm, not tried on ratpoison but still may work.
While in a xfce session, enter in terminal.
```
ratpoison --replace
```

---


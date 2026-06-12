---
title: "Problems setting up fluxbox!"
date: 2007-05-12
forum: Desktop Environments
---

### Post by loathsome on 2007-05-12
Hi there.

I installed fluxbox by [FONT="Book Antiqua"]apt-get install fluxbox[/FONT], but when I try to start it, I get "Error: couldn't connect to xserver".

What do I need to to? Thanks!

---

### Post by taurus on 2007-05-12
Try to run it (pick fluxbox from the menu) from the GUI login screen, in Options (bottom left corner).

---

### Post by loathsome on 2007-05-12
Hi,

Did that, but when I logged, I only saw GNOME, and no Fluxbox.
What else should I try?

Thanks!

---

### Post by taurus on 2007-05-12
Have you tried to reboot your machine?

---

### Post by loathsome on 2007-05-12
Not actually, considering I'm running on the Live CD :KS 

I'm going to install Ubuntu soon, though - just need to test it through!

Thanks for your replies!

---

### Post by taurus on 2007-05-12
You installed fluxbox from the LiveCD and tried to start it while you already have Gnome running?  That is not going to happen.

---

### Post by loathsome on 2007-05-12
I tried to quit gnome as well (CTRL + ALT + F2)

---

### Post by taurus on 2007-05-12
<Ctrl><Alt>F2 will bring you to a console, not quitting Gnome.  Perhaps you need to kill gdm first and restart it again.

```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

---

### Post by loathsome on 2007-05-12
Thanks.

Exactly what is *gdm*?

I'll try it now.

---

### Post by taurus on 2007-05-12
GUI login screen.

---


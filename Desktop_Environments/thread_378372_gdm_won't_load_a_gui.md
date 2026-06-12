---
title: "gdm won't load a gui"
date: 2007-03-07
forum: Desktop Environments
---

### Post by vegetali on 2007-03-07
I have installed the flwm package, but gdm does not display it in the list of possible GUI. flwm works properly. I have tried it by disabling gdm and restarting. I found online a few tips to let gdm load new interfaces, but all of them refer to old version of gdm, and do not work on my system (I think that directory's names have been changed). I guess I should add something in /etc/X11/gdm, but I do not know what.

Thx

---

### Post by louis_nichols on 2007-03-07
is FLWM an entire desktop environment or just a window manager? If it's the latter, then it's normal to not find it among the gdm sessions. The way to activate it would be to log in, then press ALT+F2 and execute the command

```
flwm --replace
```

This should replace metacity with flwm. You could also tweak your user's gnome sessions to contain one that automatically starts flwm, but I'm not sure how that works...

---

### Post by vegetali on 2007-03-07
flwm is a window manager that can run by itself. It does not need a desktop environment (as gnome) to run. I do not know if you call that a desktop environment itself. In any case, many window managers are automatically loaded by gdm. These include jwm, wmaker, icewm, and others.

I would like to load flwm, mainly because I do not want to load gnome all the times. I executed flwm as you said. I did not receive any error message but... nothing happened.

thank you

---


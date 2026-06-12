---
title: "ubuntu 19.04 desktop irresponsive"
date: 2019-10-28
forum: Desktop Environments
---

### Post by aloboaleu on 2019-10-28
After (perhaps too much) tweaking the desktop (with the TWEAK app), the desktop does not work any more: I do not see the icons and main menu,
the mouse works but clicking on icons (including shutdown on top right) does nothing. 
All I can do is Ctrl-Alt F1 and then log in and run ```
sudo shutdown -h now
```
Then I can start using another desktop (LXDE). If I enter selecting Ubuntu, I get stuck and have to shutdown using the aforementioned procedure.
Any way to reocver the functionality of the default Ubuntu desktop?

---

### Post by deadflowr on 2019-10-28
The command
```
dconf reset -f  /
```
will reset the desktop to the system defaults.
It needs to be run from a graphical desktop session.
(Or at least needs an X display running.)

But if you can log into lxde you can run the command from there, then log out and try the Ubuntu session to see if it helped.

---

### Post by aloboaleu on 2019-10-29
Running dconf from within LXDE, would imply resetting LXDE to defaults as well? I like it how I have it now...

---

### Post by deadflowr on 2019-10-29
> **aloboaleu said:**
> Running dconf from within LXDE, would imply resetting LXDE to defaults as well? I like it how I have it now...

Perhaps anything dconf related would be.
But lxde is not dconf based.

If truly worried you can make it more specific with
```
dconf reset -f /org/gnome/
```

---


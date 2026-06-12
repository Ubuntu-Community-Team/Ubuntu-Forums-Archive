---
title: "Default install seems unstable, want to switch to xfce4"
date: 2015-08-22
forum: Desktop Environments
---

### Post by fkrogh2 on 2015-08-22
I have a vivid install on a new laptop.  Desktop looks like gnome, but gnome is not selected in the package manager.  I'm comfortable with xfce and given that things seem a bit unstable (mainly the mouse pointer freezes) I have installed a bunch of packages  for xfce4.  Now what??   I'd like to boot into xfce4, and get rid of whatever desktop environment was the default choice.  I'm hoping for some suggestions.  Many thanks,
Fred
I think I have marked this as solved, using Thread Tools.

---

### Post by Bucky Ball on 2015-08-22
You don't need to install any packages for xfce4. You just need:

```
sudo apt-get install xfce4
```

Log out, choose it from the Sessions menu, login. That's it. ;)

If you know what you've installed, uninstall it. You possibly don't need it. You only want the desktop environment, nothing more.

Note: Doing it this way, you will still have all default Ubuntu apps. DON'T install xubuntu-desktop as that will drag in ALL Xubuntu apps and is equivalent to installing Xubuntu from scratch on top of Ubuntu. You don't want that. 

My regular installs are a mini.iso with xfce4 and the apps I want/need only. Very light and fast.

PS: If you're sure you would prefer xfce4 and this is a new install, install Xubuntu or do a mini install with xfce4 would be my advice. :)

---

### Post by howefield on 2015-08-22
Try running...

```
echo $XDG_CURRENT_DESKTOP
```

in a terminal, to find out exactly what you are currently running.

---

### Post by fkrogh2 on 2015-08-23
I was expecting an email when replies are mad, thus the delay.  I finally stumbled on the way to get xfce loaded.  I realize now that installing xbuntu in the first place was the best solution.  But starting from where I am, I'm happy with what I have.  Work spaces work the way I like and the mouse at least for the present is not locking up.  And I have discovered unity is the package that was responsible for the default desktop.  Thanks for the responses.
Fred

---

### Post by Bucky Ball on 2015-08-23
If all is good please mark the thread as solved. See the first link in my signature. Good luck. :)

---


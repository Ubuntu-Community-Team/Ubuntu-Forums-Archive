---
title: "Disabling Fluxbox rightclick menu..."
date: 2007-12-11
forum: Desktop Environments
---

### Post by Hilipatti on 2007-12-11
Hey all,

I was just wondering how you can disable the right-click menu and add some button for it (you know, like Gnome) I really like Fluxbox but I hate the rightclick menu..

If this is even possible ^_^

---

### Post by cknight on 2007-12-11
Easy enough to disable the right click menu.  Simply comment out or remove the following line from your ~/.fluxbox/keys file:
```
OnDesktop Mouse3 :rootMenu
```

Much trickier is assigning the menu to a button.  This post talks about how to accomplish this, but I don't remember it being straightforward or easy...[http://ubuntuforums.org/showthread.php?t=371144]("http://ubuntuforums.org/showthread.php?t=371144")

Personally, I think you might be better off with a different window manager which has native support for this type of functionality.  I believe that IceWM in particular comes highly rated as lightweight but with a menu button.  Good luck!

---


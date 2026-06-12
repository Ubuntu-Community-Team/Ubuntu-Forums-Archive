---
title: "Startup programs in FVWM"
date: 2005-08-30
forum: Desktop Environments
---

### Post by ubuntme on 2005-08-30
Hi, I have install FVWM as my windows manager, but I can't figure out how to load some programs on startup.  Any ideas? on gentoo i played with the fvwm file in /etc/X11/Sessions but I don't have any such directory in ubuntu... any ideas?

---

### Post by artships on 2005-09-01
Don't have an answer, but I've noticed the problem, too.  AddToFunc "InitFunction" in .fvwm/.fvwm2rc works as expected on my SunBlade, just not in Ubuntu.  I ended-up putting my initialization things in a script called from the gnome "sessions" menu.  Still haven't found how to stop a terminal window from popping-up on bootup.

On further reflection (read, "lucky googling"), you might edit your .fvwm2rc file, replacing:

 AddToFunc "InitFunction" 

with:

AddToFunc "SessionInitFunction" 

According to _[http://www.cs.vassar.edu/cgi-bin/man2html?fvwm2+1](http://www.cs.vassar.edu/cgi-bin/man2html?fvwm2+1)_

---

### Post by linkunderscore on 2005-09-28
```
## Starts gtk theme (makes the app menus look pretty)
DestroyFunc InitFunction
AddToFunc   InitFunction
   + I Exec exec gnome-settings-daemon
```

Thats a tid bit from my config for reference.

---

### Post by ubuntme on 2005-09-30
Thanks,

All working well now :)

---


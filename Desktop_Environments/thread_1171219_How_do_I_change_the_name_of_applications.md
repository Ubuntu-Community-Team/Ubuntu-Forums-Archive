---
title: "How do I change the name of applications?"
date: 2009-05-27
forum: Desktop Environments
---

### Post by Fzang on 2009-05-27
How do I change the name of applications? I'd imagine it to be pretty easy, like editing a text file or something, however, I have no idea where to look or if it might have any impact on other applications or the system

Can anyone help me?

---

### Post by stefangr1 on 2009-05-27
One way to do this is to change the name of the executable, at the place where it's installed (often /usr/bin).

---

### Post by Fzang on 2009-05-27
Thank you! It's working :D

And this won't hurt any part of my system? Searches or anything? Can I freely do this to any application (like, system included applications)?

If you wonder why I'm doing this it's because I use global menubar and it looks stupid to have it display "gnome-appearance-properties" and "ccsm" and stuff

---

### Post by stefangr1 on 2009-05-27
> **Fzang said:**
> Thank you! It's working :D

And this won't hurt any part of my system? Searches or anything? Can I freely do this to any application (like, system included applications)?

If you wonder why I'm doing this it's because I use global menubar and it looks stupid to have it display "gnome-appearance-properties" and "ccsm" and stuff


It is not a good idea to do this with applications that are used by the system, as it doesn't know of the change and can't find the application. In that case, however, you can make a symbolic link.

Example:

sudo ln -s /usr/bin/mplayer /usr/bin/bmplayer

---


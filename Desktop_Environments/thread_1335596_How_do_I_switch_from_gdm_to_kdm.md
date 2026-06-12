---
title: "How do I switch from gdm to kdm"
date: 2009-11-23
forum: Desktop Environments
---

### Post by josephellengar on 2009-11-23
So, as I'm sure that everybody here is aware, the new gdm is really ugly.  I've installed kdm, but have several problems with it.  When I try to log in to gnome with it, it shows a terminal but does not login.  I have to go to a different tty, kill it from there, and then do a startx to get in.  And when I get in that way, my gnome-keyring is never enabled and my messages have the old theme, rather than the transparent notify-osd theme.  Does anybody have a tutorial or something on how to do this?

---

### Post by josephellengar on 2009-11-23
bump

---

### Post by listerofsmeg1 on 2009-11-23
assuming kdm is already installed:
```
sudo dpkg-reconfigure kdm
```

edit:
idiot clicked to soon :(
I had the same issue and just the reconfigure did the trick

---


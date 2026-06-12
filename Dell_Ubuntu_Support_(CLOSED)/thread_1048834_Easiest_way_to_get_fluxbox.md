---
title: "Easiest way to get fluxbox?"
date: 2009-01-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by CrazyDesi on 2009-01-23
I have been interested in running fluxbox.  Do I need to delete Gnome and run it?  If not how exactly would I do it on my Mini 12 with 8.04?

---

### Post by kerry_s on 2009-01-23
> **CrazyDesi said:**
> I have been interested in running fluxbox.  Do I need to delete Gnome and run it?  If not how exactly would I do it on my Mini 12 with 8.04?

```
sudo apt-get install fluxbox menu
sudo update-menus
```

log out, select fluxbox

---

### Post by CrazyDesi on 2009-01-23
Should I delete Gnome afterwards?

---

### Post by kerry_s on 2009-01-24
that's up to you, you can just leave it there as a backup, fluxbox is not for everyone and you might want to go back later.

---

### Post by CrazyDesi on 2009-01-24
> **kerry_s said:**
> that's up to you, you can just leave it there as a backup, fluxbox is not for everyone and you might want to go back later.

Well I haven't really decided yet.  If I did want to delete Gnome, how would I go about doing that?

---

### Post by kerry_s on 2009-01-24
you would just go into synaptic package manager, click status, installed, scroll down to the first package that starts with gnome and mark it for complete removal. be warned though it will start a chain reaction of all the gnome parts installed, you may end up with a totally boned system, if you don't read and understand whats being removed.

those of us who use a window manager only, prefer to install the base system than build up from there. it gives you a much cleaner result. i use jwm for mine, it the best window manager for me.

---


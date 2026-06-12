---
title: "Installed xmonad and now top bar is missing?"
date: 2009-01-18
forum: General Help
---

### Post by dmix on 2009-01-18
Hi,

I installed xmonad via deb package on recommendation from some experianced linux users. But I don't think I am ready to use it yet. 

The top bar (with apps/time) is now missing and I am not sure how to recover it. How is this done?

Thanks

---

### Post by Sorivenul on 2009-01-18
I don't use Xmonad on Ubuntu, so I don't know its default configuration. However, it does not run any panels, etc. However, I have run it, but for new users, it may take some adjustment. It is meant to maximize your workspace and effectiveness.

To use Xmonad from within GNOME, which you have probably been using, try [this thread]("http://ubuntuforums.org/showthread.php?t=975329"). For another nice bit of information, see [this snippet]("http://ubuntu-snippets.blogspot.com/2008/08/xmonad-tiling-window-manager.html").

Good luck!

---

### Post by dmix on 2009-01-18
To clarify, I am trying to remove Xmonad and bring back the default gnome title bar.

---

### Post by dmix on 2009-01-18
Alright I figured it out, it was the gnome-panel I was trying to restore. I found a guide via Google and it fixed it.

Metacity is still not loading as default but I'm working on fixing that next.

---

### Post by Sorivenul on 2009-01-18
I didn't understand your original goal. I'm apologize.

As for restoring your window decoration, in a terminal try:
```
metacity --replace
```

---


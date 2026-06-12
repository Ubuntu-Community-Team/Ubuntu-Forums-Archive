---
title: "Gnome Overview Problem"
date: 2013-02-28
forum: Desktop Environments
---

### Post by soundpwns909 on 2013-02-28
Hi, I just installed gnome 3.4.1 and love it so far, but I am trying to bind the overview to a mouse key.  I have successfully done so for the most part.  I have managed to get it to launch into the gnome overview but I can't get it to toggle out of the overview via the mouse button.  

I partially followed this guide

[http://www.bohemianalps.com/blog/2011/gnome-3-activate-overlay-and-more-by-mouse-button/](http://www.bohemianalps.com/blog/2011/gnome-3-activate-overlay-and-more-by-mouse-button/)

and just replace the xdotool code with this

```
dbus-send --session --type=method_call --dest=org.gnome.Shell /org/gnome/Shell org.gnome.Shell.Eval string:'Main.overview.toggle();'
```Here is what my ~/.xbindkeysrc file looks like

```
# Gnome Overview Toggle Mouse Button 10
"dbus-send --session --type=method_call --dest=org.gnome.Shell /org/gnome/Shell org.gnome.Shell.Eval string:'Main.overview.toggle();'"
release + b:10
```

Ubuntu 12.04
Gnome 3.4.1

---

### Post by soundpwns909 on 2013-02-28
Anybody?

---


---
title: "gnome-shell GNOME 3 karmic problem"
date: 2009-11-14
forum: Desktop Environments
---

### Post by bcn17 on 2009-11-14
I just installed gnome-shell to try it out. I realize there are bound to be bugs, however I wan't to get around them!


On an upgraded version of 9.10, no problems at all I used these commands:

```
sudo apt-get build-dep gnome-shell

```
```
sudo aptitude install gnome-shell
```
```
gnome-shell --replace
```

I realize the first 2 commands may be redundant - If I'm using aptitude do I need to: apt-get build-dep ?

Anyway, when I executed the last command my top panel completely disappeared, and rather than being replaced with any of the gnome3 GUI all I had was my desktop- That is it. I could alt+tab to switch between the few windows I had open, that were completely full screened, but I had no menus of any sort. 

Any help appreciated!

---

### Post by ukblacknight on 2009-11-15
Same problem here.  In the terminal, I get a load of errors, but no Shell Panel shows up.  Trying to get my traditional panels back was a bit of a pain!

Running Ubuntu 9.10 x64, Q9550 Intel Core 2 Quad, nVidia 8800GTS 320mb.

---

### Post by bcn17 on 2009-11-15
I right clicked my desktop, made an application launcher that launched gnome-terminal, and then used that to log out ( gnome-session-save --logout) When I logged back in I was back to normal. Shortcuts like ALT+F2 were not working. I suppose it was a bug or that shortcut is just a gnome 2.x thing... hmm.

---


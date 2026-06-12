---
title: "Compiz made my desktop invisible"
date: 2007-02-24
forum: Desktop Environments
---

### Post by Rippy on 2007-02-24
I installed Beryl, but it wasn't doing transparency around the window borders. While waiting for an answer, I figured maybe Compiz would do it right without the hassle.

So I type in:
```
sudo apt-get desktop-effects
```
It installs. I go to the Control Center (I'm on feisty herd 4) and enable the desktop effects. It worked well for about 20 seconds (still had the black bar around the windows though), until I maximized a window, which ended up doing the same thing that Beryl was doing to me: the top and bottom taskbars went blank, and all my windows disappeared.

After a restart, everything was still invisible, although if I restart gnome I can briefly see the outlines of gdesklets and amsn, meaning they DO still load. Anyway, my first instinct was to call up a command-line with ctrl+alt+F1 at the login window, where I removed desktop-effects with apt-get. I restarted again, and no difference. So I reinstalled the package, uninstalled with --purge, AND used autoremove to get rid of its dependencies.

AND IT STILL DOESN'T WORK. ;_;

Has Compiz edited a config file such as xorg to cause this even after uninstall? That's the only thing I can come up with..

Thanks!

-Rippy

---

### Post by shareMenaPeace on 2007-02-24
edit

Maybe check the official compiz forum
[http://forum.go-compiz.org/](http://forum.go-compiz.org/)

[http://en.wikipedia.org/wiki/Compiz](http://en.wikipedia.org/wiki/Compiz)

---

### Post by Rippy on 2007-02-25
I'm gonna have to bump this, the Compiz forum is very inactive (and the site's down atm anyway), and I'd really like to get back to using Ubuntu again...

---

### Post by shareMenaPeace on 2007-02-25
Sorry but just guessing ...

try 

```
killall gnome-panel 
```

if this not help either manual modify your xorg or use 

```
sudo dpkg-reconfigure xserver-xorg
```

---


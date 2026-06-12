---
title: "gnome vision?"
date: 2010-04-04
forum: Desktop Environments
---

### Post by ngativ on 2010-04-04
I just installed kde 4.4.2 and i realized that it has a lot of features with an improved performance. It feels like kde 4 has a vision that gnome don't have: the future desktop.

The Gnome Project has any plans for the future?, because despite its stability , looks stuck in the past

---

### Post by Silent Warrior on 2010-04-04
Well, there's Gnome Shell/Gnome 3, all in development and the like. Have you checked out gnome.org?

---

### Post by ngativ on 2010-04-04
Thanks! i didn't notice that the project already exist. But i saw the cooncept and i still think that   the gnome3 project  is, at least,   2 years too late . Gnome will be using the gtk+ libraries still?


I'd installed the gnome-shell for testing but it runs too slow. Do i need some kind of tweak on my Xorg instalation?. I'm using a nvidia card.

---

### Post by Silent Warrior on 2010-04-05
Well, as you said: "For testing". They probably have some debugging features enabled that slow you down. Either way, I'm sure it'll be further optimised as time passes.

---

### Post by NightwishFan on 2010-04-05
The Gnome Shell is getting much better, try installing the GIT snapshot by running this command:
```
sudo add-apt-repository ppa:ricotz/testing && sudo aptitude update && sudo aptitude install gnome-shell
```

Then press alt+f2 run this command to start it:
```
gnome-shell -r
```

To exit Gnome Shell, press alt+f2 and type:
```
debugexit
```

For more information visit these links.
[http://live.gnome.org/GnomeShell](http://live.gnome.org/GnomeShell)
[http://live.gnome.org/GNOME3Myths](http://live.gnome.org/GNOME3Myths)

---


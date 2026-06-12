---
title: "convert gnome ubuntu -&gt; kde or icewm?"
date: 2006-07-02
forum: Desktop Environments
---

### Post by darenw on 2006-07-02
so far, what i like best about ubuntu is that is finds all the hardware, and has good looks.  however, it uses the heavy Gnome desktop.  I find Gnome hard to use for many reasons, and i really need all my cpu cycles and RAM for my work.   On other machines,  i usually  use icewm and xfe or some other lightweight file manager.  i heard about xubuntu with xfce - no CD for it - but  i wonder if with Synaptic, by removing gnome desktop packages and adding xfce and whatnot, could i have a setup just like as if i had loaded xubuntu?  would i still have the great hardware detection, easy recognition of USB devices being plugged in (e.g. camera) and whatever other nice things one has in xubuntu?   or would it take a lot of tweaking and fussing?  And what about using icewm (lightest WM i know of) instead?

---

### Post by IYY on 2006-07-02
> but i wonder if with Synaptic, by removing gnome desktop packages and adding xfce and whatnot, could i have a setup just like as if i had loaded xubuntu?

Yes, it will be the same thing. Even easier is this:

```
sudo apt-get install xubuntu-desktop

```

And IceWM works very well in Ubuntu, too. I use it, and I find it to be the coolest WM around. It's the only one that allows me to easily use only the keyboard and never touch my mouse.

---

### Post by darenw on 2006-07-02
Wow!! looks too easy!   will do this ASAP...

---

### Post by darenw on 2006-07-02
hmm, now, how could i have found this through the usual documentation?  

how did *you* discover this?

---

### Post by aysiu on 2006-07-02
I would use *aptitude* instead of *apt-get*: ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
``` Makes it easier to remove later, should you wish to do so.

---


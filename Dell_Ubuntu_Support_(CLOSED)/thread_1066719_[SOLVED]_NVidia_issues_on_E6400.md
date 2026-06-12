---
title: "[SOLVED] NVidia issues on E6400"
date: 2009-02-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sebvieira on 2009-02-11
I had some problems with my new Latitude E6400's nvidia card. Ubuntu (8.10) suggested nvidia driver v177 (recommended) or 173. Both gave weird problems:

* clicking on a webpage link that contains (lots of) javascript was incredibly slow. Sometimes FF seemed to hang (window turns gray) but the proceeded after a few seconds
* when typing in a gnome-terminal some artifacts remained in the window. I can't explain it better than that, but when playing angband (a roguelike game) this was really annoying (hacking at monsters who aren't there anymore, trying to walk through a wall, etc etc)

After this:
```
sudo apt-get install nvidia-glx-180 nvidia-180-modaliases nvidia-180-kernel-source
```

all my problems were gone.

---

### Post by sebvieira on 2009-02-11
> **sebvieira said:**
> After this:
```
sudo apt-get install nvidia-glx-180 nvidia-180-modaliases nvidia-180-kernel-source
```

all my problems were gone.


Yeah, except that they're not :(   Its seems to be a problem that the screen doesn't redraw all the time, except when i move the window or change virtual desktop. Oh, i'm using compiz btw.

Anyone else got a clue?

---

### Post by virtualXTC on 2009-03-13
You probably should have started a new thread since this one was marked as solved.  Nevertheless I'm having some issues with compiz so I'll report back if I find anything.

---

### Post by virtualXTC on 2009-03-13
So far it seems like it seems likely that it's a problem with NVidia's crapy proprietary drivers:
[http://en.community.dell.com/forums/t/19254128.aspx](http://en.community.dell.com/forums/t/19254128.aspx)

Switch to the opensource 'nv' driver and your problem should disappear.

Unfortunately, this means I can't run compiz.

It's too bad they didn't offer this laptop with the new AMD(ati) cards.

---


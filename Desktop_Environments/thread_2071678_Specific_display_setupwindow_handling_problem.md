---
title: "Specific display setup/window handling problem"
date: 2012-10-16
forum: Desktop Environments
---

### Post by sfrank on 2012-10-16
Hi,

I have a very specific display setup/window handling problem I have not been able to resolve satisfactorily myself.

The setting:
I have a Lenovo X200 with a pen-based touchscreen which I use for lectures; specifically okular/evince and xournal.

When using an external projector I overlap/stack both the internal and the external display and run them in their respective native resolution because only using the smaller external resolution in clone mode for both displays screws up the Wacom stylus behaviour.

So there is the following display situation:
```
+---------+
|VGA    | |
|       | |
+-------+ |
|LVDS     |
+---------+
```

Now, when running xournal in fullscreen mode or Okular in presentation mode I would like for them to only expand their windows to the smaller VGA screen size (1024x768) and not to the bigger native size of the tablet display (1280x800).

In Gnome/Unity I used to do this via special hints in the compiz display configuration. However, since both environments have becoming more and more unstable and erratic for me wrt. to xrandr switching, I'd really like to set up my configuration with KDE which has been very stable and smooth so far.

I've tried applying the geometry and window restrictions to the two applications, but they do not seem to apply for fullscreen "windows" as these always expand to the larger screen.

Any ideas and help would be much appreciated.

Thank you very much,
Stephan

---

### Post by Favux on 2012-10-17
Hi sfrank,

Out of curiosity what do you mean when you say?
> When using an external projector I overlap/stack both the internal and the external display and run them in their respective native resolution because only using the smaller external resolution in clone mode for both displays screws up the Wacom stylus behaviour.
What is the stylus doing "wrong"?

projector VGA screen size 1024x768
X200t LVDS tablet display 1280x800

Also are you using Disper for the projector?

---


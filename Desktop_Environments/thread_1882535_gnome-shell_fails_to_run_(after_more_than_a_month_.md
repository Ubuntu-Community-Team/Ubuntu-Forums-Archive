---
title: "gnome-shell fails to run (after more than a month of running fine)"
date: 2011-11-17
forum: Desktop Environments
---

### Post by AvalonSpirit on 2011-11-17
Hey,

I run ubuntu 11.10 on a dell xps 15z.

And after a month or so of being able to run gnome-shell (gnome 3.2) just fine. Today my laptop loads the gnome classic session, and no matter how many times I restart it it wont load gnome-shell.

The default graphics card is an integrated intel one.
the nvidia was supposedly working with ironhide.

I thought the problem was that the intel graphics card got deconfigured, so I tried running

```
gnome-shell --replace
```

And got the following message:

Xlib:  extension "GLX" missing on display ":0".
Error: couldn't get an RGB, Double-buffered visual

So I tried:
```
optirun gnome-shell --replace
```

And got the window deccorations of gnome-shell to run, but nothing else.

Any help anyone can offer will be greatly appreciated.

---

### Post by BillyBoa on 2011-11-17
Try to reinstall Gnome 3

```
sudo apt-get --purge remove gnome-shell
```

```
sudo apt-get install gnome-shell
```

---

### Post by AvalonSpirit on 2011-11-17
Ok, that might be the best option rather than spending hours on trying to fix it. I'll give it a try in the afternoon.
Thanks

---

### Post by AvalonSpirit on 2011-11-24
Hello again, I have reinstalled gnome-shell (using --purge). And the same thing is happening. It will only login into gnome classic.

I'm stil wondering why this might be happening as it was working fine, before it started happening

---


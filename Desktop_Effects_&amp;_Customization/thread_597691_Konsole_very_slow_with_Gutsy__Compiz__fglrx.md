---
title: "Konsole very slow with Gutsy / Compiz / fglrx"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by BillyBreen on 2007-10-30
I have Gutsy working with Compiz and fglrx and a Radeon x1300 card.  For the most part, things work very well and performance is certainly acceptable.  This is true for Gnome Terminal, pan, and just about any other GTK app I can think of.

However, I prefer to use Konsole as my terminal, and performance of Konsole is pretty terrible.  There is a noticeable (probably 500ms to 1s) delay between typing and seeing characters in the terminal.  Has anyone else experience this?  If so, is there a workaround?

Thanks!

---

### Post by Happy_Man on 2007-10-30
There is a workaround.... use Kubuntu. :p

Seriously, though, any KDE app (including konsole) will run more slowly on Ubuntu/GNOME, simply because they run on completely different backends that the system will have to juggle constantly. Hence your lag.

---

### Post by BillyBreen on 2007-10-30
Unfortunately, I prefer Gnome.  But I hate Gnome's terminal.

My question is specific to the graphics layer, and I don't quite see why the backends should be such a factor.  Performance was fine on 7.04.  It's only since moving to XGL + Compiz that I've had this problem.

---

### Post by cus on 2007-10-31
I'm getting the same problem with Kubuntu, Billy.

No compiz - responsive, snappy.
With Compiz - Konsole makes me a sad panda. The delay isn't as bad as 1s, but it's still bad enough for me to notice, and to stop compiz if I know I'm doing a terminal-heavy session.

This is under AIGLX rather than XGL

---

### Post by cus on 2007-10-31
I've just tried starting konsole with the following:

```
konsole --real-transparency
```

...and performance seems to be significantly better. Worth a shot?

---

### Post by switchfootfan on 2007-11-01
So, if a ubuntu newbie can ask, how can one get konsole onto a fresh ubuntu 7.10 installation? I *really* like the tabbed terminal feature.

---

### Post by switchfootfan on 2007-11-01
Never mind, I just ran gnome-terminal and see that it has tabs too, I just have to figure out how to rename them.

---


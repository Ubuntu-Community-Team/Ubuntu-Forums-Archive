---
title: "program memory usage"
date: 2006-08-12
forum: Desktop Environments
---

### Post by kreso on 2006-08-12
why do some , on first glance, trivial programs consume so much memory?

for instance, gnome terminal takes about 5 megs, an xfce panel applet that displays text takes 3 megs etc etc?

---

### Post by az on 2006-08-12
Unused memory is wasted memory.

If another process needs the ram, it will be dumped.  Otherwise, performance is improved by using as much ram as possible.

---

### Post by kreso on 2006-08-13
yes, I know that, that's why the kernel loads files into ram cache, but I'm not refering to that.

A simple experiment: open gnome-system-monitor, note the amount of memory usage, load gnome-terminal, and note the memory usage again. the difference is at least 5 megs, sometimes more.

I'm just curious why do these programs which use very little resources like graphics,sounds etc, use so "much" memory?

---

### Post by kerry_s on 2006-08-13
You can always use other alternative programs that are designed to use less resources. For instance instead of gnome-terminal i use xterm instead, gnome-terminal is just a fancy version of xterm so you can drop the the fancy'ness and just use the base. Depending on what apps you want to be more efficent, you can one, see if there's a base app that is running under that fancy'ness you can use or just select another app that does the same but uses less.

---

### Post by kreso on 2006-08-15
yes, I know :) in fact, I find rxvt and aterm to be much faster and lightweight then xterm.

anyway, we're drifiting away from the topic, what I find very odd is that some very simple programs use so much memory, mainly I've noticed this with gnome's or xfce's pannel applets, where an applet that just displays some text, uses 3 megs of memory! I mean, sure it has to load gtk+ I guess, but shouldn't that get loaded once and shared with the rest of gtk+ programs?

---


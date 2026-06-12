---
title: "Embedded Terminal on Desktop"
date: 2009-06-25
forum: Desktop Environments
---

### Post by Rasch_ on 2009-06-25
So I've recently worked my way through the guide posted here [http://ubuntuforums.org/showthread.php?t=535027](http://ubuntuforums.org/showthread.php?t=535027)

It's all gone pretty well except for one problem. My terminal window still has borders on it that I can't seem to get rid of (as you can see in the screen shot) does anyone have any ideas on how to remove these?

I'm using Compiz in Jaunty

---

### Post by VCoolio on 2009-06-25
system > preferences > compiz config settings manager > window decorations > in the decoration windows entry where it says "any" (unless you changed it before) add
& !(class=Gnome-terminal)
The exclamation mark means an exception is following; in this case for Gnome-terminal (it is case sensitive). Hit the + button on the right to grab windows and see what class it is. The same works for window dropshadows in the entry below the one for decorations, e.g. for Gnome-panel or Conky if you use that. You can also reverse by !any & (class=Gnome-terminal) which would mean no windows have decorations except gnome-terminal. That's not what you want in this case of course. Anyway, play with it, it takes immediate effect (no login needed) so WYSIWYG.

---

### Post by ~sHyLoCk~ on 2009-06-25
> **Rasch_ said:**
> So I've recently worked my way through the guide posted here [http://ubuntuforums.org/showthread.php?t=535027](http://ubuntuforums.org/showthread.php?t=535027)

It's all gone pretty well except for one problem. My terminal window still has borders on it that I can't seem to get rid of (as you can see in the screen shot) does anyone have any ideas on how to remove these?

I'm using Compiz in Jaunty

Use tilda for something like this:~
[[img]http://omploader.org/tMXZxYQ[/img]](http://omploader.org/vMXZxYQ)

---


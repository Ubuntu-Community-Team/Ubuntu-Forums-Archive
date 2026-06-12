---
title: "Alt + Ctrl + F10 == Time Bomb ???"
date: 2009-03-03
forum: Desktop Environments
---

### Post by xp_newbie on 2009-03-03
I was working on something, then got curious to see whether the keyboard shortcut Alt+Ctrl+F10 is assigned to anything, so I pressed it and... KABOOM! TOTAL SYSTEM RESET. I of course lost unsaved data (not too much, fortunately).

So the obvious question that comes to mind is:  Ubuntu Linux (8.04) is... **NOT** for curious people? #-o

---

### Post by spongypants23 on 2009-03-03
Ctrl + Alt + F# will take you to a different "runlevel". My advice is don't push them unless you know what you are doing.

---

### Post by xp_newbie on 2009-03-03
Hmmm... Alt + Ctrl + F7 will actually restore it to where it was (Gnome desktop). It doesn't really perform a reset, it only looks that way.

So, perhaps Ubuntu 8.04 **is** for curious people, after all. ;)

---

### Post by Ben Crisford on 2009-03-03
> **xp_newbie said:**
> Hmmm... Alt + Ctrl + F7 will actually restore it to where it was (Gnome desktop). It doesn't really perform a reset, it only looks that way.

So, perhaps Ubuntu 8.04 **is** for curious people, after all. ;)

Haha :D.

I think i'll still keep my fingers to myself after reading this though :p.

---

### Post by WatchingThePain on 2009-03-03
Meddlers pay a price lol.

---

### Post by tgalati4 on 2009-03-03
Always back up your important data BEFORE meddling!

Ubuntu and Linux in general is designed by meddlers for the sole purpose of meddling.

Unfortunately, meddling interferes with getting real work done.

Keep one machine for getting work done; set up a second machine for meddling!

---

### Post by Armor Nick on 2009-03-03
I don't want to prove everyone wrong, but I will do so anyway.

Ctrl+Alt+F# switches to another virtual terminal (I suspect we've got 10 or so), which is basically a means for someone else to log into a terminal (like the thing you get when you open a terminal emulator) on your computer. This, of course, is only for advanced users.

Edit: I just tested what you did and there is, in fact, no tenth terminal ;) .

---

### Post by albandy on 2009-03-03
TTys are defined in /etc/event.d (in earlier versions were defined in /etc/inittab)

There you can control ctrl+alt+delete, what to open when ctrl+alt+F1-12, etc ...

---


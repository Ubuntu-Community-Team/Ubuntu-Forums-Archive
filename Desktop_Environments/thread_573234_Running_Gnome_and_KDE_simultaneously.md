---
title: "Running Gnome and KDE simultaneously"
date: 2007-10-11
forum: Desktop Environments
---

### Post by Osedax on 2007-10-11
1. Does ubuntu have default (or possible) virtual consoles, as in Debian?

2. Can I run gdm and kdm at the same time, switching between them with the aforementioned consoles or something similar?

---

### Post by gibbsnich on 2007-10-11
1. Do you mean those consoles that come up when you press strg+alt+[F1 to F6]? Yes, it does.
2. Can you explain why you'd want to do that? I think you can't because g/kdm run by default on the 7. console (strg+alt+F7), I don't know of any way to tell gdm to run on #6 and kdm on #7, for example. I don't even think that would make sense because essentially both do the same thing, AFAIK: let you select and start your favourite window manager. AFAIK, both can start kde and gnome. 
With the command 'sudo dpkg-reconfigure gdm' you can select which one you'd like as your default.

HTH!

Michael

---

### Post by Dmitri on 2008-02-07
Found this thread by Google, so I thought it could help someone even though it's pretty late.

Anyway, all you gotta do is Switch user (lock or simply start new session), then you can log in with different desktop environment, with the same user account if you wish.

Oh, it will take a while to switch between environments though... so you gotta be patient (well, depending on how much you computer can handle).

---


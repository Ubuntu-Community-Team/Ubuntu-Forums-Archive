---
title: "Segfault in terminal, runs okay from shortcut"
date: 2009-03-01
forum: General Help
---

### Post by Ng Oon-Ee on 2009-03-01
Hi all,

I'm using Wine to run a program called E-Sword. Now, before you tell me to move my question to the Wine forum, I'm not asking specifically about Wine. Anyway, what happens is that, when running the program, I call the following code:-

```
env WINEPREFIX="/home/data/wine/esword" wine "C:\Program Files\e-Sword\e-Sword.exe"
```

Whenever I run this from the terminal (gnome-terminal, as is default in Ubuntu), I get a segfault. So I've been spending most of the day reinstalling Wine and the application, was driving me crazy because it would work once in a while. After a while, I figured out that it would only work when I launch it from the .desktop launcher that gets created.

So, I figured something must be borked in my terminal session. After confirming that the problem was caused by launching from gnome-terminal (and, by extension, by launching from my dock, cairo-dock) and does not appear when lauching directly by double-clicking the launcher in Nautilus, I tried to run the above line within xterm (as opposed to gnome-terminal). It ran fine, no segfault.

My question, therefore, is what additional env settings are applied to gnome-terminal (or whatever settings would cause a difference between the xterm and gnome-terminal results). I'm pretty sure I've borked something in my tweaking, it only showed up this morning, though, and I haven't recently messed around with many configs besides compiz (and yes, I disabled compiz to test, as well).

So, anyone can suggest stuff which may be contributing to this? Please note that I'm also posting this at linuxforums, can be accessed [here]("http://www.linuxforums.org/forum/ubuntu-help/141740-segfault-terminal-runs-okay-shortcut.html#post673192").

---

### Post by tombom62 on 2009-03-01
i just replied over there.  check it out.

---


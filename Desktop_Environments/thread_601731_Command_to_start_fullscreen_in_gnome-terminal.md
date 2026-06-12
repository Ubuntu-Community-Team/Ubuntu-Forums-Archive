---
title: "Command to start fullscreen in gnome-terminal?"
date: 2007-11-03
forum: Desktop Environments
---

### Post by keyboardashtray on 2007-11-03
I'm trying to figure out if there is an option to run a command in full-screen.

Specifically, for NetHack, I've got this so far:gnome-terminal --window-with-profile=NetHack --hide-menubar --command=nethack

It works OK except that when I hit fullscreen, NetHack doesn't utilize the fullscreen. It has to be in full screen before I run nethack for it to fully utilize it.

I want the perfect one-click command. Any suggestions?

---

### Post by aidanr on 2007-11-03
Couple of suggestions; If you use Compiz Fusion you can add name=gnome-terminal in the window rules plugin under fullscreen, secondly xfce4-terminal has a fullscreen switch, you should be able to run that in Gnome without pulling in lots of Xfce stuff.

---

### Post by Thyme on 2007-11-03
Hi guys,

I've also used "--geometry=<width>x<height>" to get a specific size for the terminal. Maybe it might be useful.

---

### Post by keyboardashtray on 2007-11-04
Thanks for the suggestions guys.

I actually found a command, --full-screen did the trick. (it needed that dash).

Edit: Except it isn't working all the time - only sometimes. If I start it up it usually doesn't work, but if I try again right after that it does. Hmm, does placement matter? So far it is gnome-terminal --window-with-profile=NetHack --full-screen --hide-menubar --command=nethack

---


---
title: "Where's my Terminal gone?"
date: 2010-05-19
forum: Desktop Environments
---

### Post by WarrenL on 2010-05-19
Hi folks,

I ran a 10.04 Minimal Install on an old box last night and everything went really well right up to to when I needed to do the "tasksel" bit. Wanting a basic Gnome desktop I chose to manually install packages, and knew from previous experience (and you guys here on the Forum) that I needed Gnome and gdm. 

Here's where it got interesting. I chose to install gdm first (sudo apt-get install gdm) and all the guff downloaded and installed, after which I was able to boot up to what looks like a basic Gnome desktop.

So far so good (I thought)! But there was heaps of stuff missing. No problem, I'll install gnome-core and everything will be fine. But wait! There appears to be no way of accessing a terminal in order to accomplish this. There's no link to it from within the Gnome accessories menu, and if I log out I get back to the gdm screen but there's no terminal option in the sessions menu.

Have I made a fundamental error in installing gdm before Gnome?

What can I do?

---

### Post by utnubuuser on 2010-05-19
xterm might be part of the ubuntu-desktop meta package -  can you access a terminal with ctrl+alt+F1 ?

Is gnome-terminal installed?

---

### Post by WarrenL on 2010-05-19
I can't answer either of those at the moment, but I'll try the Ctl-Alt-F1 tonight and report back.

Cheers.

---

### Post by aysiu on 2010-05-20
Control-Alt-F1 is a safe bet.

But it's also possible that *gnome-terminal* or *xterm* is installed but not in the menus, in which case (while you're logged into Gnome), you can press Alt-F2 and type in ```
xterm
``` to launch it.

---

### Post by WarrenL on 2010-05-20
Nup, I can confirm that no amount of typing into Alt+F2 could help me last night. But tonight when I got home from work Ctl+Alt+F1 gave me a terminal prompt and I'm away again!

I'll file that shortcut away in the back of my head for future reference.

Thanks once again, this forum is bloody marvellous.

---


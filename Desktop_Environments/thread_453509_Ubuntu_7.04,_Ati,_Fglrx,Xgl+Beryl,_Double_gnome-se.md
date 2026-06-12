---
title: "Ubuntu 7.04, Ati, Fglrx,Xgl+Beryl, Double gnome-settings-daemon on startup"
date: 2007-05-24
forum: Desktop Environments
---

### Post by localhost0 on 2007-05-24
Hey All.

I have weird problem with gnome-settings-daemon.
Well, It start occurring since i installed Xgl&Beryl.

As i followed the wiki, all went fine, except, one thing:

After i added Xgl profile in my gdm, and logged in i had no theme, ugly fonts and icons.

I typed "gnome-settings-daemon &" and my normal theme&icons&fonts came back, but then, I've noticed 
that my os becoming really heavy and slow. 

i checked gnome-system-monitor and saw that gnome-settings-daemon runs twice!
one of the processes, took almost half of my cpu.

Anyways, i killed one of the two process, the one with the lower pid, and fixed the problem.
if i'll kill the process with the higher pid, the ugly no-theme mode will come back.

if i'll kill them both, the no theme mode will come back, and gnome will run gnome-settings-daemon
in background, without doing anything with it.

So, i learned that i need to kill the lower pid of one of the two processes each login, in order to keep
my system running smoothly.

That's pretty annoying.. 

Btw, i remember i had this issue since the dats of 6.04 and xgl, so that's not something new.
I don't think that's something with xgl/beryl code, because i didn't have this problem with archlinux.


Is there any workaround to this?

Thanks in advance, 
Localhost(0).

---


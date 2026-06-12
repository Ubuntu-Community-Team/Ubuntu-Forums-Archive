---
title: "COMPIZ: amazing problem: sometimes compiz.real uses 100% cpu on a big pc"
date: 2009-07-20
forum: Desktop Environments
---

### Post by MisterBark on 2009-07-20
Hi !

I use compiz with ubuntu 8.10 on a big enough computer :
core2duo 6400
4GB DDR2 corsair
Nvidia 9400GT (1GB DDR2)
WD raptor system hdd
no saturated disk space
kernel 2.6.29.4-rt18 selfmade
dual screen 2560x1024

NB: I can't update ubuntu, and it won't fix the problem (see below: the backup...)

I work 12h a day on this computer and I never had any problem for more than 3 months.

**And since a few days ago, sometimes, the process "compiz.real" starts to use 100% of my cpu !** (the memory usage stills normal)
although I don't do anything with it (don't move any window or cube, no heavy apps)
NB: in the same time, the process Xorg also takes more cpu than usually, but not that much that compiz.

It happens about every 1 hour, for 10 to 30 minutes or more.
It always finishes to stop, but sometimes it's very long !
Obviously, when it happens everything is very slow, even playing a simple video without moving anything, or just scrolling into a web page. It's just like a 3 frames/s screen (except the mouse)
I carefully checked what I was doing each time it started but there's absolutely no reason ! usually it starts when I'm not touching anything.

NOTE:
I just restored a very clean backup which always worked.
Then, I used tar with -k option to put my new system files over this backup without replacing anything.
And it stills the same !
I don't use any new app than before.

Any idea ?
is there something to do when it happens to try to understand what's going on ? (a command or log ...)
I just looked in "top" and saw the very high cpu usage for the process "compiz.real" (almost 100%. usually it's about 2%).
I have no idea what else I also can examine.

I really thank you in advance !

**PS:**
I noticed something really strange :
when it happens, some faces of the cube take less cpu than others.
i.e. when I stay on the desktop 1/4 (pidgin, firefox & geany) it uses a bit less than the face 3/4 (terminal & tea)
it's not a very big difference but I really can see it on the graph. (I don't touch anything when I stay on a face and nothing happens in pidgin or terminal)

---

### Post by MisterBark on 2009-07-23
Hi !
I'm sorry but nobody has an idea ? :(

thanks !

---

### Post by Dullstar on 2009-07-24
That is a strange problem.

Just an idea, it might not work, but...

Go to Synaptic Package Manager.
Run a search for Compiz.
Mark all installed Compiz packages for re-installation.

---

### Post by MisterBark on 2009-07-24
> **Dullstar said:**
> That is a strange problem.

Just an idea, it might not work, but...

Go to Synaptic Package Manager.
Run a search for Compiz.
Mark all installed Compiz packages for re-installation.

Hi !
I just tried...
the problem stills BUT :
it's strange because it was ok at the beginning and started after 20s of video playing (continued when I stopped the video)
Usually it's also ok at log in but starts anytime, not when I do something special.
I don't if there's a link, I have to try again to be sure, but I must close everything AGAIN to logout...

And now, it's slow but faster than before (probably because the compiz.real process is freshly loaded for now)

---

### Post by MisterBark on 2009-07-24
ok, now no doubt.
It starts a few seconds after lunching a video !
After stopping the video, it continues a few minutes, then stop. (to start again in the future...)

PS: it wasn't like that before reinstalling every compiz packages. Before, it started anytime, without any special action.

---


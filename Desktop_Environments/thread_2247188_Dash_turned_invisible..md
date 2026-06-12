---
title: "Dash turned invisible."
date: 2014-10-06
forum: Desktop Environments
---

### Post by lakersforce on 2014-10-06
Using the keyboard it still functions, but nothing is rendered to the screen. Everything else about Unity is still working normally. It just suddenly behaved this way, I was not messing around with any settings or anything. Reboot does not fix it. Using the unity tweak tool to reset does not fix it. Removing all compiz configs does not fix it.

---

### Post by lakersforce on 2014-10-06
And it inexplicable started to display again just a moment ago. I have not worked on the problem since I wrote the last post.

---

### Post by lakersforce on 2014-10-06
And it turned invisible again.

---

### Post by Vladlenin5000 on 2014-10-07
Probably a graphics drivers issue... Start by posting it, ie, your graphics card/chip and, if nvidia or AT/AMD, also which drivers are you using.

---

### Post by CantankRus on 2014-10-07
In unity tweak tool try changing the dash blur to static.
You'll find it in the unity > search section.

---

### Post by Vladlenin5000 on 2014-10-07
> **CantankRus said:**
> In unity tweak tool try changing the dash blur to static.
You'll find it in the unity > search section.

Yes, please also try this ^^^^

---

### Post by lakersforce on 2014-10-08
Changing the Dash blur to static (or turning it off) does not help.

```

OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTX 260/PCIe/SSE2
OpenGL core profile version string: 3.3.0 NVIDIA 331.38
OpenGL core profile shading language version string: 3.30 NVIDIA via Cg compiler

```

---

### Post by CantankRus on 2014-10-08
Is it happenning in all scopes?
Try deleting the zeitgeist folder in **~/.local/share/** and logging out/in.

---

### Post by lakersforce on 2014-10-08
Yes. The Dash is completely invisible, no matter what scope I use.
Deleting the Zeitgeist folder did not make it visible.

---

### Post by CantankRus on 2014-10-09
Test in guest or new account to see if it's a config issue.

---

### Post by lakersforce on 2014-10-09
It seems like it might be a problem in the Nvidia driver. I tried to revert the graphics driver back to Nouveau and the Dash is visible again.
I might add that the Dash still was visible after I installed the proprietary Nvidia driver. It worked for about a week with it, before the Dash turned invisble.

---

### Post by lakersforce on 2014-10-14
I pinpointed what caused the problem. I have a dual monitor setup. By default (due to my cable setup) Ubuntu makes my left (blue) monitor the right and vice-versa. Under Display I switched the monitors around (green and blue), and I wanted to keep my Sidebar on the left side of my left monitor, so I chose Display - General Options - Launcher placement  - blue monitor, (my left, default right). Later I discarded my dual view and chose to mirror the displays. The monitor that you mirror is the default left, i.e. the green, but due to having switched the monitors and wanting to direct the placement of the launcher (which I wrongly figured meant sidebar, not Dash) to the blue monitor (only), it stays with the blue, although you do not have the option to specify it after checking 'Mirror displays'.

What I can not explain is why the Dash reappeared and disappered again within an hour, because I was not messing around with the Display options. Or why the Dash worked when I switched to the Nouveau driver (perhaps it retains display settings from last that driver was used?)

---


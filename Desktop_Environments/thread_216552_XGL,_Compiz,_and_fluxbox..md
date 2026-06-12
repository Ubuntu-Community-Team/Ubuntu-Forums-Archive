---
title: "XGL, Compiz, and fluxbox."
date: 2006-07-15
forum: Desktop Environments
---

### Post by Blazeix on 2006-07-15
Hi. I was looking at XGL, and I have a few questions. Correct me if I'm wrong, but XGL is an openGL xserver. Right now, people mainly use it with compiz to provide 3d effects for desktop switching. If I use fluxbox as my window manager, is there a way to get the 3d effect, or do I have to use a kde/gnome window manager? Thanks for any insight.

---

### Post by jpkotta on 2006-07-15
> **Blazeix said:**
> Hi. I was looking at XGL, and I have a few questions. Correct me if I'm wrong, but XGL is an openGL xserver. Right now, people mainly use it with compiz to provide 3d effects for desktop switching. If I use fluxbox as my window manager, is there a way to get the 3d effect, or do I have to use a kde/gnome window manager? Thanks for any insight.

Xgl is pretty complicated in how it fits in with all the other X stuff, but it's basically an OpenGL client that runs on top of X.org, and then acts like another server (I hope that's right).  

You can't get all the crazy effects of Compiz in Fluxbox until Fluxbox implements them.  As far as I know, Compiz is the only wm that takes advantage of Xgl.

---

### Post by Blazeix on 2006-07-15
O.K. I've also heard that xgl is faster than xorg. Is this just because compiz is faster than gnome/kde, or is xgl actually faster than xorg? Thanks for your help.

---


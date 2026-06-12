---
title: "[SOLVED] Problems with Beryl on Intel GMA X3000"
date: 2007-07-18
forum: Desktop Effects &amp; Customization
---

### Post by mysticmatrix on 2007-07-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/111257](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/111257) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am using a DG965RY motherboard and Feisty. I have installed beryl quite easily(used synaptic).
The problem is that OpenGL applications(like glxgears, xscreensaver, etc) don't seem to work well with Beryl. When I try to move a window of such a application, the output is not synced to screen i.e the application stays on its place until I leave the mouse button, and then it jumps to its new place.
This problem was also with playing video, but that was fixed by changing video output of all players I know(VLC, Mplayer, Xine, Gstreamer) to X11.
The solution I want is:
(a) Quick and dirty way to change video output of xscreensaver to something like X11 ( and get a huge hit on performance)
AND/OR
(b) Permanent way to solve OpenGL and Xv driver output problem. (Might be important if Gutsy enables desktop effects by default)

A video demonstration of my problem can be seen here: [http://www.youtube.com/watch?v=7qZ5AVt2d_0](http://www.youtube.com/watch?v=7qZ5AVt2d_0)
(Mine one has even worse syncing than that).
I am attaching my x.org file.

EDIT: The problem continues with Compiz Fusion I installed fron Trevino's Repositary

---

### Post by mysticmatrix on 2007-08-22
Bump!

---

### Post by mysticmatrix on 2007-10-24
Ok I came to know that intel needs to add something called EXA in xorg to make this stuff work.

As of Gutsy, I am blacklisted to have effects :(

---

### Post by fadumpt on 2008-01-19
so is there a fix yet or is the 3000 still blacklisted?

:(

---


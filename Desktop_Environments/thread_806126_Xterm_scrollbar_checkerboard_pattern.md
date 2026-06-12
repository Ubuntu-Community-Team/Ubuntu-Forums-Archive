---
title: "Xterm scrollbar checkerboard pattern"
date: 2008-05-24
forum: Desktop Environments
---

### Post by jnygaard on 2008-05-24
I have just converted from a hand-assembled Linux "non-distro", to Ubuntu 8.04, to save a little time by using modern package maintenance tools...

My systems is almost where I want it now, but one little thing bugs me:

The scrollbar in xterm should consist of alternating pixels in colours "scrollbar.foreground" and "scrollbar.background" respectively, in the language of X-resources.

Unfortunately, the alternating pattern has become a pattern of vertical stripes instead, and I have no idea whatsoever how this has happened or can be removed. I can not find any X-resource to affect this, so I suspect there may actually be a bug in some X-component of this distro.

Sounds strange, I know, so *please*, tell me that there is a simple X-resource setting that fixes this for me... :-)

Jay

---

### Post by kerry_s on 2008-05-24
try removing it completely and reinstalling.
are you using a .Xdefaults or .Xresources file to customize? 
if so can you post it, maybe a screenshoot of the problem to.

the main resource file for xterm is in /etc/X11/app-defaults

---


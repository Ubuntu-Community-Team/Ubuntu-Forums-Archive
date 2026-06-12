---
title: "Getting out the resolution of a video file in the GNU bash"
date: 2010-12-14
forum: Desktop Environments
---

### Post by shredIt on 2010-12-14
Hi guys,

Hopefully this post is here at the right place...

I need some information about the GNU shell.

I want to write some bash script which is able to sort movie files by resolution of that video.

I noticed under GNOME, it's able to view the resolution of a video file by rightclicking clicking on the file and choosing properties afterwards.

I would be glad if anyone could tell me which shell-command GNOME uses for this action.

Thx a lot!!

---

### Post by DaithiF on 2010-12-14
What makes you think Gnome is running a shell command to get the resolution?  More likely it is using a gstreamer library call to do that, something you wouldn't be able to easily repeat from the command line.

Instead, install the mplayer package, it includes a script called midentify which can tell you resolution, framerate, codec, etc.

---

### Post by shredIt on 2010-12-14
It worked very well...
Thx 4 this information!!!

SOLVED

---


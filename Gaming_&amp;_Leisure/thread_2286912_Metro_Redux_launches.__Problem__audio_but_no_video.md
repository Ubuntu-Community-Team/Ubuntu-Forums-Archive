---
title: "Metro Redux launches.  Problem:  audio but no video."
date: 2015-07-15
forum: Gaming &amp; Leisure
---

### Post by v1k1ng1001 on 2015-07-15
When I try to run either Metro 2033 Redux or Metro Last Light Redux from Steam, I get audio and overlay, but no video (i.e. my mouse disappears but I still see the desktop.)  I experimented with removing the video files so that it launches straight into game play with the same result--audio but no video.

Running:

Ubuntu Gnome 15.04 x64
Nvidia driver 352.21

on:

Intel i5
Nvidia 750ti


I've read a ton of threads and no one seems to be having a similar problem.  Any idea what I might try to get my system running Metro Redux?

---

### Post by MikeCyber on 2015-07-16
Other Steam games work? Download some and try. Metro needs OpenGL >=4, does your card support that?
Try in a terminal:
nvidia-settings
also run it in a term to see error messages.
I have Metro LL (not redux) working fine with my Asus GTX770.

---


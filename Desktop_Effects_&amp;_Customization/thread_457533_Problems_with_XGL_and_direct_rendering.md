---
title: "Problems with XGL and direct rendering"
date: 2007-05-28
forum: Desktop Effects &amp; Customization
---

### Post by pospam on 2007-05-28
Hi All:
I have what I think is an strange problem. 
I have followed the guide for ATI video cards and I now beryl works.
The problem is that when I start the session with XGL
Beryl works but direct rendering does not. So I cannot for example play games like
WoP. If run this commands this is what I get:

glxinfo | grep direct
I get
Xlib: extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

for
fglrxinfo I get the right output

display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600
OpenGL version string: 2.0.6334 (8.34.

Now, if I restart gnome and start a normal gnome session
direct rendering works and I can play games normally.

$ glxinfo | grep direct
direct rendering: Yes
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600
OpenGL version string: 2.0.6334 (8.34.8)

Any ideas why this is happening and how it can be solved?
Thanks all for your help.
P.

---

### Post by kpolice on 2007-05-28
Direct rendering will not work when you use XGL, as simple as that.

---

### Post by pospam on 2007-05-29
Thanks for your answer.
So I guess I have to choose, either I have beryl and cannot play games, or the opposite.
Anyway I could do both in the same session?

---

### Post by btechcs on 2007-06-01
> **kpolice said:**
> Direct rendering will not work when you use XGL, as simple as that.

I also have the same problem, may I ask why can't direct rendering work with xgl?

---

### Post by jae1227 on 2007-08-26
Time to get a Nvidia Card...

---


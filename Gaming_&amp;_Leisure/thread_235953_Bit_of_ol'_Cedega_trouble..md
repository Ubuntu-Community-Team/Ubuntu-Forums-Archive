---
title: "Bit of ol' Cedega trouble."
date: 2006-08-14
forum: Gaming &amp; Leisure
---

### Post by kimusabi on 2006-08-14
Hello fellow Ubuntu gamer's. I return with another problem.
After hour's of having issue's with nVidia driver's, I managed to get it working with having to fight with my Xorg,conf.
Yet I am faced with another problem, this time Cedega related.
I know full well that the right driver's are installed, I'ved tested them with various program's which would lag without driver's (Stellarium for example)

The problem is, Cedega doesn't seem to see that the driver's are installed.
When I run the Video Test's in Cedega, I fail at OpenGL Direct Rendering yet succed at 3D Accelration.

Suggestion's?

Cheer's,
-Kimmeh

---

### Post by kimusabi on 2006-08-14
Bump.

---

### Post by kimusabi on 2006-08-15
Anyone at all?

---

### Post by DoktorSeven on 2006-08-15
Looks like (from the Python scripts Cedega installs) it looks in glxinfo to determine whether direct rendering is enabled, and runs glxgears to see if it gives > 800FPS as its 3d acceleration test (glxgears is a very poor test of speed, IMO).

So if you fail on "direct rendering", see if it's enabled at all (from a console):

```

glxinfo | grep direct

```

Should return **direct rendering: Yes** if everything's set up right; if no, X isn't set up for 3d yet.  Instructions are [here](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia).

---


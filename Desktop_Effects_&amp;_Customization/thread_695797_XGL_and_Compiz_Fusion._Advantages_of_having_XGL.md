---
title: "XGL and Compiz Fusion. Advantages of having XGL"
date: 2008-02-13
forum: Desktop Effects &amp; Customization
---

### Post by Victormd on 2008-02-13
I've had compiz installed on my machine from the beginning and recently installed XGL. The only reason I installed XGL is that I read in a few threads that it would allow more visual effects. The only thing I noticed was a small increase in time for X to load and did not see any new effects. I was wondering, what are the true advantages of having XGL installed?

---

### Post by hyperair on 2008-02-13
There are close to none, really, if you have a driver that has AIGLX support, for example, the nVidia restricted binary driver. However, on drivers that don't support AIGLX, then XGL allows the desktop effects to run. 

Drawbacks of XGL: 
1. It's slow, bulky, eats system resources (at least on systems with relatively less resources). This happens because XGL is another X server on top of your native X server.
2. You cannot run OpenGL apps such as games and Compiz Fusion while XGL is running.

---

### Post by Victormd on 2008-02-13
So in my case, I have the nVidia restricted driver installed so having XGL is a waste of resoucrces?

---

### Post by hyperair on 2008-02-14
Yeah it's pretty much that way.

---

### Post by dman777 on 2008-02-14
Are you sure you have XGL enabled? Also I read where you need to manually set XGL from software rendering to 3d Hardware accelleration.

---

### Post by Victormd on 2008-02-14
I did have it enabled, but I just finished uninstalling it based on the replies to this thread...

---


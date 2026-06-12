---
title: "How to check if 3d acceleration is enabled?"
date: 2007-05-03
forum: Gaming &amp; Leisure
---

### Post by skywarp04 on 2007-05-03
I have fglx driver installed for my Radeon 9700 Pro card, but how do I check that 3d acceleration is working?  It doesn't seem like it is, because some of the screen savers seem like they require 3d acceleration to run decently, but they still run slow.

---

### Post by DoktorSeven on 2007-05-03
glxinfo | grep direct

should get you 

direct rendering: Yes

if it's working, No if it's not.

---

### Post by bastiegast on 2007-05-04
glxgears should also do.

---

### Post by skywarp04 on 2007-05-04
Did that, says Direct Rendering = No and glxgears only shows about 300 fps.  I have been told it should be over 1000 if 3d acceleration is enabled.  Where do I start?

---

### Post by lakersforce on 2007-05-04
You should start by searching the forums.

---


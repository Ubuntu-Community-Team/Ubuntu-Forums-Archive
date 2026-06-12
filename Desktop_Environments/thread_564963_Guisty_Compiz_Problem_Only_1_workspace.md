---
title: "Guisty Compiz Problem: Only 1 workspace"
date: 2007-10-01
forum: Desktop Environments
---

### Post by reflexion on 2007-10-01
Hi,

I have Compiz running, everything works fine, except that I have only 1 desktop and I cant have the cube.

I ran "ccsm", went to the general option, desktop size, H:1 V:1 #of desktop :4, but it did not worked.

I was able to get a plane to act like a  cube, but their was only one workspace... weird.

But since I applyed default back on it, I cant have it anymore.


Why do I have only one workspace (or desktop)???

thank you

---

### Post by ThrobbingBrain66 on 2007-10-01
I think you may have had your settings backward.  It's supposed to be:

Horizontal Virtual size: 4
Vertical Virtual size: 1
Number of Desktops: 1

I know it seems a little backward, but it works.

---

### Post by reflexion on 2007-10-01
hmmm, ill try this in about an hour.
thanks

---

### Post by reflexion on 2007-10-02
It worked!!!!
thanks a lot

---

### Post by vioakimi on 2007-10-02
I have exactly the same problem. How did you manage to resolve it? 
Thanks!

---

### Post by vioakimi on 2007-10-02
I'll make it more precise.

Whenever I use "visual effects" i only get one working space and I loose the "frame" around the windows. 

Any ideas? How can I get the compize settings?

---

### Post by lennartack on 2007-10-05
> **vioakimi said:**
> I'll make it more precise.

Whenever I use "visual effects" i only get one working space and I loose the "frame" around the windows. 

Any ideas? How can I get the compize settings?

Go to System - Preferences - Advanced Desktop Effect Settings - General Options - Desktop Size
Then set Number of Desktops and Vertical Virtual Size to 1 and Horizontal Virtual Size to 4

Virtual Desktops needs to be 1, and not virtual desktops, because the cube plugin in fact uses the same desktop for every side of the cube. That desktop needs to be 4 desktops wide(horizontal virtual size) to have a cube with 4 sides. If you set Virtual Desktop to 2 and Horizontal Virtual Size to four you'll have two different cubes. So then you'll have 8 desktops on two different cubes!

---


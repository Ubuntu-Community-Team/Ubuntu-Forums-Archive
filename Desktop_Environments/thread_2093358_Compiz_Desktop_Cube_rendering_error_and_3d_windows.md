---
title: "Compiz Desktop Cube rendering error and 3d windows"
date: 2012-12-10
forum: Desktop Environments
---

### Post by splifftor on 2012-12-10
Hey ppls,

so since installing 12.1 ( bare install ) and getting compiz set up, I have a strange rendering glitch with desktop cube when combining with 3d windows. at the edge of each desktop I get a mirror of the windows on the desktop. This is not completely static, it starts being mirrored on what would be the walls if I had inside cube turned on. However rotating the cube will the have the exact same mirror image duplicated on other planes and then randomly switching between them as the cube is rotated.  See image for an example . Any help would be awesome.

---

### Post by harvodan on 2013-01-15
Just in case anyone's still looking at this matter, I'm having a similar issue. Ubuntu 12.10 with 3d desktop cube too. Would anyone out there care to weigh in?

---

### Post by Frogs Hair on 2013-01-15
The only thing I notice in the CCSM that may account for a dual image is "Clone Ouput."

---

### Post by fbiazi on 2013-01-25
I has the same problem, and solved it by:
1. open CCSM;
2. Go to "OpenGL";
3. Disable Vertex buffer object.

Done.

Framebuffer object also caused some strange things here, disabled it.

WARNING: Ilumination, with is disabled here, turns my screen black when I enable it, I can't see anything. Care with it. Luckly I didn't move the mouse and was able to click again to return things to normal.

---

### Post by vonkarman on 2013-05-09
first post here, I've solved all problems since starting to use ubuntu a few months ago by just researching on the internet, unable to find a solution to this one however:

I have had this problem in 12.10 and still in 13.04

disabling the vertex buffer objext created all different graphics problems, any other solutions to this problem?

i also get other rendering faults behind the cube from the 3d windows, looks like the cascading cards when you finish solitaire

i'm using proprietary nvidia-310 drivers on a gt330m card (vaio, vpcf11m1e)

[ATTACH=CONFIG]242379[/ATTACH][ATTACH=CONFIG]242380[/ATTACH]

---

### Post by ch1mp on 2014-04-03
> **vonkarman said:**
> first post here, I've solved all problems since starting to use ubuntu a few months ago by just researching on the internet, unable to find a solution to this one however:

I have had this problem in 12.10 and still in 13.04

disabling the vertex buffer objext created all different graphics problems, any other solutions to this problem?

i also get other rendering faults behind the cube from the 3d windows, looks like the cascading cards when you finish solitaire

i'm using proprietary nvidia-310 drivers on a gt330m card (vaio, vpcf11m1e)

[ATTACH=CONFIG]242379[/ATTACH][ATTACH=CONFIG]242380[/ATTACH]

Did you ever find a way to sort this out? I can't anable 3d windows or cube deformation without things just going insane. It's usable without these, but I used to like having a cylinder with raised windows on :)

---

### Post by s.fox on 2014-04-03
This is an old thread, I would suggest you start a new one. :)

Closed.

---


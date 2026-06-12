---
title: "Unity White Screen"
date: 2011-04-30
forum: Desktop Environments
---

### Post by Didjit on 2011-04-30
Dug and can't find a resolution. Just upgraded, and at time Unity has a "white screen". What I have found is if I resize the window, I can see the actual contents of the window. For example, launch Firefox, blank white screen, resize window, contents are now displayed. If I try to resize again to make larger, white screen. This happens with all applications. 

Thought this may be the window manager, not sure if its my graphics driver etc. Any one have ideas?

Thank you.
Didjit

---

### Post by CandidMan on 2011-04-30
I'm having a similar problem. The problem seems to sort of go away if you minimise all the windows but the one you're concerned with.  
I will try reinstalling my video card drivers, switching to Ubuntu classic, and if that fails, heck I don't know switch to 10.10/Debian or something...

---

### Post by julz7 on 2011-05-01
I had the same issue using Compiz with a GeForce 6150 LE. Switching to version 173 of the Nvidia driver instead of the latest one seemed to fix the problem.

---

### Post by marty7 on 2011-05-01
Problem confirmed. Upgraded this morning and all windows turn white until they are shrunk to a certain size. The size threshold seems to differ between different applications/windows too...

[    38.765] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011

00:12.0 VGA compatible controller: nVidia Corporation C68 [GeForce 7050 PV / nForce 630a] (rev a2)

---

### Post by cellarboy on 2011-05-01
Switching to the v.173 on Nvidia drive worked for me as well.  Thanks, for the tip julz7.

Could it be the Recommended Nvidia driver is the problem?

---

### Post by AldenIsZen on 2011-05-20
Switching to 173 worked for me as well. I was ready to start trashing Unity, but if it is a Driver issue, then hey, what can you say? At any rate, as long as it works then I am happy. I will try to report back if I still have any issues, but so far so good.:popcorn:

---

### Post by openam on 2011-07-24
I've been upgrading my laptop since about Ubuntu 8.10.  I figured it was time to start clean. I have 11.04 running on my desktop in the basement, and it was working fine.  After I wiped my computer and upgraded, I was getting pretty ticked about this issue.

I tried to disable animations in Compiz, but that didn't seem to help. Switching the driver back to 173 is working for me as others have reported.

---

### Post by grahams on 2011-07-28
Still a problem with nvidia's 275.19 driver

Trying 173

---

### Post by miroi on 2011-09-14
For me as well -- return to nvidia-173 helped. No "nvidia-current", but good, old nvidia-173  ! 

M.

---


---
title: "Workspace is too large?"
date: 2018-08-19
forum: Desktop Environments
---

### Post by Robbyx on 2018-08-19
Instead of 1920x1080 wmctrl shows:

robins@robins-desktop:~$ wmctrl -d
0  * DG: 3840x1080  VP: 0,0  WA: 0,0 3840x1042  Workspace 1
1  - DG: 3840x1080  VP: N/A  WA: 0,0 3840x1042  Workspace 2
2  - DG: 3840x1080  VP: N/A  WA: 0,0 3840x1042  Workspace 3
3  - DG: 3840x1080  VP: N/A  WA: 0,0 3840x1042  Workspace 4
4  - DG: 3840x1080  VP: N/A  WA: 0,0 3840x1042  Workspace 5

When opening apps they usually  stretch across my 2 screens. How do I ensure that a new app just fills one monitor?

---

### Post by TheFu on 2018-08-20
It is dependent on the GPU driver and tools used to manage those.  nvidia and amd have setting controller apps.  With intel iGPUs I use lxrandr.
My nvidia GPU is very, very old, but the name of the program to manage it 5+ yrs ago was nvidia-settings.

---

### Post by Robbyx on 2018-08-21
Thank you for your reply. I think it is now working better.

---


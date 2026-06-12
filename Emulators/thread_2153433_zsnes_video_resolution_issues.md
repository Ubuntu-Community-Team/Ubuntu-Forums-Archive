---
title: "zsnes video resolution issues"
date: 2013-06-11
forum: Emulators
---

### Post by Shaffness on 2013-06-11
To get right into it. I have been trying to get ZSNES to go to full screen but when I switch the resolution it crashes immediately I have figured out that the problem is with any of the OpenGL resolution modes. even the low res modes cause ZSNES to have a segmentation fault and crash. 

Does anyone know of a solution to stop OpenGL from causing ZSNES to crash on me. There is a non-OpenGL full screen mode available but the resolution is really low and I would prefer to use a higher res if I could. The help would be much appreciated.

---

### Post by Shaffness on 2013-06-11
I was fooling around and found that if I set ZSNES to full screen I can use it but if I close it and try to run it again it crashes. If I want to open it again I have to open it in video mode 2 which is a low res windowed mode and then set the full screen resolution again each time I want to play anything. This is a very odd problem.

---


---
title: "OpenGL doesn't work, /dev/nvidia* has buggy permissions"
date: 2009-02-23
forum: General Help
---

### Post by evouga on 2009-02-23
Whenever I run an OpenGL application, hardware rendering is disabled because the files /dev/nvidia* (nvidiactl and nvidia0) are owned by root and have read-only permission. If I sudo chmod them, I am then able to run OpenGL with hardware rendering, but the permissions reset every time I reboot.

I edited /etc/udev/rules.d/40-permissions.rules to add MODE="0666", as follows:

KERNEL=="nvidia*",                      GROUP="video", MODE="0666"

However this did not work.

1. Why are the nvidia devices being assigned wrong permissions?
2. Why doesn't the above udev fix work?
3. What can I do permanently fix the problem (I can probably write a script that chmods every time I reboot, but that is a hack I'd like to avoid.)

---

### Post by 5dollafootlong on 2009-02-23
how did you install your drivers? did you compile them 
from source or use the restricted driver utlity? and what 
version driver do you have 177? also what card to do you have?

---

### Post by 5dollafootlong on 2009-02-23
also what proram/s are giving you this problem? linux native?
or wine implemented? sorry for so many question but it gives us a better idea of what is the problem

---

### Post by evouga on 2009-02-23
I have 177.82 installed through the restricted drivers dialog box.

According to xorg.conf the card is "nVidia Corporation NV18GL [Quadro FX 550]."

The program I am trying to run I compiled myself using freeglut3-dev. But the problem appears for any OpenGL application: running glxinfo shows direct rendering: no until I chmod the /dev/nvidia*, at which point it switches to direct rendering: yes.

---

### Post by evouga on 2009-03-09
Nobody? I'm now chmodding after every reboot, which works around the problem, but isn't a very satisfactory solution...

---

### Post by evouga on 2009-04-24
If anybody searches the forums with this same problem: the user account I was using was not a member of the "video" group; adding this group resolved the issue.

---

### Post by griffjon on 2011-08-13
my /dev/nv* devices are being assigned to the root user/group; I'd love to have them auto-assign to the video group.  Tried udev, but that does not seem to be being used, so the rule isn't applied.

---


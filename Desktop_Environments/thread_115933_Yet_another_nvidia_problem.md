---
title: "Yet another nvidia problem"
date: 2006-01-11
forum: Desktop Environments
---

### Post by stack445 on 2006-01-11
I've look around, in the how to for nvidia, but i dont see any anwser to my problem. I've got this error message when i enable the nvidia driver and restart X :
Nvidia kernel module is 1.0.7174 and X module is 1.0.7667. 

How do i actually fixed this mismatch ? I'm runnig 2.6.12-10-k7. I"ve try many different thing, like automatix, and installing the download driver from nvidia. To be quite honnest i lost track. I dont care what driver to use, i just want 3d support. Right now im on the nv driver in my xoer.conf, and i have the load glx line put in, but when i try to run 3d stuff i get : 
maxime@cortex:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
maxime@cortex:~$

Any help is appreciated 

thx

---

### Post by jerrykenny on 2006-01-11
Its odd, I wonder if you've had a kernel update, ( since installation) but you havent had a corresponding nvidia driver update?

Can you go into synaptic, mark the nvidia driver for "complete" removal (just to make sure any old modules are removed) and then reinstall nvidia . . . .

---


---
title: "x server problem, New install"
date: 2006-01-13
forum: General Help
---

### Post by Age One on 2006-01-13
Hi, I just installed 5.10 on my machine. When the system boots to the GUI the screen locks up and turns light blue with a bunch of wierd lines that streek accross it. I tryed installing both x86 and x86-64 on the machine, same results both times. then I tryed the live CD's both had the same outcome.

My machine is a AMD 64 3400+, ATI 9250 video card. 

I had suse 9.3 on this machine before and ran the card fine (without 3d) and would have a simmalir problem if I attempted to run 3D. I *think* its trying to run the 3D drivers, either that or it just plain hates my card. 

can you help me how to edit my x.org config file.. I want to set it to a regular driver untill I can figure out how to make it work better. unless theres a trick to making it work correctly now thats easier.

I'm having to go back and forth between Linux and xp, so bare with me a bit

Thanks
-Adrian

---

### Post by Age One on 2006-01-13
figured it out, replaced ATI with VESA and deleated "load GLX" now it works.

---

### Post by newclique on 2006-01-14
You won't get 3D acceleration with VESA, though. I followed the upgrade guide on this website for installing the latest ATI drivers and it worked but I still have a problem with glx not allowing X to start. When I removed glx, it started for me and now I have the latest ATI drivers supporting my 9250.

---

### Post by Age One on 2006-01-14
[QUOTE=newclique]You won't get 3D acceleration with VESA, though. I followed the upgrade guide on this website for installing the latest ATI drivers and it worked but I still have a problem with glx not allowing X to start. When I removed glx, it started for me and now I have the latest ATI drivers supporting my 9250.[/QUOTE]

I changed the driver from vesa to radeon this morning and it looks great. I'll figure out 3D later, its not all that important to me. I'll work on it when I wanna run a cooler 3d screen saver. but now I still have a bunch of other stuff to do. I just wanted to see what I was doing before anything else. :smile:

---


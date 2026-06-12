---
title: "how load modules at boot time with additional parameters"
date: 2009-05-10
forum: General Help
---

### Post by menschmeier on 2009-05-10
To get my webcam work it had to compile the driver and load the module. This is working fine but the images are upside-down. So I have to use the additional parameter vflip=1 when I load the module. Using modprobe this is working but if I add the line 

sn9c20x vflip=1 

in /etc/modules resp. /etc/modules.autoload.d/kernel-2.6 the parameter vflip=1 wil be ignored. What is the right way to load a module at boot time with additional parameters?

---

### Post by nzadLithium on 2009-05-10
I'm not sure how to do it using the /etc/modules (I've never managed to make anything work in that :S), but how I load modules is add them to /etc/rc.local

so for yours I would add to /etc/rc.local
rmmod sn9c20x
modprobe sn9c20x vflip=1

this removes any instance of the sn9c20x module already running, then starts a new one with your parameters. It should be possible to achieve via /etc/modules, but I have no idea how to make that file do anything :S

---


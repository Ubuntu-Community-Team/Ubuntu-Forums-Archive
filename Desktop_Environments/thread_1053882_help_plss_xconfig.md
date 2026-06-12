---
title: "help plss xconfig"
date: 2009-01-29
forum: Desktop Environments
---

### Post by jlo-linux on 2009-01-29
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

whats the prob?? 

and how can i fix that?? help plss

---

### Post by oaqster on 2009-01-29
can you provide some more info on what exactly is going on? what vga card you have installed? did you recently put it in? has it ever worked? is this a fresh install of the OS? what version of ubuntu you have? etc.

most nvidia cards will simply work with the default restricted driver that comes with ubuntu just goto System -> Administration -> Hardware Drivers and enable what comes up in the list.  For some GPUs you might actually need to figure out which one you need & download/install it from nvidia's website.  alternatively you can download & install Envy/EnvyNG (which ever is applicable for you), it will detect, download & install the appropriate driver for your card given that it has either nvidia or ATI.

hope this helps
- oaqster

---


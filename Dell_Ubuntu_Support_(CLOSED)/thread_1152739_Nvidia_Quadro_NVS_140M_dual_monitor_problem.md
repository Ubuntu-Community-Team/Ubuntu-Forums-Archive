---
title: "Nvidia Quadro NVS 140M dual monitor problem"
date: 2009-05-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vreemde eend on 2009-05-08
Hi all,

I've got a Latitude D830 with Nvidia Quadro NVS 140M. Ever since I use the 180.x driver, I can't get my dual monitor setup to work. If I attach an external monitor and set it up in twinview and position it to the left, everything goes black (I can only see the mouse pointer). I have to restart X to get things back to normal. If I position the external monitor to the right, I have my desktop on the external monitor, but the laptop screen goes black. Things get back to normal after a minute. 

Though, if I set up the external monitor in twinview and disable my laptop screen, everything goes fine. But then I'm only using the external screen.

I'm now running 9.04 64bit, but had the same issue with 32 bit 8.10 and the 180.x driver. I upgraded the driver to 180.53, but still have the same problem. In the nvidia-settings both displays have the same display number: 0. That might be the issue? Any ideas?

kind regards,

pieter

---

### Post by vreemde eend on 2009-06-12
Solved the problem by manually installing the latest stable driver (185.18.14) as described here: [http://ubuntuforums.org/showthread.php?t=990978&highlight=Quadro+NVS+140M](http://ubuntuforums.org/showthread.php?t=990978&highlight=Quadro+NVS+140M)

---


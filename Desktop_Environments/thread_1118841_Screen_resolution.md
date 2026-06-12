---
title: "Screen resolution"
date: 2009-04-07
forum: Desktop Environments
---

### Post by Superdude_123 on 2009-04-07
I have two problems:

When I first get the screen to log in to the system, my resolution is way off, and I'd like to change it to 1024X768. How do I do this?

Also, under user Y, every time I log in, the screen resolution is off, how do I change it to be by default 1024x768 when the user doesn't have access to all rights on the system ?

---

### Post by nebileix on 2009-04-07
pls indicate ur graphic card and post your xorg.0.log and dmesg in order for others to find out wats the problem.

---

### Post by webkris on 2009-04-07
I don't know what your hardware setup is, but I found that I wasn't saving my xorg.conf file as root or with sudo.

What would happen to me is: I would run nvidia-settings from administration and set everything up. Get the resolution of both my monitors set, and then upon restart or log-off / log-on my resolution would go back to crap... What I needed to do is run nvidia-setting from a terminal with sudo.
Hope that helps.

- Kris

---

### Post by Ben_neB on 2009-04-07
I had the same problem, and the solution was as webkris describes it. I was running 8.10 with the Nvidia 8600. I don't know what you've got, but that's the first thing I'd try.

---

### Post by andrea000 on 2009-04-09
sorry messed up

---

### Post by andrea000 on 2009-04-09
I had the same problem with 8.04 and the same card had to 
use [envyng]("http://albertomilone.com/nvidia_scripts1.html") to fix mine.i dont know if this will help you but it 
might.Saving xconfig as root may also be a solution.

---


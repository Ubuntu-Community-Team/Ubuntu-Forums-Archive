---
title: "Mouse only works after restarting X"
date: 2008-08-05
forum: Desktop Environments
---

### Post by mwolthers on 2008-08-05
When I boot my Kubuntu Hardy x86 32bit system, my mouse doesn't work. When I then press ctrl-alt-backspace to restart X, everything works fine. I don't want to keep doing this so I'm trying to figure out what's wrong.

Problem has existed for a couple of weeks, after an apt-get upgrade, I think there were some xserver packages upgraded at that time, but I'm not sure.

My mouse is a Logitech MX400 which has always done it's job perfectly well on Kubuntu. I don't suppose the problem is with the mouse, I expect the problem to be with the new X config that Hardy uses, but I only know xorg.conf for configuration. Has anybody got any tips where to look for errors?

---

### Post by sebbss on 2008-08-06
You can look in the xserver log file to see what is the problem. But i don't know exact where it is kept.

---

### Post by mwolthers on 2008-08-22
I solved the problem. Pointing out the physical location of my mouse did the trick. The logs where quite strange, didn't quite understand what was actually happening. So to be short: this solution works, even if I don't know why it does...

---


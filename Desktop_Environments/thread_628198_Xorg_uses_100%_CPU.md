---
title: "Xorg uses 100% CPU"
date: 2007-12-01
forum: Desktop Environments
---

### Post by hyperair on 2007-12-01
I'm using Ubuntu Gutsy, running Compiz Fusion and I've noticed this problem for quite some time already. When Compiz Fusion is running, and there's a window which changes its title quite often, such as the DownloadThemAll manager for Firefox, the Xorg CPU usage goes all the way up to consume whatever remains of the CPU (Firefox consumes the rest).

This has happened to me before using Ubuntu Feisty, and Opera. Opera with its download tab open will change its title frequently to reflect the speed at which it is going, and how much time remains. Xorg will then proceed to eat my CPU.

Is there anything that can be done to fix this?

---

### Post by TeaSwigger on 2007-12-01
What are the specs of the computer? Compiz takes a lot of resources. Could also be a video driver issue?

---

### Post by hyperair on 2007-12-01
CPU:2.66GHz single core Intel P4 No HT.
GPU:nVidia GeForce4 MX 440
Driver: nvidia-glx 1:1.0.9639+2.6.22.4-14.10
Xorg uses 10% CPU or below if there are no windows with rapidly updating titles.

---

### Post by TeaSwigger on 2007-12-01
What does /etc/X11/xorg.conf say is being used for graphics driver? That is, does it specify nvidia.

EDIT: adding a stray thought: does glxgears run smoothly? To test, enter the word glxgears in a terminal and let it run for 30 secs or so. Movement should be uniform and smooth, frames per second fairly steady, and it should not cause a 100% cpu condition.

---


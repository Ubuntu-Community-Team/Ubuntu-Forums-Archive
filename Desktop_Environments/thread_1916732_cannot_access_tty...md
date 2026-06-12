---
title: "cannot access tty.."
date: 2012-01-28
forum: Desktop Environments
---

### Post by memstick on 2012-01-28
Hey,

I'm working on an NVIDIA cuda project and have to work in Ubuntu 10.10 for the time being. I've just attempted installing Ubuntu and NVIDIA's cuda development driver, a setup working fine on an XPS laptop I've been using until now. The problem is that I'm not at all able to enter a TTY terminal. The system boots fine after installation, but when I try to enter a tty, the mouse pointer disappears and apart from that the screen stays exactly the same. I am able to go back to the desktop environment successfully. 

This represents a problem because you need to stop gdm and xserver in order to be able to build and install the proprietary nvidia driver. I have tried installing the driver from the package system (nvidia-current or something) and this actually solves the problem with the ttys, but then it creates errors later when I have attempted to install the development driver from tty.

My computer has two gtx 8600 cards in sli plus an integrated nvidia nforce 750 on the motherboard. 

Is there anywhere I might be able to get some logs for the tty problem, or anything anyone can think of that might help?

---

### Post by memstick on 2012-01-30
I solved this problem by ssh'ing to my machine and shut down gdm from there. 

I noticed that after nouveau was removed, I could switch to other ttys again.. So the problem must've been there..

---


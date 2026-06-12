---
title: "can't get texmaker to run"
date: 2007-06-13
forum: Education &amp; Science
---

### Post by ManoloM on 2007-06-13
I'm using feisty on a 64-bit machine. I used synaptic to install texmaker and it appears on the gnome menu but I can't get it to launch!

In the command window I type: texmaker

but instead of opening the window I get: Segmentation fault (core dumped)

What can I do?

---

### Post by kleeman on 2007-06-13
Known bug

[https://bugs.launchpad.net/ubuntu/+source/texmaker/+bug/88891](https://bugs.launchpad.net/ubuntu/+source/texmaker/+bug/88891)

Workarounds:
1) Run as root: 

gksudo texmaker

2) Works from the enlightenment desktop (not kde or gnome)
3) deinstall and install the edgy version

Odd bug,,,

---


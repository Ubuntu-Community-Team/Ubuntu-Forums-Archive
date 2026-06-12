---
title: "Blank screen + Mouse after Login"
date: 2009-05-02
forum: General Help
---

### Post by bruno.eberhard on 2009-05-02
Hi there,

I've googled a lot but havnt found a solution or the matching thread for my problem.

I've installed ubuntu 9.04 x64 on my Dell 420 XPS (ATI Radeon HD 3870, Intel Q9400). Everthing went fine, amazing fast the nice login screen appeared but after logging in the screen kept blank except for the mouse pointer which was visible and moveable.

What should I do? How could I get more information about whats wrong? Would the dell-ubuntu edition help?

Greetings

---

### Post by CarlosUtah on 2009-05-04
I had the same problem. I could not fixed it and I had to reinstall. However, after I reinstalled I glooged & found somebody with same problem & a solution I did not try.
Here is that particular solution:
Ctrl+alt+F1 to open a terminal
log in as root
type sudo apt-get install ubuntu-desktop
then reboot the system or Alt+F7
That should reinstall missing packages.
That worked for that guy!!!

What went wrong in my case? when removing evolution using synaptic package  Manager some critical apps were also removed. I found similar cases

---

### Post by bruno.eberhard on 2009-05-08
Thanks carlos,

in my case it was a fresh installation. Later I tried the 32bit version (not the x64) and that version works.

Now I don't know which package causes the problems in the x64 version.

Greetings

---


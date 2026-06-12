---
title: "Ubuntu 12.04 using gnome-shell"
date: 2012-06-15
forum: Desktop Environments
---

### Post by metallica1973 on 2012-06-15
I just removed the entire unity unity-2d gnome desktop and installed the barebones essentials "gnome-shell" and all is working fine. The problem that I have noticed seems to be with permissions. These are the things that I cannot do:

1 -(tty access)

control-alt-f1,f2,and etc.

2 - customize my desktop

3 - If I attempt to sudo /etc/init.d/gdm stop, it hangs(need add an NVIDIA video driver that require me to stop the GUI), I believe because of some type of security thing going on. 

4 - I can successfully mount the root partion using single mode but when I attempt to change the runlevel from 1 to 3:

<root>init 3

and I attempt to login as a standard user, I simply cannot.

help

---


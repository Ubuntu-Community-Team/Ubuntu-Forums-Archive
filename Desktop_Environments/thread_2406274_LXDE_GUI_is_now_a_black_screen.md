---
title: "LXDE GUI is now a black screen"
date: 2018-11-18
forum: Desktop Environments
---

### Post by steve234 on 2018-11-18
Hi there,

I'm having some difficulties with x11vnc and LXDE on a LUbuntu box. I've posted in general help, but think this sub-forum is probably the best place for the query as on further research it seems to be an LXDE issue. I have asked to have the original thread moved.

In summary:

- I was trying to run a monitor-less setup using VNC to occasionally do things where I needed a GUI. That did not work and plugging in a monitor also does not work (both just show black).

- I can see (using htop over ssh) that lightdm greeter has fired up, so perhaps I'm not getting the picture to the monitor due to changing xorg.conf settings.

- more details are in original thread below:

[https://ubuntuforums.org/showthread.php?t=2406189](https://ubuntuforums.org/showthread.php?t=2406189)

---

### Post by steve234 on 2018-11-19
Solved - xorg.conf deleted.

---


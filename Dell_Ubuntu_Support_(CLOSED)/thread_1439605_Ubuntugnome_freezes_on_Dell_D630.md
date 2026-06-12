---
title: "Ubuntu/gnome freezes on Dell D630"
date: 2010-03-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tendonstrength on 2010-03-26
I have a Dell D630 laptop with Ubuntu 9.10, and I am having trouble with it freezing in certain situations. By freezing I mean that you can move the mouse around the desktop, but you can't left click anything (right clicking works). The desktop for the most part does not respond to keyboard input, however I can use control-alt-delete to shutdown reboot (although I have to wait the default 60 seconds instead of being able to choose an option).

I only have Ubuntu 9.10 on this machine and I use it most of the time with no problem. 90% of the time the laptop is docked and using a wired ethernet connection. I have the freezing problem only when I am both undocked and connected to a wireless network. 

Any insight would be appreciated. This is an inconvenience, but for the most part I have been very happy with Ubuntu.

---

### Post by coffeeaddict22 on 2010-03-28
Hi,
In a terminal, typing ```
xev
```will give you a wee box you can test for mouse events reaching HAL.  It's not your mouse, is it?  Have you tried using a different one?

---


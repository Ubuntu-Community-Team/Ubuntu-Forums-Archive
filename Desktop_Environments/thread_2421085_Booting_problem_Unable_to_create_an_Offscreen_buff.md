---
title: "Booting problem: Unable to create an Offscreen buffer"
date: 2019-06-16
forum: Desktop Environments
---

### Post by larry90 on 2019-06-16
Hello everyone, 

Sadly I have a new problem with my Ubuntu and i can't manage to boot it normally. Today after a software update and a reboot I found out that I get a neverending loading screen after i chose to boot Ubuntu; I can still login in Ubuntu if i pick "advanced options --> recovery  mode --> normal start.
 At first i was thinking it was a NVIDIA driver problem so I reinstalled them, but sadly the problem was still there; than, since i saw NVIDIA persistence daemon couldn't load i tried to fix it with this guide ([https://askubuntu.com/questions/979259/nvidia-persistence-daemon-continuously-starting-and-stopping-in-syslog/1138052](https://askubuntu.com/questions/979259/nvidia-persistence-daemon-continuously-starting-and-stopping-in-syslog/1138052)) but the problem was still not fixed.... moreover while checking syslog i found this error:
message repeated 71 times: [ clutter-offscreen-effect.c:202: Unable to create an Offscreen buffer]

Can anyone help me with my problem? Thanks in advance!

Edit: I managed to "solve" my problem by disabling the autologin... now i can boot normaly but I have to insert my password... any idea how to avoid this part?

---


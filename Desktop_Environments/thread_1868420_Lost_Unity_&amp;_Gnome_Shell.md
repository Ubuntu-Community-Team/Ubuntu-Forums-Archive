---
title: "Lost Unity &amp; Gnome Shell"
date: 2011-10-24
forum: Desktop Environments
---

### Post by badactress on 2011-10-24
Hi,

I'm running Ubuntu 11.10 64bit on Asus 1201N.

Everything was fine until I installed gnome-shell. I rebooted and at the login, the only desktop options I have are gnome classic and gnome classic (2d). 

Re-installing video drivers and both unity and gnome shell hasn't worked. Removing gnome shell didn't help. 

Running unity_support_test shows:

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: ION/PCI/SSE2
OpenGL version string:  3.3.0 NVIDIA 280.13

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

I'm a bit baffled now! I've tried everything I can think of.

Can anybody suggest a next step? To be honest I'm growing to like Unity, so gnome-shell isn't essential. If I can just get Unity back I'd be happy.

Thanks in advance for any advice.
Norman

---

### Post by badactress on 2011-10-24
Oh no! My problem is slipping onto page 3 of the forum with no replies :(

I guess a fresh install and no more trying anything silly like installing Gnome shell is the answer! :)

---

### Post by ubu_dynamite on 2011-10-24
```
sudo apt-get install ubuntu-desktop gnome-shell
```
that should install unity, gnome-shell and gnome-session-fallback

---

### Post by badactress on 2011-10-24
Ubu_dynamite thankyou so much! Worked perfectly.. I have Unity and Gnome shell. You Rock! :o)

---


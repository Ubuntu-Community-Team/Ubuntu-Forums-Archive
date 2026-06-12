---
title: "VNC + tensorflow: giving more resources to tensorflow and less to the desktop"
date: 2018-10-05
forum: Desktop Environments
---

### Post by virilo on 2018-10-05
I'm using a 1080TI on Ubuntu 16, and I'd like to give the most GPU resources to tensorflow/keras instead of the desktop.

I use 50% times just VNC access, 49% just ssh and 1% real desktop.

I installed gnome to be used by VNC server.

When I'm training a model, I've the feeling that it's not using the whole memmory.

I've never reached the 11000MB limit, but sometimes it complaint because tensorflow cant allocate a little amount of memory

It's alwasy using at max something like 10760 / 11169 MB:

[0] GeForce GTX 1080 Ti | 64'C,  61 % | 10760 / 11169 MB | python/4668(10677M) Xorg/1496(70M)

Is it reserving memory for gnome?

Is there any way to use all the GPU memory for CUDA?

Thanks in advance.

---


---
title: "w3m inline image support in console ?"
date: 2006-10-04
forum: Desktop Environments
---

### Post by Kompressor on 2006-10-04
This is not really related to Ubuntu desktop but I haven't found the right place to post in, sorry if that bothers.

I'm using Ubuntu Dapper server and have installed w3m-img for inline image support. According to apt-cache, it is supposed to be able to display inline image in X terminal and 'Linux frame buffer'.

I'm not sure about frame buffer support (out of the box) in Ubuntu so I checked a couple of things:
 - lsmod returned 'vesafb' and 'fbcon' modules loaded.
 - dmesg said 'Console: switching to colour frame buffer device 128x48' and 'fb0: VESA VGA frame buffer device'.

From my limited understanding of Linux, that is necessary to activate the console frame buffer. I added 'vga=792' at boot time for higher resolution.
I've built LFS and have tried building frame buffer support into the kernel, but I've got no idea of how to activate this if the fb was built as a module.

A kernel rebuilding will be performed if necessary, other solutions are prefered though.
It would be of great help to me if some directions/links are suggested.

Thanks.

---

### Post by encompass on 2006-11-06
I think that only works in X but if you get it to work in console cool.  You could just try emailing the programmers.

---


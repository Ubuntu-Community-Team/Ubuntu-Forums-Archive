---
title: "3d Acceleration"
date: 2006-01-06
forum: General Help
---

### Post by linuxfan128 on 2006-01-06
While trying to figure out why i was getting so slow FPS i did glxinfo it came with this output.
[http://home.insightbb.com/~chrisbaird2/glxinfo.txt]("http://home.insightbb.com/~chrisbaird2/glxinfo.txt")

What do i do to enable direct rendering here is my xorg.conf

[http://home.insightbb.com/~chrisbaird2/xorg.txt]("http://home.insightbb.com/~chrisbaird2/xorg.txt")

xorg.o.log
[http://home.insightbb.com/~chrisbaird2/xorg.o.log.txt](http://home.insightbb.com/~chrisbaird2/xorg.o.log.txt)

---

### Post by aclaunch on 2006-01-06
I don't know the Intel i810 chipset but there are two warnings shown in you xorg.log file:

(**) I810(0): DRI is disabled because it runs only at 16-bit depth.

(WW) I810(0): Direct rendering disabled

"What is DRI?
The Direct Rendering Infrastructure, also known as the DRI, is a framework for allowing direct access to graphics hardware in a safe and efficient manner. It includes changes to the X server, to several client libraries and to the kernel. The first major use for the DRI is to create fast OpenGL implementations." (from Gentoo documentation)

You might try setting you depth to 16-bit and see if that helps.

Good Luck,
Alan

---

### Post by linuxfan128 on 2006-01-06
Thanks for the help

---


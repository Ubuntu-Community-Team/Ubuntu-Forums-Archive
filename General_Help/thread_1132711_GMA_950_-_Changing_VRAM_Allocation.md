---
title: "GMA 950 - Changing VRAM Allocation"
date: 2009-04-22
forum: General Help
---

### Post by shade11 on 2009-04-22
I am currently using an Intel GMA 950 Graphics Accelerator. My BIOS does not allow me to change the amount of RAM I want allocated to my GPU. I heard something about being able to change the amount of VRAM allocated using the Intel utilities in Windows. I do not run windows at all, is something like this possible under Linux.

---

### Post by zevans on 2009-04-22
There are ways to change MTRR setup in later kernels, that might be a good place to look?

Lots of links for further reading in this blog post:
[http://www.tikirobot.net/wp/2009/03/01/fixing-mtrrs-on-linux/](http://www.tikirobot.net/wp/2009/03/01/fixing-mtrrs-on-linux/)

I think it would be wise to check if you have the bug it talks about first though :-)

Come to think of it it would be nice for me if I could reduce the usage when I know I'm going to be using Office all day, and then up it for gaming...

---

### Post by eldragon on 2009-04-22
from "man intel"
```

       VideoRam integer
              This  option  specifies  the  amount of system memory to use for
              graphics, in KB.

              The default is 8192 if AGP allocable memory is < 128  MB,  16384
              if  <  192  MB, 24576 if higher. DRI require at least a value of
              16384. Higher values may give better 3D performance, at  expense
              of available system memory.

```

i hope its what you are looking for

EDIT: leaving xorg to do its thing, i get from /var/log/Xorg.0.log:
```

$  cat /var/log/Xorg.0.log | grep VideoRam
(==) intel(0): VideoRam: 262144 KB

```

---


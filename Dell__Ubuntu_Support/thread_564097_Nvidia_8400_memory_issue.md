---
title: "Nvidia 8400 memory issue"
date: 2007-09-30
forum: Dell  Ubuntu Support
---

### Post by dardack on 2007-09-30
So I just got my new Dell Inspiron 1720 with nvidia 8400, everything works great.  I do have a slight issue i would like to solve.  Dell and the bios says the GPU memory is 128mb.  nvidia-settings says i have 256mb.  If i run grep -i nvidia /var/log/Xorg.0.log i get:
(--) NVIDIA(0): Memory: 262144 kBytes

If i run lshw i get:
 description: VGA compatible controller
...
 size: 64MB
...

Which is the correct amount?

---

### Post by silverdarkness on 2007-10-01
You probably have a 8400 gs card which has turbocache. I believe it has 128mb of dedicated memory plus a certain amount of shared memory. The shared memory can vary depending on the driver you are using.

---


---
title: "install doom3 on 12.04"
date: 2012-05-13
forum: Gaming &amp; Leisure
---

### Post by ahso4271 on 2012-05-13
Hi
after seeing this:
[http://www.lgdb.org/game/cerberon](http://www.lgdb.org/game/cerberon)
I decided to install my old doom3 but get:

michael@michael-ubuntu:~/Downloads$ sudo ./doom3*304*
Verifying archive integrity... All good.
Uncompressing DOOM 3.............................................................................................
./setup.sh: 192: ./setup.sh: /home/michael/.setup2968: not found
michael@michael-ubuntu:~/Downloads$ 

I've downloaded the installer 1304...so what's going on here?
Thanks

---

### Post by ahso4271 on 2012-05-13
on 64Bit that helped:

sudo apt-get install ia32-libs

but now I get:

----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
dlopen(libGL.so.1)
idRenderSystem::Shutdown()
signal caught: Segmentation fault
si_code 1
Was in fatal error shutdown: Unable to initialize OpenGL
Trying to exit gracefully..
michael@michael-ubuntu:~$

---

### Post by ahso4271 on 2012-05-13
With another app I got:

10$ ldd X*86 
    linux-gate.so.1 =>  (0xf7799000)
    libGL.so.1 => not found
...

So I reinstalled the Nvidia driver from Software Center and it works. 
I guess the newest driver has this bug. If it wouldn't be a pain in the *** 
to report bugs I'd do...thanks for reporting this bug, folks.

---


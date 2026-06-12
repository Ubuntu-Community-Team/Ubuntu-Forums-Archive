---
title: "Help needed with compiling programs requiring OpenGL"
date: 2005-04-23
forum: Gaming &amp; Leisure
---

### Post by Skye on 2005-04-23
Here's the problem:  Whenever i try to compile a program that requires openGL, (such as Quake2 or vpython)  the configure script will fail when it reaches the point of detecting openGL, mesa, and gtkglarea.  This is the error that poped up with vpython- until this point, the configure script worked well:

checking GL... no
checking GL with threads... no
checking Mesa... no
checking Mesa with pthreads... no
configure: error: gtkglarea is required on Unix-like systems

Now, i've spent about two days looking for every single mesa, openGL, and gtkglarea package ever created.  I've re-installed all of them multiple times, and the configure scripts stil fail.

What's wrong? I'm running Hoary i386 with an BFG 6800 GT OC.  I have the nvidia drivers installed and running.  I DIDN'T get the drivers from apt, though, i used the drivers direct from nvidia's site.  This may have been a mistake, i'm not sure.

What's strange is that Unreal Tournament 2004 works perfectly, as do games like Call of Duty and Half-life 2, running from within cedega.  

Any help would be much appreciated.  Up to this point, i've been able to solve my problems by looking through these forums or on google, but this time, i couldn't find any info about this problem. Thanks!

---

### Post by gil-galad on 2005-04-23
Try 
sudo apt-get build-dep quake2

---

### Post by Skye on 2005-04-24
Getting the source didn't work because my sources.list didn't include a URI that had the source of quake2, but i did discover the source of the openGL problem- i needed the nvidia-glx-dev package.  When I installed the drivers directly from nvidia, i didn't get that package, and hence, compiling failed.

Thanks for the help!

---

### Post by kkith on 2005-04-24
[QUOTE=Skye]
What's wrong? I'm running Hoary i386 with an BFG 6800 GT OC.  I have the nvidia drivers installed and running.  I DIDN'T get the drivers from apt, though, i used the drivers direct from nvidia's site.  This may have been a mistake, i'm not sure.

What's strange is that Unreal Tournament 2004 works perfectly, as do games like Call of Duty and Half-life 2, running from within cedega.  
[/QUOTE]
Sounds like the shared libraries are in the correct place since UT2004, et al. are using them.  My first guess is that you don't have the openGL header files (gl.h, glx.h, etc) in the correct place.  Mine are in /usr/include/GL.  Check there to see if you have these files, if not look in /usr/local/include/GL, if you do find them in /usr/local/include/GL, a quick fix would be to create a symlink.

ln -s /usr/local/include/GL /usr/include/GL, but this is considered a hack by some.

If you can't find ANY of these files, then maybe try (if you haven't yet) installing the package (I found it through 'synaptic') xlibmesa-gl-dev.

If I recall correctly, these header (.h) files were installed when I installed the Nvidia drivers through Ubuntu's  repository.  Maybe the first thing you should try is installing the nvidia drivers from ubuntu?

Good luck.

---

### Post by francisco_athens on 2006-10-09
if you get OpenGL not found errors you should install xorg-dev package.

---


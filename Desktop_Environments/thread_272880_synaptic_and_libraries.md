---
title: "synaptic and libraries"
date: 2006-10-07
forum: Desktop Environments
---

### Post by vanth13 on 2006-10-07
hello . I have an application with this dependancy list:

libGLU.so.1 => /usr/lib/libGLU.so.1
libGL.so.1 => /usr/X11R6/lib/libGL.so.1
libXmu.so.6 => /usr/X11R6/lib/libXmu.so.6
libXext.so.6 => /usr/X11R6/lib/libXext.so.6
libX11.so.6 => /usr/X11R6/lib/libX11.so.6
libstdc++.so.6 => /usr/lib/libstdc++.so.6
libm.so.6 => /lib/tls/libm.so.6
libgcc_s.so.1 => /lib/libgcc_s.so.1
libc.so.6 => /lib/tls/libc.so.6
libtiff.so.3 => /usr/lib/libtiff.so.3
libjpeg.so.62 => /usr/lib/libjpeg.so.62
libz.so.1 => /usr/lib/libz.so.1
libthread.so.0 => /usr/lib/libthread.so.0
libdl.so.2 => /lib/libdl.so.2
libXt.so.6 => /usr/X11R6/lib/libXt.so.6
libSM.so.6 => /usr/X11R6/lib/libSM.so.6
libICE.so.6 => /usr/X11R6/lib/libICE.so.6
/lib/ld-linux.so.2 => /lib/ld-linux.so.2

but I can't find this stuff on synaptic running... what can I do? does it mean I can't runn this app on ubuntu?

please help me! I deserve this app for my thesis!!! I tried too on mac osx with fink ... but can't find this libs... anyway

---

### Post by aysiu on 2006-10-07
What's the app?

---

### Post by vanth13 on 2006-10-07
here's the link  :

[http://perception.inrialpes.fr/~Franco/EPVH/](http://perception.inrialpes.fr/~Franco/EPVH/)

vision library... very damn urgent for me!!! 

I'm new to linux. I started using it for the great flexibility in the research field... and I'm loving it!!!

but I'm very bad.... I have a lot of things to learn...

thk..

---

### Post by vanth13 on 2006-10-07
don't know if it's importan... but I'm running ubuntu on Apple macbook under parallels...

I guees this is not the problem in this case..

---

### Post by aysiu on 2006-10-07
Well, I'm not expert at compiling from source, but generally, you do ```
./configure
make
sudo make install
``` after installing *build-essential*. In this case, though, that doesn't work. For ```
./configure
``` you get *bash: ./configure: No such file or directory*. For ```
./reconstruct
``` you get *./reconstruct: error while loading shared libraries: libepvh.so.1: cannot open shared object file: No such file or directory*

*libepvh.so.1* does, in fact, exist in the *lib* folder in the unzipped .tgz, but it's not being recognized, I guess. I even tried putting it in the path (/usr/lib), but it's still not recognized.

I have no idea how to install that.

The homepage says the binary (I'm assuming it's *reconstruct*, as that's the only executable in the .tgz) is compiled for Mandrake. > 
The binary does require the presence of some (standard) shared libraries. Of course it also requires the libepvh shared library, so be sure to place it in your LD_LIBRARY_PATH. The binary was compiled on a Mandrake 9.2 Linux PC and on Fedora Core 2 Linux PC and worked on the RedHat linux PCs we have in the lab. Here is the dependency list (ldd):

   libGLU.so.1 => /usr/lib/libGLU.so.1
   libGL.so.1 => /usr/X11R6/lib/libGL.so.1
   libXmu.so.6 => /usr/X11R6/lib/libXmu.so.6
   libXext.so.6 => /usr/X11R6/lib/libXext.so.6
   libX11.so.6 => /usr/X11R6/lib/libX11.so.6
   libstdc++.so.6 => /usr/lib/libstdc++.so.6
   libm.so.6 => /lib/tls/libm.so.6
   libgcc_s.so.1 => /lib/libgcc_s.so.1
   libc.so.6 => /lib/tls/libc.so.6
   libtiff.so.3 => /usr/lib/libtiff.so.3
   libjpeg.so.62 => /usr/lib/libjpeg.so.62
   libz.so.1 => /usr/lib/libz.so.1
   libthread.so.0 => /usr/lib/libthread.so.0
   libdl.so.2 => /lib/libdl.so.2
   libXt.so.6 => /usr/X11R6/lib/libXt.so.6
   libSM.so.6 => /usr/X11R6/lib/libSM.so.6
   libICE.so.6 => /usr/X11R6/lib/libICE.so.6
   /lib/ld-linux.so.2 => /lib/ld-linux.so.2

Most of these libraries are installed by default on recent linux distributions.
The most notable exceptions could be the GL/GLU shared libraries (usually available with standard rpms, like Mesa) and the libstdc++.so.6 (I did encounter version problems on some machines, but this is usually solved by installing some standard rpm that provides the needed version).
However you hopefully shouldn't have to deal with any of that. Perhaps you might want to try using PCLinuxOS (which is Mandriva-based)?

---

### Post by vanth13 on 2006-10-07
I added in the lib path the dir where libephv is and it works. It doesn't find libtiff.so.3...

in synaptic I just find libtiff.4 but not .so ...??

make another try...

what's PClLinuxOS   ?? how can I run it on my macbook?

thanlks so much

---

### Post by vanth13 on 2006-10-07
the problems is : the libraries

Synaptic is the only way for searching? can I try something else? how does it works? I need all the libs in the dependancy list...

---

### Post by aysiu on 2006-10-07
PCLinuxOS is another Linux distribution. It's based off Mandriva, which used to be called Mandrake.

Apparently, the binary for EPVH is compiled specifically for Mandrake, so you may not have all those dependency/library problems if you just run *reconstruct* in PCLinuxOS.

---

### Post by vanth13 on 2006-10-07
this is very unconfortable...

I have to install another version just for one app?? 

crazy!!!!

thank you aysiu. you were very helpfull

---

### Post by aysiu on 2006-10-07
It's not really your typical application. In fact, if you do a Google search for *ubuntu epvh*, **nothing** comes up in the results.

Try that for any other Linux application.

It sounds as if the developer just made it difficult.

---

### Post by vanth13 on 2006-10-07
yes in fact... tryng now with pclinux os and then on debian

---

### Post by vanth13 on 2006-10-07
I'm now on PCLinuxos and it's the same!!! can't find all the lib..

and if I runn the run_me example executable file it say: ./reconstruct: error while loading shared libraries: /home/vanth13/Desktop/franco/epvh-1.0/lib/libepvh.so.1: invalid ELF header

what can I do??? just let go and don't use it? This kind of things make me mad and I fight till I win!!!

ideas???

---

### Post by aysiu on 2006-10-07
No ideas... maybe contact the developer?

---

### Post by rlopez3d on 2008-04-22
Hi:

I am a student looking for the EPVH-1.1 Visual Hull Library. I did have this library before but I lost it when my hard drives crashed. Now I must finish my research work and I can not find it anymore.  I would appreciate very much if you send me a copy. PLEASE help me. 

Best regards,

Robert

---


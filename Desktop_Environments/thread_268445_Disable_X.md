---
title: "Disable X?"
date: 2006-09-30
forum: Desktop Environments
---

### Post by jason_w on 2006-09-30
Hi there,

How do I disable X.  I'm trying to run Dapper as a server without X11.  In the past (I've used Fedora and Redhat), I would simply edit /etc/inittab.   It looks like it isn't that easy with Ubuntu...

:confused: Thank y0u...

---

### Post by apjone on 2006-09-30
Just download

Server install CD

The server install CD allows you to install Ubuntu permanently on a computer for use as a server. It will not install a graphical user interface.

There are four images available, each for a different type of computer:

PC (Intel x86) server install CD
[http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-server-i386.iso](http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-server-i386.iso)
    For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows. Choose this if you are at all unsure.

Mac (PowerPC) server install CD
[http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-server-powerpc.iso](http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-server-powerpc.iso)
    For Apple Macintosh G3, G4, and G5 computers, including iBooks and PowerBooks.

64-bit PC (AMD64) server install CD
[http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-server-amd64.iso](http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-server-amd64.iso)
    For computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon). It is not necessary for all (even most) processors made by AMD -- only their 64 bit chips.

SPARC server install CD
[http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-server-sparc.iso](http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-server-sparc.iso)
    For Sun UltraSPARC computers, including those based on the multicore UltraSPARC T1 ("Niagara") processors.

---

### Post by Jussi Kukkonen on 2006-09-30
apjone, I don't think you answered the actual question there :)

jason_w, not sure if you realised that but there are quite a lot of services running on the dektop Ubuntu that a server just doesn't need... the server installs might be easier choices.

To answer your question: you can prevent gdm from starting, by e.g. removing /etc/rc2.d/SXXgdm -symlink.

---


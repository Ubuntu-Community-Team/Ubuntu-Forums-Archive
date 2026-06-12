---
title: "Issue after Installing OpenFOAM"
date: 2011-04-07
forum: Education &amp; Science
---

### Post by jesse.johns on 2011-04-07
Hello gracious ones,

I installed openFOAM and paraview.  Then in following the instructions, I added:

source /opt/openfoam171/etc/bashrc

To my .bashrc file.  When I open up a new terminal, however, I receive the following error, twice:

[FONT=monospace]/usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../../lib/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: ld returned 1 exit status

[/FONT]I figured that maybe the cause was due to not having the proper GNU compiler or libraries, so I installed just about every library that seemed reasonable.  In checking the forumns, I saw one gentleman claim that the library that contains crt1.0 is "glibc-devel;" however, I can't seem to find something along those lines.

I'm am not quite sure what the implications of this error might be since have not yet tested all the capabilities of openFOAM in its current state.  Any advice would be greatly appreciated.

Thank you.
[FONT=monospace]
[/FONT]

---

### Post by Azrael3000 on 2011-04-10
Hey,

according to this thread [http://ubuntuforums.org/showthread.php?t=190193](http://ubuntuforums.org/showthread.php?t=190193)
you need to install libc6-dev. That package should definitely exist.

Cheers,
Arno

---

### Post by jesse.johns on 2012-05-07
Hi,

Just to clear up how I fixed this:

MATLAB happens to install its own MPI libraries.  I decided to remove those and built MPICH2 myself just following the directions from the Argonne website.   OpenFOAM then required a few changes within the make files to point to MPICH2 instead of OpenMPI. 

I tend to keep beating at a problem until I figure it out, then I forget to come back to the forum... 

Cheers.

---


---
title: "SCIRun installation problems"
date: 2007-06-16
forum: Education &amp; Science
---

### Post by gdoermann on 2007-06-16
Has anyone installed SCIRun ([http://software.sci.utah.edu/]("http://software.sci.utah.edu/"))?
I have had some problems when I try and make the thirdparty programs.  If anyone can help it would be great.

I have tried installing the program several times, each time receiving the same error.  I read [this]("http://software.sci.utah.edu/SCIRunDocs/index.php/Documentation:SCIRun:Installation:Unix:CommonProblems") wiki on the Common Problems and installing on Ubuntu.  I installed the following packages: x-libs, xlibs-dev, flex, bison, subversion, libpng, smp kernel, libxaw, libxaw-dev, libglew, lapack, blas, g77, gcc, g++, make, cmake(available in Universe) and made sure they were up to date. 

I followed [this]("http://software.sci.utah.edu/SCIRunDocs/index.php/CIBC:Documentation:SCIRun:Installation:Unix-v3.0.2#Operating_System") wiki to install the program. 

glxgears said everything was working with my ATI card. 
X11 is installed and working, g++ is version 4.1.2, and cmake is 2.4- patch 6

I extracted the SCIRun tarball into a Download folder in my home directory. 
In the terminal I changed directory to the SCIRun directory and ran the ./build.sh command.  This was successful. 
I changed to the thirdparty.src directory and ran the ./install.sh, specifying the full path to the thirdparty.bin directory (ps, there is a typo in the wiki at this part- mispelled thirdparty.bin). 
This also was successful (at least it did not show any errors).

I changed to the bin directory, and ran cmake .../src
To this point there have been no real problems.  When I ran make (I did not specify how many cores) it gave me an error 2 and an error 1.  I thought it might have been a rights issue, so I tried
sudo make
This didn't work either, it gave the same error.  I have attached any error logs I could find and have also attached a file with the last 1000 lines of code from the terminal named "log."

---

### Post by kleeman on 2007-06-16
The error says you are missing glu.h which is in
libglu1-mesa-dev

If you have an ati card and are using the fglrx driver you might want to install
xorg-driver-fglrx-dev

as well

---

### Post by in_flu_ence on 2007-06-16
Seems like an interesting tool. Does it work well with fluid dynamics area or it is just meant for bio-related stuff.

---

### Post by gdoermann on 2007-06-16
> **in_flu_ence said:**
> Seems like an interesting tool. Does it work well with fluid dynamics area or it is just meant for bio-related stuff.

I believe it has a plugin for fluid dynamics and works very well for that purpose.

---

### Post by gdoermann on 2007-06-16
Hey thanks kleeman, I am a bit of a noob still on Ubuntu.  I got it up and running!

---


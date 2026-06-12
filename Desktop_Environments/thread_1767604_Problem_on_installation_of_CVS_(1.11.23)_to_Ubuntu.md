---
title: "Problem on installation of CVS (1.11.23) to Ubuntu 11.04"
date: 2011-05-25
forum: Desktop Environments
---

### Post by Tetsuro Kikuchi on 2011-05-25
Hello.
 
I would like to install CVS-1.11.23 to my Ubuntu 11.04 (64-bit) OS. My host machine is HP Z800 workstation, of which hardware has a dual-boot system by Ubuntu 11.04 and Windows 7 (fifty-fifty split).
 
I have downloaded a tar archive of the version of CVS and got it extracted in home directory.
In Terminal, I set the environment variable "CC" as follows:
 
export CC=gcc
 
Then, I run the configure script by entering "./configure" and successively run the make program. However, it failed with the error messages which are written in the attached log file.
 
Could you provide me any idea to solve this problem and complete installation?
 
 
Tetsuro

---

### Post by areeda on 2011-05-25
Is there a reason you can't just install the package from the Software Center?

---

### Post by Tetsuro Kikuchi on 2011-05-26
Thank you for your reply, areeda.
 
When I searched for softwares related to "cvs" at "Get Software" menu in Ubuntu Software Center of my OS, two kinds of CVS frontend named "Cervisia" and "tkcvs" were detected. Do you think these two CVS frontends would substitute CVS? Or do I misunderstand your comment? I have not been familiar with the area of software development and management.
 
I intend to use an atmospheric modeling program named "Community Multiscale Air Quality modeling system (CMAQ)" under a Linux OS. The operational guide of the modeling program says CVS is required to be installed before installing any components of the program.
 
 
Tetsuro

---

### Post by Tetsuro Kikuchi on 2011-05-26
I downloaded a package of CVS (cvs_1.12.13-12ubuntu1_amd64.deb) from "Ubuntu Packages Search" web site. Using the package, I finally succeeded in installation of CVS to my Ubuntu OS through Ubuntu Software Center. I have not known the way of installing CVS other than that reported previously.
 
Thank you for your consideration.

---


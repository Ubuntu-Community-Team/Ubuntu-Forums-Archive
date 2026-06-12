---
title: "OpenFOAM solver (dbnsTurbFoam) compilation problem"
date: 2015-07-02
forum: Education &amp; Science
---

### Post by Gert-Jan_Meijn on 2015-07-02
Hello everybody,

Can somebody please do me a favor and help me find the problem that occurs when I try to compile this application?

I want to make a modification of the "dbnsTurb" solver found in Openfoam Extend 3.1. Without giving all the details about my new solver, the first thing I wanted to accomplish is remove the energy equation from the solver. When I removed the actual solving of the energy equation in 'Mydbns.C' the solver recompiled without any issues. When I went on to remove the redundant flux calculations from the libraries, the main program no longer wanted to compile... The libraries are still compiling normally, but I only removed lines from them so that makes sense. The really confusing part is that error is due to "undefined reference to" which I don't quite get when I only change the internal contents of a script and not the references between the files/headers... 

I thoroughly checked the links to the libraries and to the headers.
Can somebody else try to compile the program and help me find the problem?

link to all the files needed to compile inside OpenFOAM extend 3.1:
[https://www.dropbox.com/s/nh8wxxlbn8b8nkk/dbnsTurb_modified.tar.gz?dl=1](https://www.dropbox.com/s/nh8wxxlbn8b8nkk/dbnsTurb_modified.tar.gz?dl=1)
link to the log-file of wmake:
[https://www.dropbox.com/s/594zc06qyncryx2/make.log?dl=1](https://www.dropbox.com/s/594zc06qyncryx2/make.log?dl=1)

---

### Post by monkeybrain20122 on 2015-08-23
Not really helping you with the compilation but openfoam has a repository for Ubuntu.
[http://www.openfoam.org/download/ubuntu.php](http://www.openfoam.org/download/ubuntu.php)

---


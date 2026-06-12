---
title: "LAMMPS compiling error"
date: 2013-10-24
forum: Education &amp; Science
---

### Post by fdzQHQR on 2013-10-24
Dear Developer and users,

I am new to LAMMPS and just try to install it. However, it produce the following error:

collect2: ld returned 1 exit status
make[1]: *** [../lmp_openmpi] Error 1
make[1]: Leaving directory `/home/vampire/tools/lammps-30Sep13/src/Obj_openmpi'
make: *** [openmpi] Error 2
vampire@vampire-HP-ProBook-4530s:~/tools/lammps-30Sep13/src$

I am not sure how to solve it but obviously related to lmp (what is lmp anyway?). Please be kind enough to provide me necessary steps to solve this error. By the way, I am working on Ubuntu 12.04 OS
Thanks in advance

---

### Post by Lars Noodén on 2013-10-24
If you are compiling anything on Ubuntu, you have probably taken a misstep and need to go back a little and start over.

Linux, Apache, MySQL/Postgresql, and Perl/PHP5/Python are all either on your system already or available via the package manager.  With the package manager not only do you get to skip compiling anything, but it also automatically handles dependencies and later updates and patches.

The Linux part, that's Ubuntu.  So you have that already.

Apache2, that's in Ubuntu Software Center or in Synaptic.  Same with MySQL and PHP5.

Perl and Python are already on your system.  

So the few packages you need can be installed via the package manager (Ubuntu Software Center or Synaptic) via a few clicks.  No compiling needed.

---

### Post by steeldriver on 2013-10-24
I suspect the OP is referring to this --> [http://lammps.sandia.gov/](http://lammps.sandia.gov/) rather than LAMP

However there does appear to be a PPA --> [http://lammps.sandia.gov/download.html#ubuntu](http://lammps.sandia.gov/download.html#ubuntu)

---

### Post by Lars Noodén on 2013-10-24
LOL.  No harm done, I hope.  The PPA would be the easy way, I hope it is up to date.

---

### Post by fdzQHQR on 2013-10-25
Steeldriver and Lars Nooden,

Thank you for your comments. However, I am not sure how it is going to work with pre-built LAMMPS. It is just go to usr/share/lammps-daily and type "make yes-all" and the rest of the commands?? Anyway, if any of you built this on your Ubuntu 12.04 please give me more information. 
Thanks

---

### Post by fdzQHQR on 2013-10-25
New error appreas here. I will post this also in LAMMPS mailing list. If any of you familier with this please give me some useful information to proceed from here. Thanks 

In file included from ../neigh_list.h:18:0,
                 from ../neigh_respa_omp.cpp:16:
../my_page.h: In member function ‘void LAMMPS_NS::MyPage<T>::allocate() [with T = int]’:
../my_page.h:154:7:   instantiated from ‘T* LAMMPS_NS::MyPage<T>::vget() [with T = int]’
../neigh_respa_omp.cpp:99:27:   instantiated from here
../my_page.h:216:11: warning: unused variable ‘ptr’ [-Wunused-variable]
mpic++ -O2 -funroll-loops -fstrict-aliasing -Wall -W -Wno-uninitialized  -DLAMMPS_GZIP -DLMP_USER_OMP -I../../src   -DFFT_FFTW3   -c ../output.cpp
mpic++ -O2 -funroll-loops -fstrict-aliasing -Wall -W -Wno-uninitialized  -DLAMMPS_GZIP -DLMP_USER_OMP -I../../src   -DFFT_FFTW3   -c ../pair_adp_omp.cpp
In file included from ../pair_adp_omp.h:28:0,
                 from ../pair_adp_omp.cpp:18:
../thr_omp.h:171:20: warning: unused parameter ‘nthreads’ [-Wunused-parameter]
../pair_adp_omp.cpp: In member function ‘virtual void LAMMPS_NS::PairADPOMP::compute(int, int)’:
../pair_adp_omp.cpp:74:10: error: ‘class LAMMPS_NS::ThrData’ has no member named ‘timer’
../pair_adp_omp.cpp:74:16: error: incomplete type ‘LAMMPS_NS::Timer’ used in nested name specifier
../pair_adp_omp.cpp:95:10: error: ‘class LAMMPS_NS::ThrData’ has no member named ‘timer’
../pair_adp_omp.cpp:95:16: error: incomplete type ‘LAMMPS_NS::Timer’ used in nested name specifier
../pair_adp_omp.cpp: In member function ‘void LAMMPS_NS::PairADPOMP::eval(int, int, LAMMPS_NS::ThrData*)’:
../pair_adp_omp.cpp:205:10: error: ‘class LAMMPS_NS::ThrData’ has no member named ‘timer’
../pair_adp_omp.cpp:205:16: error: incomplete type ‘LAMMPS_NS::Timer’ used in nested name specifier
../pair_adp_omp.cpp:223:10: error: ‘class LAMMPS_NS::ThrData’ has no member named ‘timer’
../pair_adp_omp.cpp:223:16: error: incomplete type ‘LAMMPS_NS::Timer’ used in nested name specifier
make[1]: *** [pair_adp_omp.o] Error 1
make[1]: Leaving directory `/home/vampire/tools/lammps-30Sep13/src/Obj_openmpi'
make: *** [openmpi] Error 2

---

### Post by Lars Noodén on 2013-10-25
PPAs contain ready-made packages, just not ones ready for the main repositories.  Using a PPA is mostly like using any other repository but the difference is that you have to point your package manager to the right archive.  

[https://help.launchpad.net/Packaging/PPA/InstallingSoftware](https://help.launchpad.net/Packaging/PPA/InstallingSoftware)

Once that's set, you can install your program and do not need to look at 'make' or other compiler tools.

Edit: see the link steeldriver posted in #3 above.  It goes to "Pre-built Ubuntu Linux executables " which would allow you to skip compiling everything yourself.

---

### Post by fdzQHQR on 2013-10-26
Hi all,

I have solved the above problem by editing the file pair_adp_omp.cpp by removing the thr->timer::(Timer::START) and thr->timer (timer::PAIR) lines. So it is solved. However, as my knowledge of Ubuntu 12.04lts OS is limited please someone advice me how to set FFTW2 library path to makefile.openmpi . I have fftw3 but lammps users requested to use fftw2 because fftw3 may chage the interface of the software. I downloaded fftw 2.1.5 version and keep it in my lammps-30Sep12/usr. Now i am not sure how to add the path to makefile to do the job because I have already tried to use I/home/vampire/tools/lammps-30Sep13/src/fftw-2.1.5 as path but doesn't work.??
Please anyone tell me what should I do to make it work.
Thanks

---

### Post by steeldriver on 2013-10-26
If you install it from the ppa there is no need to build anything - the ppa contains a pre-built binary for your system

[http://lammps.sandia.gov/download.html#ubuntu](http://lammps.sandia.gov/download.html#ubuntu)

3 commands and done

---

### Post by fdzQHQR on 2013-10-26
Dear Steeldriver,

I am trying to install it from lammps-daily package provided by the above link. However, I came across a problem which is althrough I have lammps-daily in /usr/bin/lammes-daily and /usr/share/lammes-daily-doc in correct places I can't run the make yes-all command and rest of them because when I am trying to access to /usr/bin/lammps-daily it said that lammps-daily is not a directory? So how can I run commands to build the lammps from lammps-daily PPA?? Please explain to me. By the way , I have limited knowledge of Ubuntu and particularly Linux so please try to answer with little details. Thanks a lot.
Jeffrey

---

### Post by Lars Noodén on 2013-10-26
If you get it via the PPA it is already built for you and you don't need to build anything yourself or even the source code.  The PPA uses the same package management tools that the regular repository uses.  So it takes care of any dependencies (other packages you need to run the first package) and updates.  You have to add your particular PPA manually following the instructions above, but once it is added to your list of repositories, you can install with a few clicks and won't need to compile anything.

---

### Post by fdzQHQR on 2013-10-27
Dear Lars,
Thanks for you feedback, However, there are still unclear places for me. 
According to your comment means ..... I can just run my calculation on this?? You also said that ppa can install with a few clicks... it means still I have to install the software or as I said it is already in appropriate directories so no need to do any thing about it??

---

### Post by Lars Noodén on 2013-10-27
There are two steps.  

The first one is a preparatory step and needs to be done only once.  That is to add the appropriate [PPA](http://www.makeuseof.com/tag/ubuntu-ppa-technology-explained/) to your list of repositories.  steeldriver pointed to it in #3 above.

The second one is that you can use your package manager (Synaptic or Ubuntu Software Center) to install LAMMPS.  No manually downloading or compilation is needed then.  

Then you should be able to run LAMMPS on your machine and get updates from the PPA as they become available.  Manual downloading or compilation should not come into the question using a PPA.

---


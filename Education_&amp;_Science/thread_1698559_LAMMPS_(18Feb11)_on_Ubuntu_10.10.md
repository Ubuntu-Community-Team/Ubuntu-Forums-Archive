---
title: "LAMMPS (18Feb11) on Ubuntu 10.10"
date: 2011-03-02
forum: Education &amp; Science
---

### Post by Yoshis88 on 2011-03-02
I'm here to post new instructions to be easily found by others searching the web.
I will tell you how to compile LAMMPS (18Feb11) on Ubuntu 10.10.
I don't expect to be making many return trips to this post, since as far as I can tell, everything works smoothly.

A couple pointers:
[LIST]
[*]LAMMPS will probably never be available through apt-get because of very quick release of patches and updates as well as the inability to modify/extend LAMMPS if it were installed by apt-get.  That means LAMMPS never gets "installed", and when you call it, the path to the binary must be explicitly given or be found within the $PATH.
[*]The version of LAMMPS changes very rapidly, so just replace lammps-18Feb11 with lammps-(whatever your package release date is) and everything should still work.
[*]The [LAMMPS documentation (link)]("http://lammps.sandia.gov/doc/Manual.html") is exceedingly thorough.
[*]Check the [mailing list (link)]("http://sourceforge.net/mailarchive/forum.php?forum_name=lammps-users"). [Searching it (link)]("http://sourceforge.net/search/?group_id=149493&type_of_search=mlists") is a good idea if you're stuck.
[*]Consult your local Linux expert for help using the command-line.
[*]I am not responsible for any difficulties you may encounter.
[/LIST]

Let's start making LAMMPS!
[LIST=0]
[*][Enable Universe Repository, if not enabled (link)]("https://help.ubuntu.com/community/Repositories/Ubuntu")
[*]Install required packages to build LAMMPS
You will need superuser privileges to successfully issue:
```
sudo apt-get install g++ mpi-default-bin mpi-default-dev fftw-dev
```
[*]Get LAMMPS and unpack LAMMPS
You can do this by going to the [LAMMPS WWW site (link)]("http://lammps.sandia.gov/") and unpack it using your favorite program.
Or by issuing the following commands in terminal:
```
wget http://lammps.sandia.gov/tars/lammps.tar.gz
tar xvzf lammps.tar.gz
```
[*]Compile LAMMPS
Make sure you are sitting in lammps-18Feb11/src (not the MAKE directory!).
```
cd lammps-18Feb11/src
make openmpi
```
[/LIST]

I may return to this article to add details on how to compile strictly serial versions, POEMS/MEAM/REAX, GPU, xmovie and other utilities.

---

### Post by thegreeneyes on 2011-03-17
!!!!
Yoshis88 .... simply magic!!!!

Thanks!!! ;-)

---

### Post by Frozenport on 2011-04-16
I seems to still be having some problems. I get about a hundred compiler problems and at the end:> ...
_GZIP   -DFFT_FFTW  -M region_block.cpp > region_block.d
mpic++ -O2 -funroll-loops -fstrict-aliasing -Wall -W -Wno-uninitialized -DLAMMPS_GZIP   -DFFT_FFTW  -M read_restart.cpp > read_restart.d
mpic++ -O2 -funroll-loops -fstrict-aliasing -Wall -W -Wno-uninitialized -DLAMMPS_GZIP   -DFFT_FFTW  -M read_data.cpp > read_data.d
read_data.cpp:22: fatal error: atom_vec_ellipsoid.h: No such file or directory
compilation terminated.
make[1]: *** [read_data.d] Error 1
make[1]: Leaving directory `/home/misha/Desktop/lammps/lammps-15Apr11/src/Obj_openmpi'
make: *** [openmpi] Error 2



Lammps documentary seems to say I should use gmake (which is make?) or to write my own make file. Has anybody encountered this problem before?

---

### Post by thegreeneyes on 2011-04-27
Any idea about how to run reaxFF in lammps?
Or at least about how to produce successfully the ATC library?

Thanks
Victor

---

### Post by Pand5461 on 2011-04-28
> **thegreeneyes said:**
> Any idea about how to run reaxFF in lammps?
Or at least about how to produce successfully the ATC library?


In lammps-XXX/src dir type ```
make yes-user-atc
``` or ```
make yes-reax
``` to set makefile options. Then go to lammps-XXX/lib/atc or lib/reax and compile the libs (README files give clues on how to do it). Then again in src dir type ```
make your-machine-name
```

---

### Post by joldaerath on 2011-12-15
Yoshis88, thanks a lot for this quick setup!

Did you ever manage to get GPU working in Ubuntu?  I took a few stabs at it but couldn't get it to work.

---


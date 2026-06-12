---
title: "LAMMPS in Ubuntu"
date: 2009-01-12
forum: Education &amp; Science
---

### Post by Yoshis88 on 2009-01-12
[B]#######
NB: This thread is outdated.  I haven't deleted it just for historical reference.  Please follow the [new post]("http://ubuntuforums.org/showthread.php?t=1390490") and do not post new comments to this thread.
#######[/B]


Step 1, install MPICH and FFTW2 (FFTW3 does not work as [evidenced in LAMMPS documentation]("http://lammps.sandia.gov/doc/Section_start.html#2_2"))
```

sudo apt-get install build-essential mpich-bin libmpich1.0-dev mpi-doc fftw2 fftw-dev libxaw7-dev

```

Step 2, Add an include line to [FONT="Courier New"]src/change_box.cpp[/FONT]
```

#include <cstring>

```

Step 3, run the following command in the [FONT="Courier New"]src[/FONT] directory
```

make debian

```

And it compiles!  I don't know if those steps were obvious to people, but it caused me to do a fair bit of detective work to figure out.
The [FONT="Courier New"]libxaw7-dev[/FONT] package was installed to allow xmovie to be compiled.  Just one [FONT="Courier New"]make[/FONT] and it was good.

PS:  This should be helpful information for people taking CEE 2324 under Professor To at the University of Pittsburgh.  Instead of dealing with cygwin, I would *highly* recommend installing Ubuntu inside of Windows (you can do that)!  It's just as if it were a Windows program, and no partitioning or hassle involved!  Then, you can work on a *real* Linux platform instead of a Linux emulation

---

### Post by chianchiere on 2009-02-06
There is a problem with lamboot/mpich and lamboot/openmpi: if you compile with mpich, then the code will not be executed via mpirun. 

The trick is to select  the "right" mpirun via

```
sudo update-alternatives --config mpirun
```

selecting 

> /usr/bin/mpirun.mpich

as preferred choice

cheers
a

---

### Post by cruger on 2009-03-23
Many thanks you have very much helped!

&#1089;&#1087;&#1072;&#1089;&#1080;&#1073;&#1086;, &#1086;&#1095;&#1077;&#1085;&#1100; &#1074;&#1099;&#1088;&#1091;&#1095;&#1080;&#1083;&#1080; &#1089; &#1101;&#1090;&#1080;&#1084; &#1083;&#1101;&#1084;&#1087;&#1089;&#1086;&#1084;, &#1072; &#1090;&#1086; &#1079;&#1072;&#1089;&#1090;&#1088;&#1103;&#1083; &#1091;&#1078;&#1077; :)

---

### Post by dimaslave on 2009-05-11
> **Yoshis88 said:**
> I was stumped on how to get LAMMPS (21 May 2008 version) molecular modeling and MD simulation software to work on this Ubuntu 8.10 computer (64-bit OS, shouldn't be relevant) and I tried searching the forums to no avail (though, the forums were down for the second half of that day).  But I finally got it to compile, and I was like, if only that was on the forums.  So, I'm going to come put it on here :)

Step 1, install MPICH and FFTW2 (FFTW3 does not work as [evidenced in LAMMPS documentation]("http://lammps.sandia.gov/doc/Section_start.html#2_2"))
```

sudo apt-get install build-essential mpich-bin libmpich1.0-dev mpi-doc fftw2 fftw-dev libxaw7-dev

```

Step 2, Add an include line to [FONT="Courier New"]src/change_box.cpp[/FONT]
```

#include <cstring>

```

Step 3, run the following command in the [FONT="Courier New"]src[/FONT] directory
```

make debian

```

And it compiles!  I don't know if those steps were obvious to people, but it caused me to do a fair bit of detective work to figure out.
The [FONT="Courier New"]libxaw7-dev[/FONT] package was installed to allow xmovie to be compiled.  Just one [FONT="Courier New"]make[/FONT] and it was good.

PS:  This should be helpful information for people taking CEE 2324 under Professor To at the University of Pittsburgh.  Instead of dealing with cygwin, I would *highly* recommend installing Ubuntu inside of Windows (you can do that)!  It's just as if it were a Windows program, and no partitioning or hassle involved!  Then, you can work on a *real* Linux platform instead of a Linux emulation

Thanks for the info Yoshis88. I've just compiled LAMMPS on my Ubuntu laptop, but every time I run a job on both cores it asks me for my user password... Has anyone encountered the same problem or is it just me? LAMMPS requires no password for single processor jobs, but it asks for it if there's communication between processors. This makes me think my mpich might not be configured properly, but I'm no expert. Any advice on how to get rid of this annoying password prompt would be appreciated.

Cheers,
D

---

### Post by ahmedo047 on 2009-05-23
Thanks for the info Yoshis88. I've just compiled LAMMPS on Ubuntu. But I don't be able to run any samples. **Sample:** Lammps manual has instructions following for one of the Lennard&#8722;Jones tests.

cd src
make debian
cp lmp_debian ../examples/lj
cd ../examples/lj
mpirun &#8722;np 4 lmp_debian <in.lj.nve

I tried above instructions but &#304;t isn't run.

please help me

Thanks in advance

---

### Post by Straight on 2009-06-10
Hey I think I might have the same issue. 

Just want to throw it out there that I am very new to this but being asked a vp for some help,


Following the documentation when I try and do 

mpirun -np 4 lmp_linux < in.lj.nve 



I get the following


  mpirun -np 4 lmp_debian < in.obstalce

ssh: connect to host localhost port 22: Connection refused
p0_3932:  p4_error: Child process exited while making connection to remote process on localhost: 0
p0_3932: (6.127177) net_send: could not write to fd=4, errno = 32
root@greg-desktop:~/Desktop/Lammps# 


Does this mean anything to anyone?  Any help at all would be helpful.

---

### Post by ahmedo047 on 2009-06-23
cd src
make debian
cp lmp_debian ../examples/lj
cd ../examples/lj
./lmp_debian <in.lj.nve

problem solved by using above commands. 

The "mpirun -np 4" means that you want to run on 4 processors. For 1 processor, you can just use:

./lmp_debian < in.lj.nve

---

### Post by ahmedo047 on 2009-06-24
Hi all,
 
 I have the following ERROR. What can I do?
 ahmedo@ahmedo:~/Masaüstü$ cd lammps
 ahmedo@ahmedo:~/Masaüstü/lammps$ cd src
 ahmedo@ahmedo:~/Masaüstü/lammps/src$ cp lmp_debian ../examples/GB-test
 ahmedo@ahmedo:~/Masaüstü/lammps/src$ cd -
 /home/ahmedo/Masaüstü/lammps
 ahmedo@ahmedo:~/Masaüstü/lammps$ cd examples
 ahmedo@ahmedo:~/Masaüstü/lammps/examples$ cd GB-test
 ahmedo@ahmedo:~/Masaüstü/lammps/examples/GB-test$ ./lmp_debian <
 in.ellipse.gayb
 erne
 LAMMPS (9 Jan 2009)
 *ERROR: Invalid atom style*
 ahmedo@ahmedo:~/Masaüstü/lammps/examples/GB-test./lmp_debian <
 in.ellipse.gayb
 erne
 
 *NOT&#304;CE:* in input file in.ellipse.gayberne
 
 # GayBerne ellipsoids in LJ background fluid
 
 units         lj
 atom_style   ellipsoid
 dimension    2
 .
 .
 .  						
*1. try*
 ahmedo@ahmedo:~/Masaüstü$ cd lammps
 ahmedo@ahmedo:~/Masaüstü/lammps$ cd src
 ahmedo@ahmedo:~/Masaüstü/lammps/src$ cp lmp_debian ../examples/GB-test
 ahmedo@ahmedo:~/Masaüstü/lammps/src$ cd -
 /home/ahmedo/Masaüstü/lammps
 ahmedo@ahmedo:~/Masaüstü/lammps$ cd examples
 ahmedo@ahmedo:~/Masaüstü/lammps/examples$ cd GB-test
 ahmedo@ahmedo:~/Masaüstü/lammps/examples/GB-test$ ./lmp_debian <
 in.ellipse.gayb
 erne
 LAMMPS (9 Jan 2009)
 ***ERROR: Invalid atom style***
 ahmedo@ahmedo:~/Masaüstü/lammps/examples/GB-test./lmp_debian <
 in.ellipse.gayb
 erne
 
 *NOT&#304;CE:* in input file in.ellipse.gayberne
 
 # GayBerne ellipsoids in LJ background fluid
 
 units         lj
 atom_style   ellipsoid
 dimension    2
 .
 .
 .
 ***2.try***
 
 ahmedo@ahmedo:~$ cd Masaüstü
 ahmedo@ahmedo:~/Masaüstü$ cd lammps
 ahmedo@ahmedo:~/Masaüstü/lammpscd src
 ahmedo@ahmedo:~/Masaüstü/lammps/src$ make yes-ellipsoid
 *Package ellipsoid does not exist*
 ahmedo@ahmedo:~/Masaüstü/lammps/src$
 [B]
 *3.try*[/B]
 ahmedo@ahmedo:~/Masaüstü/lammps/src$ make yes-asphere
 *Installing package asphere
 [B]/bin/sh: csh: not found
 make: *** [yes-asphere] Error 127*[/B]
 
 please help me
 Thanks in advance

---

### Post by ahmedo047 on 2009-06-24
The problem solved after I installed to ubuntu the csh package.
ahmedo@ahmedo:~/Masaüstü/lammps/src$ make yes-asphere
 Installing package asphere
ahmedo@ahmedo:~/Masaüstü/lammps/src$ make debian

ahmedo@ahmedo:~/Masaüstü$ cd lammps
 ahmedo@ahmedo:~/Masaüstü/lammps$ cd src
 ahmedo@ahmedo:~/Masaüstü/lammps/src$ cp lmp_debian ../examples/GB-test
 ahmedo@ahmedo:~/Masaüstü/lammps/src$ cd -
 /home/ahmedo/Masaüstü/lammps
 ahmedo@ahmedo:~/Masaüstü/lammps$ cd examples
 ahmedo@ahmedo:~/Masaüstü/lammps/examples$ cd GB-test
 ahmedo@ahmedo:~/Masaüstü/lammps/examples/GB-test$ ./lmp_debian <
 in.ellipse.gayberne

Step rot E_pair TotEng Press Volume 
       0    2.2718861            0        2.394      0.04788        20000 
     100    1.7442957            0    1.8380516  0.035762064    20558.675 
     200    2.2770743            0     2.399467  0.046545738    20620.294 
     300    1.8572884            0    1.9571177  0.042405959     18460.78 
     400    2.1710835 -0.00050891124    2.2872701   0.06679187    13689.462 
....

---

### Post by Led Sama on 2009-10-09
Hi everyone !

Im from Peru and i was trying to run LAMMPS (9sep09 version) in ubuntu 9.04, i follow  all the steps but i think my problem is with some libraries, this is the error i get when i execute **make debian**:[INDENT]......... -lfftw -lmpich -lblas -llapack -lifcore -lsvml -lompstub -limf -lifcore -lsvml -lompstub -limf -lcudart  -o ../lmp_debian
**/usr/bin/ld: cannot find -latc**
collect2: ld devolvió el estado de salida 1
make[1]: *** [../lmp_debian] Error 1
make[1]: se sale del directorio `/home/led/Escritorio/lammps-29Sep09/src/Obj_debian'
make: *** [debian] Error 2
[/INDENT]latc is refered to ATC library that needs to be compile before the LAMMPS and  was in the {LAMMPS}/lib/atc directory. The problem is that i dont know how to compile it, i dont understand what i have to config in the makefile.g++. in the readme says:

"Note that the ATC library makes MPI calls, so you must build it with
the same MPI library that is used to build LAMMPS, e.g. as specified
by settings in the lammps/src/MAKE/Makefile.foo file"

well what i do is this:

# ------ SETTINGS ------

# include any MPI settings needed for the ATC library to build with
# the same MPI library that LAMMPS is built with

CC =            g++
#CCFLAGS =       -O -g -I../../src -DMPICH_IGNORE_CXX_SEEK
[B]CCFLAGS =    $(PKGINC) -g -O -I/usr/lib/mpich/include/ -DFFT_FFTW -DLAMMPS_GZIP
[/B]ARCHIVE =    ar
ARCHFLAG =    -rc
DEPFLAGS =      -M
LINK =             g++
LINKFLAGS =    -O
USRLIB =    -lblas -llapack
SYSLIB =

this was the any change i made, but i have erros with linking the headers (*.h), Anything will help !!  

Thanks in advance

---

### Post by Led Sama on 2009-10-10
well i solve my firsts problems, but i cant compile the **gpu** library. I dont know if gpu only runs in NVIDIA devices =S, is there any posible way to run with no NVIDIA chip ? or maybe compile the LAMMPS without compiling GPU??.

Thanks i advance.

---

### Post by timestwo on 2009-10-14
Hi Led Sama
I'm battling the same issues installing Lammps under 9.04 -- how did you solve the first problem of  'errors with linking the headers (*.h),' for ATC
many thanks

---

### Post by Led Sama on 2009-10-22
Hi, can someone tell me wich intel fortran compiler you use to compile the REAX and POEMS libraries, i have tried wich some of them but i got erros like:

/usr/bin/ld: warning: libintlc.so.5, needed by /opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5, not found (try using -rpath or -rpath-link)
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `__gtq'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `tbk_string_stack_signal'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `_intel_fast_memcpy'
/opt/intel/Compiler/11.1/056/lib/intel64/libsvml.so: undefined reference to `__intel_cpu_indicator'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `a_csubq'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `__dtoq'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `__qtof'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `a_addq'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `__divq'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `a_leq'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `__eqq'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `__qtod'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `__jtoq'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `a_subq'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `__addq'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `__ltq'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `a_divq'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `_intel_fast_memset'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `__subq'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `a_caddq'
/opt/intel/Compiler/11.1/056/lib/intel64/libsvml.so: undefined reference to `__intel_cpu_indicator_init'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `__negq'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `__qtoj'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `__compareq'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `_intel_fast_memcmp'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `__itoq'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `__mulq'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `__qtoi'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `a_geq'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `__intel_sse2_strlen'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `a_cmulq'
/opt/intel/Compiler/11.1/056/lib/intel64/libifcore.so.5: undefined reference to `a_mulq'
collect2: ld devolvió el estado de salida 1
make[1]: *** [../lmp_debian] Error 1
make[1]: se sale del directorio `/home/led/LAMMPS/src/Obj_debian'
make: *** [debian] Error 2

the reax and meam library uses the -lifcore, is there some other way to compile please let me know !! .. 

PD: i have a amd64 version of ubuntu.

Thanks in advance !

---

### Post by Adrastos on 2009-11-01
Yoshis88, Thanks a lot for the help.
I was trying to install Lammps but in the latest release Lammps-3Nov09, there is no make file for the debian (i.e. no Makefile.debian) as it was in the previous versions. However for the time being I have installed the older version but what should I do now to install the latest version ?

---

### Post by puroorava on 2009-11-05
Hello everyone
I followed the above steps but when I run the 'make debian' command i get an error message '' make: *** [debian] Error 1''.
Please help

Regards
Puroorava Chakravarthy

---

### Post by copross65 on 2009-11-28
I figured a way to do it, keep reading  below

---

### Post by copross65 on 2009-12-02
Download it from lammps.sandia.gov
 

 In the terminal write the following:
   
 gunzip lammps*.tar.gz 
 tar xvf lammps*.tar
 

 This will create a file named: ''lammps-21Nov09'' (The date may change depending of the updates in the website).
 

 It will contain the following files: bench, doc, examples, lib, potentials, src, tools.
 

 christian@christian-laptop:~/lammps/lammps-21Nov09$ cd src 
 christian@christian-laptop:~/lammps/lammps-21Nov09$ cd MAKE
 

 Before keep going it is necessary to solve some dependencies: build-essential (to compile in C), MPIch (to work in parallel) , FFTW ( to compute long-range interactions), libxaw7 (to compute the movies). In one line code you choose
 

 sudo apt-get install build-essential mpich-bin libmpich1.0-dev fftw2 fftw-dev libxaw7-dev
 

 If you are working in your personal computer you just need
 

 sudo apt-get install build-essential
 sudo apt-get install libxaw7-dev
 

 To avoid future problems it will be better installing with the first line code
 Now in the MAKE file you will see a lot of makefiles.xxx. Most users think Makefile.linux is the one they should use because they use ''linux.'' If you open the Makefile.linux you will see that it requires MPICH and FFTW. Things that we actually don't need (especially if we are starting the use of lammps). What a Beginner needs to install is Makefile.serial. If you open this file you will see in the first line that it says: no MPICH, no FFTW.
 

 If you read carefully the Makefile.serial, in one line it says:  
 # MPI library, can be src/STUBS dummy lib.
 If you go to STUBS you will find a Makefile, this will create a dummy lib for MPI in accordance to the Makefile.serial. So in the STUBS file you type:
 

 christian@christian-laptop:~/lammps/lammps-21Nov09/src/STUBS$ make  clean
 christian@christian-laptop:~/lammps/lammps-21Nov09/src/STUBS$ make 
 

 Then you go back to src and compile lammps
 

 christian@christian-laptop:~/lammps/lammps-21Nov09/src$ make  clean-all
 christian@christian-laptop:~/lammps/lammps-21Nov09/src$ make  serial

---

### Post by copross65 on 2009-12-02
Continuing from the previous post I sent....

	 	 	 	 	  It will work correctly, to verify your installation we will run some examples. First type
 

 [EMAIL="christian@christian-laptop"]christian@christian-laptop[/EMAIL]:~/lammps/lammps-21Nov09/src$ ./lmp_serial
 You should get:


 LAMMPS (7 Jul 2009)
 

This means you are ok in the installation process, ctrl-C to get out and let's go to the examples file (cd ../examples), Choose any, and get deep in learning the meaning of the codes. Each example has one or more lammps input files.
 For instance I will choose ''flow'' (cd flow). It has two in.flow.xxx files. (input files). I will run one of them by typing:
 

 christian@christian-laptop:~/lammps/lammps-21Nov09/examples/flow$ ../../src/lmp_serial < in.flow.couette
 

  Where is the data stored? Check the in.flow.couette file to see where it is. Almost at the end it says:
 

 dump		1 all atom 50 dump.flow
 

 So the data is stored in dump.flow
 To finish this test let's visualize the data in a movie. First let's install xmovie
 For this
 

 christian@christian-laptop:~/lammps/lammps-21Nov09/examples/flow$ cd ../../tools/
 christian@christian-laptop:~/lammps/lammps-21Nov09/tools$ cd xmovie
 christian@christian-laptop:~/lammps/lammps-21Nov09/tools/xmovie$ make
 christian@christian-laptop:~/lammps/lammps-21Nov09/tools/xmovie$ ./xmovie
 

 Now you will be able to visualize your data using xmovie just by typing in the flow directory
 

 [EMAIL="christian@christian-laptop"]christian@christian-laptop[/EMAIL]:~/lammps/lammps-21Nov09/examples/flow$ ../../tools/xmovie/xmovie -scale dump.flow
 

 This will open the program, maybe your screen will appear black, change the color of your particles and click in Start to watch it.

---

### Post by semabay on 2009-12-03
Hi
   I have tried to install LAMMPS in ubuntu 9.10. but after I install what you have suggested  I tried to insert the command _Make Linux_  using the terminal  in the source file directory as the manual specified and I have got error message as bellow

semabay@aaus-07-1414:~/Desktop/lammps-11Nov09/src$ make linux
make[1]: Entering directory `/home/semabay/Desktop/lammps-11Nov09/src/Obj_linux'
Makefile:93: angle_charmm.d: No such file or directory
Makefile:93: angle_cosine.d: No such file or directory
Makefile:93: angle_cosine_delta.d: No such file or directory
Makefile:93: angle_cosine_squared.d: No such file or directory
Makefile:93: angle.d: No such file or directory
Makefile:93: angle_harmonic.d: No such file or directory
Makefile:93: angle_hybrid.d: No such file or directory
Makefile:93: angle_table.d: No such file or directory
Makefile:93: atom.d: No such file or directory
Makefile:93: atom_vec_angle.d: No such file or directory
Makefile:93: atom_vec_atomic.d: No such file or directory
Makefile:93: atom_vec_bond.d: No such file or directory
Makefile:93: atom_vec_charge.d: No such file or directory
Makefile:93: atom_vec.d: No such file or directory
Makefile:93: atom_vec_full.d: No such file or directory
Makefile:93: atom_vec_hybrid.d: No such file or directory
Makefile:93: atom_vec_molecular.d: No such file or directory
Makefile:93: bond.d: No such file or directory
Makefile:93: bond_fene.d: No such file or directory
Makefile:93: bond_fene_expand.d: No such file or directory
Makefile:93: bond_harmonic.d: No such file or directory
Makefile:93: bond_hybrid.d: No such file or directory
Makefile:93: bond_morse.d: No such file or directory
Makefile:93: bond_nonlinear.d: No such file or directory
Makefile:93: bond_quartic.d: No such file or directory
Makefile:93: bond_table.d: No such file or directory
Makefile:93: change_box.d: No such file or directory
Makefile:93: comm.d: No such file or directory
Makefile:93: compute_centro_atom.d: No such file or directory
Makefile:93: compute_cna_atom.d: No such file or directory
Makefile:93: compute_coord_atom.d: No such file or directory
Makefile:93: compute.d: No such file or directory
Makefile:93: compute_displace_atom.d: No such file or directory
Makefile:93: compute_erotate_sphere.d: No such file or directory
Makefile:93: compute_group_group.d: No such file or directory
Makefile:93: compute_heat_flux.d: No such file or directory
Makefile:93: compute_ke_atom.d: No such file or directory
Makefile:93: compute_ke.d: No such file or directory
Makefile:93: compute_pe_atom.d: No such file or directory
Makefile:93: compute_pe.d: No such file or directory
Makefile:93: compute_pressure.d: No such file or directory
Makefile:93: compute_reduce.d: No such file or directory
Makefile:93: compute_reduce_region.d: No such file or directory
Makefile:93: compute_stress_atom.d: No such file or directory
Makefile:93: compute_temp_com.d: No such file or directory
Makefile:93: compute_temp.d: No such file or directory
Makefile:93: compute_temp_deform.d: No such file or directory
Makefile:93: compute_temp_partial.d: No such file or directory
Makefile:93: compute_temp_profile.d: No such file or directory
Makefile:93: compute_temp_ramp.d: No such file or directory
Makefile:93: compute_temp_region.d: No such file or directory
Makefile:93: compute_temp_sphere.d: No such file or directory
Makefile:93: create_atoms.d: No such file or directory
Makefile:93: create_box.d: No such file or directory
Makefile:93: delete_atoms.d: No such file or directory
Makefile:93: delete_bonds.d: No such file or directory
Makefile:93: dihedral_charmm.d: No such file or directory
Makefile:93: dihedral.d: No such file or directory
Makefile:93: dihedral_harmonic.d: No such file or directory
Makefile:93: dihedral_helix.d: No such file or directory
Makefile:93: dihedral_hybrid.d: No such file or directory
Makefile:93: dihedral_multi_harmonic.d: No such file or directory
Makefile:93: dihedral_opls.d: No such file or directory
Makefile:93: displace_atoms.d: No such file or directory
Makefile:93: displace_box.d: No such file or directory
Makefile:93: domain.d: No such file or directory
Makefile:93: dump_atom.d: No such file or directory
Makefile:93: dump_bond.d: No such file or directory
Makefile:93: dump_cfg.d: No such file or directory
Makefile:93: dump.d: No such file or directory
Makefile:93: dump_custom.d: No such file or directory
Makefile:93: dump_dcd.d: No such file or directory
Makefile:93: dump_xyz.d: No such file or directory
Makefile:93: error.d: No such file or directory
Makefile:93: ewald.d: No such file or directory
Makefile:93: fft3d.d: No such file or directory
Makefile:93: fft3d_wrap.d: No such file or directory
Makefile:93: finish.d: No such file or directory
Makefile:93: fix_add_force.d: No such file or directory
Makefile:93: fix_ave_atom.d: No such file or directory
Makefile:93: fix_ave_force.d: No such file or directory
Makefile:93: fix_ave_spatial.d: No such file or directory
Makefile:93: fix_ave_time.d: No such file or directory
Makefile:93: fix_bond_break.d: No such file or directory
Makefile:93: fix_bond_create.d: No such file or directory
Makefile:93: fix_bond_swap.d: No such file or directory
Makefile:93: fix_box_relax.d: No such file or directory
Makefile:93: fix_com.d: No such file or directory
Makefile:93: fix_coord_original.d: No such file or directory
Makefile:93: fix.d: No such file or directory
Makefile:93: fix_deform.d: No such file or directory
Makefile:93: fix_deposit.d: No such file or directory
Makefile:93: fix_drag.d: No such file or directory
Makefile:93: fix_dt_reset.d: No such file or directory
Makefile:93: fix_efield.d: No such file or directory
Makefile:93: fix_enforce2d.d: No such file or directory
Makefile:93: fix_evaporate.d: No such file or directory
Makefile:93: fix_gravity.d: No such file or directory
Makefile:93: fix_gyration.d: No such file or directory
Makefile:93: fix_heat.d: No such file or directory
Makefile:93: fix_indent.d: No such file or directory
Makefile:93: fix_langevin.d: No such file or directory
Makefile:93: fix_line_force.d: No such file or directory
Makefile:93: fix_minimize.d: No such file or directory
Makefile:93: fix_momentum.d: No such file or directory
Makefile:93: fix_msd.d: No such file or directory
Makefile:93: fix_nph.d: No such file or directory
Makefile:93: fix_npt.d: No such file or directory
Makefile:93: fix_npt_sphere.d: No such file or directory
Makefile:93: fix_nve.d: No such file or directory
Makefile:93: fix_nve_limit.d: No such file or directory
Makefile:93: fix_nve_noforce.d: No such file or directory
Makefile:93: fix_nve_sphere.d: No such file or directory
Makefile:93: fix_nvt.d: No such file or directory
Makefile:93: fix_nvt_sllod.d: No such file or directory
Makefile:93: fix_nvt_sphere.d: No such file or directory
Makefile:93: fix_orient_fcc.d: No such file or directory
Makefile:93: fix_plane_force.d: No such file or directory
Makefile:93: fix_press_berendsen.d: No such file or directory
Makefile:93: fix_print.d: No such file or directory
Makefile:93: fix_rdf.d: No such file or directory
Makefile:93: fix_recenter.d: No such file or directory
Makefile:93: fix_respa.d: No such file or directory
Makefile:93: fix_rigid.d: No such file or directory
Makefile:93: fix_set_force.d: No such file or directory
Makefile:93: fix_shake.d: No such file or directory
Makefile:93: fix_shear_history.d: No such file or directory
Makefile:93: fix_spring.d: No such file or directory
Makefile:93: fix_spring_rg.d: No such file or directory
Makefile:93: fix_spring_self.d: No such file or directory
Makefile:93: fix_temp_berendsen.d: No such file or directory
Makefile:93: fix_temp_rescale.d: No such file or directory
Makefile:93: fix_thermal_conductivity.d: No such file or directory
Makefile:93: fix_tmd.d: No such file or directory
Makefile:93: fix_ttm.d: No such file or directory
Makefile:93: fix_viscosity.d: No such file or directory
Makefile:93: fix_viscous.d: No such file or directory
Makefile:93: fix_wall_lj126.d: No such file or directory
Makefile:93: fix_wall_lj93.d: No such file or directory
Makefile:93: fix_wall_reflect.d: No such file or directory
Makefile:93: fix_wiggle.d: No such file or directory
Makefile:93: force.d: No such file or directory
Makefile:93: group.d: No such file or directory
Makefile:93: improper.d: No such file or directory
Makefile:93: improper_cvff.d: No such file or directory
Makefile:93: improper_harmonic.d: No such file or directory
Makefile:93: improper_hybrid.d: No such file or directory
Makefile:93: input.d: No such file or directory
Makefile:93: integrate.d: No such file or directory
Makefile:93: kspace.d: No such file or directory
Makefile:93: lammps.d: No such file or directory
Makefile:93: lattice.d: No such file or directory
Makefile:93: library.d: No such file or directory
Makefile:93: main.d: No such file or directory
Makefile:93: memory.d: No such file or directory
Makefile:93: min_cg.d: No such file or directory
Makefile:93: min.d: No such file or directory
Makefile:93: min_hftn.d: No such file or directory
Makefile:93: minimize.d: No such file or directory
Makefile:93: min_linesearch.d: No such file or directory
Makefile:93: min_sd.d: No such file or directory
Makefile:93: modify.d: No such file or directory
Makefile:93: neigh_bond.d: No such file or directory
Makefile:93: neighbor.d: No such file or directory
Makefile:93: neigh_derive.d: No such file or directory
Makefile:93: neigh_full.d: No such file or directory
Makefile:93: neigh_gran.d: No such file or directory
Makefile:93: neigh_half_bin.d: No such file or directory
Makefile:93: neigh_half_multi.d: No such file or directory
Makefile:93: neigh_half_nsq.d: No such file or directory
Makefile:93: neigh_list.d: No such file or directory
Makefile:93: neigh_request.d: No such file or directory
Makefile:93: neigh_respa.d: No such file or directory
Makefile:93: neigh_stencil.d: No such file or directory
Makefile:93: output.d: No such file or directory
Makefile:93: pack.d: No such file or directory
Makefile:93: pair_airebo.d: No such file or directory
Makefile:93: pair_born_coul_long.d: No such file or directory
Makefile:93: pair_buck_coul_cut.d: No such file or directory
Makefile:93: pair_buck_coul_long.d: No such file or directory
Makefile:93: pair_buck.d: No such file or directory
Makefile:93: pair_coul_cut.d: No such file or directory
Makefile:93: pair_coul_debye.d: No such file or directory
Makefile:93: pair_coul_long.d: No such file or directory
Makefile:93: pair.d: No such file or directory
Makefile:93: pair_eam_alloy.d: No such file or directory
Makefile:93: pair_eam.d: No such file or directory
Makefile:93: pair_eam_fs.d: No such file or directory
Makefile:93: pair_hybrid.d: No such file or directory
Makefile:93: pair_hybrid_overlay.d: No such file or directory
Makefile:93: pair_lj96_cut.d: No such file or directory
Makefile:93: pair_lj_charmm_coul_charmm.d: No such file or directory
Makefile:93: pair_lj_charmm_coul_charmm_implicit.d: No such file or directory
Makefile:93: pair_lj_charmm_coul_long.d: No such file or directory
Makefile:93: pair_lj_cut_coul_cut.d: No such file or directory
Makefile:93: pair_lj_cut_coul_debye.d: No such file or directory
Makefile:93: pair_lj_cut_coul_long.d: No such file or directory
Makefile:93: pair_lj_cut_coul_long_tip4p.d: No such file or directory
Makefile:93: pair_lj_cut.d: No such file or directory
Makefile:93: pair_lj_expand.d: No such file or directory
Makefile:93: pair_lj_gromacs_coul_gromacs.d: No such file or directory
Makefile:93: pair_lj_gromacs.d: No such file or directory
Makefile:93: pair_lj_smooth.d: No such file or directory
Makefile:93: pair_morse.d: No such file or directory
Makefile:93: pair_soft.d: No such file or directory
Makefile:93: pair_sw.d: No such file or directory
Makefile:93: pair_table.d: No such file or directory
Makefile:93: pair_tersoff.d: No such file or directory
Makefile:93: pair_tersoff_zbl.d: No such file or directory
Makefile:93: pair_yukawa.d: No such file or directory
Makefile:93: pppm.d: No such file or directory
Makefile:93: pppm_tip4p.d: No such file or directory
Makefile:93: random_mars.d: No such file or directory
Makefile:93: random_park.d: No such file or directory
Makefile:93: read_data.d: No such file or directory
Makefile:93: read_restart.d: No such file or directory
Makefile:93: region_block.d: No such file or directory
Makefile:93: region_cone.d: No such file or directory
Makefile:93: region.d: No such file or directory
Makefile:93: region_cylinder.d: No such file or directory
Makefile:93: region_intersect.d: No such file or directory
Makefile:93: region_prism.d: No such file or directory
Makefile:93: region_sphere.d: No such file or directory
Makefile:93: region_union.d: No such file or directory
Makefile:93: remap.d: No such file or directory
Makefile:93: remap_wrap.d: No such file or directory
Makefile:93: replicate.d: No such file or directory
Makefile:93: respa.d: No such file or directory
Makefile:93: run.d: No such file or directory
Makefile:93: set.d: No such file or directory
Makefile:93: shell.d: No such file or directory
Makefile:93: special.d: No such file or directory
Makefile:93: temper.d: No such file or directory
Makefile:93: thermo.d: No such file or directory
Makefile:93: timer.d: No such file or directory
Makefile:93: universe.d: No such file or directory
Makefile:93: update.d: No such file or directory
Makefile:93: variable.d: No such file or directory
Makefile:93: velocity.d: No such file or directory
icc -O -DLAMMPS_GZIP  -DMPICH_IGNORE_CXX_SEEK  -DFFT_FFTW -M velocity.cpp > velocity.d
/bin/sh: icc: not found
make[1]: *** [velocity.d] Error 127
make[1]: Leaving directory `/home/semabay/Desktop/lammps-11Nov09/src/Obj_linux'
make: *** [linux] Error 2


When I see the source file there is no *.d file rather it is *.h file. Do you have any solution for such error? Any idea may give me some hint to solve this problem.
Have a great time!

---

### Post by amp3030 on 2009-12-20
I have attached the makefile for debian. Using this file I am able to make LAMMPS (13Nov09) on my ubuntu 9.10.

Rename the file and remove the .txt from its name and then copy it to src/MAKE directory. That's it!

---

### Post by nandugopan on 2009-12-21
Guys, this may be a bit out of topic here, but I dont know where else to ask this..I have compiled LAMMPS in Ubuntu 9.10 and it works great. We have a small cluster in our University, operating under Red Hat Linux Enterprise 5.3


The .d errors and the [Error 1] and [Error 2] appear here as well, could any of you guys help me out with this. I am trying to compile using MPICH and FFTW on RHEL 5.3 using Intel Math Kernel Libraries (make type:intel_mkl)

---

### Post by Yoshis88 on 2010-01-25
Wow! I didn't realize all the additional replies here.  Unfortunately, I'm gonna have to deprecate this thread.

/close

Please redirect additional traffic and replies to the new [LAMMPS 24Jan10 in Ubuntu 9.10 post (link)]("http://ubuntuforums.org/showthread.php?t=1390490").

---

### Post by haifei on 2010-03-05
Hi,there
I am from Australia.
I can build lammps very easyly,but the problems how to build the additional package,like the meam, poems,and reax package.
BTW, my system is ubuntu 9.10, and the lammps is the latest 6 Mar 2010
Looking forward your help.
 
Thank y

---

### Post by moh1135 on 2010-04-07
> **puroorava said:**
> Hello everyone
I followed the above steps but when I run the 'make debian' command i get an error message '' make: *** [debian] Error 1''.
Please help

Regards
Puroorava Chakravarthy

It is also my problem, Please guide our to solve this problem
I use the last version (27 mar 2010)

---

### Post by moh1135 on 2010-04-07
[LEFT][RIGHT]
[/LEFT][/RIGHT]
[LEFT][RIGHT]**Hello everyone**[/LEFT][/RIGHT]
[LEFT][RIGHT]
I followed the above steps but when I run the 'make debian' command ( 27 mar 2010 version),I also get an error message **'' make: *** [debian] Error 1''.**[/LEFT][/RIGHT]
[LEFT][RIGHT][/LEFT][/RIGHT]
  [LEFT][RIGHT]I found it was some others problem but I didn’t find its solution[/LEFT][/RIGHT]
[LEFT][RIGHT]
[/LEFT][/RIGHT]
[LEFT][RIGHT] Please help me
**Regards**[/LEFT][/RIGHT]
  [LEFT][RIGHT]
Gholamhosain Haidari[/LEFT][/RIGHT]

---

### Post by tanhavi on 2010-04-18
> **moh1135 said:**
> [LEFT][RIGHT]
[/RIGHT]

[RIGHT]**Hello everyone**[/RIGHT]

[RIGHT]
I followed the above steps but when I run the 'make debian' command ( 27 mar 2010 version),I also get an error message **'' make: *** [debian] Error 1''.**[/RIGHT]
[/LEFT]
  [LEFT][RIGHT]I found it was some others problem but I didn’t find its solution[/RIGHT]

[RIGHT]
[/RIGHT]

[RIGHT] Please help me
**Regards**[/RIGHT]
[/LEFT]
  [LEFT][RIGHT]
Gholamhosain Haidari[/RIGHT]
[/LEFT]

Dear

I followed the above steps but when I run the 'make debian' command, and also get follow error masage:

sorena@sorena-desktop:~/Public/lammps-7Apr10/src$ make debian
make[1]: Entering directory `/home/sorena/Public/lammps-7Apr10/src/Obj_debian'
Makefile:50: fix_atc.d: No such file or directory
Makefile:50: force.d: No such file or directory
g++  -g -O -I/usr/lib/mpich/include/ -DFFT_FFTW -DLAMMPS_GZIP -M improper_hybrid.cpp > improper_hybrid.d
g++  -g -O -I/usr/lib/mpich/include/ -DFFT_FFTW -DLAMMPS_GZIP -M improper_harmonic.cpp > improper_harmonic.d
g++  -g -O -I/usr/lib/mpich/include/ -DFFT_FFTW -DLAMMPS_GZIP -M improper_cvff.cpp > improper_cvff.d
g++  -g -O -I/usr/lib/mpich/include/ -DFFT_FFTW -DLAMMPS_GZIP -M improper_class2.cpp > improper_class2.d
g++  -g -O -I/usr/lib/mpich/include/ -DFFT_FFTW -DLAMMPS_GZIP -M force.cpp > force.d
g++  -g -O -I/usr/lib/mpich/include/ -DFFT_FFTW -DLAMMPS_GZIP -M fix_wall_gran.cpp > fix_wall_gran.d
g++  -g -O -I/usr/lib/mpich/include/ -DFFT_FFTW -DLAMMPS_GZIP -M fix_wall_colloid.cpp > fix_wall_colloid.d
g++  -g -O -I/usr/lib/mpich/include/ -DFFT_FFTW -DLAMMPS_GZIP -M fix_reax_bonds.cpp > fix_reax_bonds.d
In file included from fix_reax_bonds.cpp:21:
pair_reax_fortran.h:53:23: error: reax_defs.h: No such file or directory
make[1]: *** [fix_reax_bonds.d] Error 1
make[1]: Leaving directory `/home/sorena/Public/lammps-7Apr10/src/Obj_debian'
make: *** [debian] Error 2

Please help me

Since regards, 
Rahmati

---

### Post by lisati on 2010-04-18
As indicated in the first post, this is an old thread.
Please refer to the information here, which will likely help solve the problems mentioned: [http://ubuntuforums.org/showthread.php?t=1390490](http://ubuntuforums.org/showthread.php?t=1390490)

Thread closed

---


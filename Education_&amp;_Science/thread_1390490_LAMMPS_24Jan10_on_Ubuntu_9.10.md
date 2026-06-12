---
title: "LAMMPS 24Jan10 on Ubuntu 9.10"
date: 2010-01-25
forum: Education &amp; Science
---

### Post by Yoshis88 on 2010-01-25
[B]*********************************************
* NB: I'm going to have to deprecate this post.
* See the new post:
*
* [http://ubuntuforums.org/showthread.php?p=10512875](http://ubuntuforums.org/showthread.php?p=10512875)
*
*********************************************[/B]

---

### Post by copross65 on 2010-01-29
Hello,
 After 
STUBS/ -->make
cd ..
src/ --> make serial or make g++ or make ubuntu or ..

i get this error
`diff style_atom.h style_atom.tmp`: Ambiguous.

Why?

thanks

---

### Post by Yoshis88 on 2010-02-01
For the "Ambiguous" error:
[http://sourceforge.net/mailarchive/message.php?msg_id=33ea1b0a1001290731t154719aah67914af03cda191c%40mail.gmail.com](http://sourceforge.net/mailarchive/message.php?msg_id=33ea1b0a1001290731t154719aah67914af03cda191c%40mail.gmail.com)

Also, as of the 30 Jan 2010 patch, the need for the "tcsh" packaage should be no more!  Make sure, if you're having build problems, to get the latest LAMMPS.

Also, I'm going to add a line to remind people to search the mail list for LAMMPS.  Someone may have already asked your question!

---

### Post by Mikhail.Glagolev on 2010-02-10
Thank you very much, Yoshis! With your makefile I've got LAMMPS working in minutes:)

---

### Post by Aeonox on 2010-02-20
Thank you so much!

---

### Post by mathyou on 2010-02-20
> **Yoshis88 said:**
> You may remember my post [from yore (link)]("http://ubuntuforums.org/showthread.php?t=1038282&highlight=LAMMPS")Try an example to verify it works
While sitting in the src directory, the first command should run the "crack" example in serial mode.  If your computer supports it, the second command should utilize 2 cores and run faster.  Remember, even if you compile using the parallel makefile, the first invocation will still work, and is the reason you don't need a separate binary for serial runs.
```
# change to the examples/crack directory
cd ../examples/crack
# for serial or parallel builds
../../lmp_ubuntu < in.crack
# for parallel builds only
mpiexec -np 2 ../../lmp_ubuntu < in.crack
```


Really useful guide, thanks. Would maybe just change this bit to ```
mpiexec -np 2 ../../src/lmp_ubuntu < in.crack
``` as I think lmp_ubuntu is created in src? obvious to most but just in case someone is trying to follow word for word ;)

---

### Post by farside bunny on 2010-02-23
from the original post :
> **timestwo said:**
> Hi Led Sama
I'm battling the same issues installing Lammps under 9.04 -- how did you solve the first problem of  'errors with linking the headers (*.h),' for ATC
many thanks

hi !
I am pretty stuck on this as well on unbuntu 9.10 can any one help me ? :confused:

---

### Post by mathyou on 2010-02-25
Hello,

Just wondering if any of you fellow lammps users also use [atomeye]("http://mt.seas.upenn.edu/Archive/Graphics/A3/A3.html") for visualization? I use it without problems on my mac but on ubuntu the window is always slightly transparent. Anyone else seen this or willing to try the binary for me to check it's not just me?

cheers,
Matt

---

### Post by Led Sama on 2010-02-25
Hi everyone,

I made a small guide of LAMMPS installation in ubuntu 9.04, i know that the  debian machine is out of date, but i think  it could be helpful  for  some of you.

[URL="http://www.scribd.com/doc/24500442/Guia-de-Instalacion-LAMMPS"]http://www.scribd.com/doc/24500442/Guia-de-Instalacion-LAMMPS
[/URL]
PD: Is in spanish, sorry =P. 

Enjoy =)

---

### Post by Yoshis88 on 2010-03-01
mathyou : Thank you for pointing out that error.  Indeed, it doesn't give the correct relative path.  Also, I tried using the latest Atomeye, and I find no transparency in the window.  I am using Karmic.

Led Sama:  Excellent guide!  Spanish is not my native language, but I know enough to appreciate the usefulness and to follow it to get a more functioning LAMMPS installation than the instructions I have provided.  Perhaps I shall use your guide to transcribe a new and updated guide that outlines more complete instructions for installation.

---

### Post by mathyou on 2010-03-03
> **Yoshis88 said:**
> mathyou : Thank you for pointing out that error.  Indeed, it doesn't give the correct relative path.  Also, I tried using the latest Atomeye, and I find no transparency in the window.  I am using Karmic.

Thanks for looking at this. It is strange, I've attached a picture of what I get. Are you using 64 bit? I get this problem with the binary on the website and also compiling from source.

---

### Post by haifei on 2010-03-05
Could you show us how to make the additional packages, it will be very helpful.
 
thank you so muh.
BTW: ubuntu 9.10, lammps (any version is ok)

---

### Post by jenvy on 2010-03-27
Thank you for these Makefiles!  Your instructions worked perfectly, and it makes me wonder why the LAMMPS folk haven't included your 'make ubuntu' functionality in their distribution; just about everyone I know uses Ubuntu on their home computers and its probably the most popular linux target for LAMMPS.

---

### Post by garfieldpbj on 2010-03-30
Hi.

I have followed the instructions and got some compiled.

But reaxFF does not work..

For example running the example in.reax.tatb, gives the following output:

LAMMPS (29 Mar 2010)
Reading data file ...
  triclinic box = (0 0 0) to (13.624 17.1149 15.1826) with tilt (-5.75316 -6.32547 7.42573)
  1 by 1 by 1 processor grid
  384 atoms
ERROR: Invalid pair style


Can anyone tell me how to get it working?

/Peter

---

### Post by thegreeneyes on 2010-05-10
Hi all!!

Thanks Yoshis88, your guide was very useful to have LAMMPS running fast and easy on UBUNTU 9.10

I could also load some modules, this is what I did from src folder:

make no-all
make clean-all
make yes-all
make no-reax
make no-poems
make no-meam
make no-gpu
make no-USER-ATC
make ubuntu

and it worked, so that all packages except those listed are installed.

Any suggestion about how to add more packages is welcome.

Bye

Victor

---

### Post by Eothain on 2010-05-16
Hi all,
I am experiencing such a problem.

After following the steps, when i try to run one of the examples to verify the installation i have an error msg..
 lmp_ubuntu < in.indent
[COLOR=Red] lmp_ubuntu: command not found ![/COLOR]

[COLOR=Black]What couses this kind of error. Any commend?

Actually solved
./lmp_ubuntu < in.* works
thnx for the guide

[/COLOR]

---

### Post by richardmems on 2010-05-30
Hi 

Somehow i can compile the serial version of LAMMPS on 64 bit Ubuntu (serial). 

I can run the examples also, but the using the 'dump' command, the output files are not coming out from the input fils in examples itself. Is it because of some compilation problem with I/O program components?

anyone has this kind of problems

Richard
Singapore

---

### Post by agkbill on 2010-06-18
Hi,

I managed to compile and get the lmp_ubuntu to run the in.* files OK.

But I can't find xmovie and going to that directory and run make do not work.

Maybe due to 64 bit version?


Best regards,
/Christer

---

### Post by matsci on 2010-06-25
> **mathyou said:**
> Hello,

Just wondering if any of you fellow lammps users also use [atomeye]("http://mt.seas.upenn.edu/Archive/Graphics/A3/A3.html") for visualization? I use it without problems on my mac but on ubuntu the window is always slightly transparent. Anyone else seen this or willing to try the binary for me to check it's not just me?

cheers,
Matt

Matt,

I discovered that the alpha channel of the color mask wasn't set properly for my system (8.04-10.04, x86_64) and wrote a patch for AX.h/AX.c to correct it, which naturally requires rebuilding AtomEye (May 2006 release) from source. I doubt it will work for AtomEye3, but it may provide you with what you need to tweak that code. (Or, if you prefer, I have a binary for AtomEye2 x86_64 that has fixed the mask issue, just send me an email at bkappes at mines dot edu.)

-Branden

---

### Post by karthikiitkgp on 2010-07-19
thank you very much...
with your useful guide i have easily build lammps. i have tried it in cygwin. but i suffered lot. i did it in ubuntu without any problem.
i want to add meam package to lammps. i am unable to do. can anybody help me?

---

### Post by lan1967 on 2010-09-02
I tried to use make_ubuntu file on lucid Ubuntu but failed to install standard package.

---

### Post by mtf45 on 2010-09-12
Does anyone have information on building LAAMPS on Ubuntu 10.04? The Makefile.ubuntu given doesn't seem to work on the new version of Ubuntu, unless I'm doing something wrong.

---

### Post by hejun on 2010-10-05
Thank you so much! I have succeeded.

---

### Post by wangy1990 on 2010-10-19
Thank you very much! Your guide saved me~

---

### Post by dmansour on 2010-11-06
hi please help me
i can't install lammps-10Sep10 on ubuntu 9.10

---

### Post by l.anna on 2010-12-23
Dear all, 

First of all, I would like to thank Mikhail for helping me! Secondly, I get this error message while trying to compile LAMMPS: does anybody know why this happens? Thank you very much!


s0793217@s0793217-VPCF12Z1E:/home$ /home/s0793217/lammps-18Dec10/src/
bash: /home/s0793217/lammps-18Dec10/src/: is a directory
s0793217@s0793217-VPCF12Z1E:/home$ cd /home/s0793217/lammps-18Dec10/src
s0793217@s0793217-VPCF12Z1E:~/lammps-18Dec10/src$ cd STUBS; make; cd ..; make ubuntu-serial
mpi.cpp:35: warning: non-local variable ‘<anonymous struct> double_int’ uses anonymous type
ar: creating libmpi.a
make: *** [ubuntu-serial] Error 1
s0793217@s0793217-VPCF12Z1E:~/lammps-18Dec10/src$ 


With best wishes,
Anna

---

### Post by sagiljames on 2010-12-27
hii.. good work ..really helped

---

### Post by amarrch on 2011-01-27
[COLOR=Green]Hey man this guideline is very helpful thanks for sharing.
:guitar:
[/COLOR]

---

### Post by zempj on 2011-01-27
First of all, thx for the nice guide.

I'm also facing the problem that I can't use the meam package. Any ideas?

---

### Post by amarrch on 2011-01-27
Hey *Yoshis88 thank you very much, the procedure works fine for installing Lammps-18Jan11 on Ubuntu-10.10. And I have another step which people can add to access Lammps without specifying the absolute path of lmp_ubutnu. These steps are same as those prescribed by *[Claus7]("http://ubuntuforums.org/member.php?u=164533")[I] to install vmd in Ubuntu. 
An advanced Unix user can [/I]*easily *[I]figure out these steps, but I post these to help beginners like me. 

1. su -     #Login as the super user

2. give the root password 

Lets say the lmp_ubuntu file is created in a folder which is located in
/home/username/Desktop/lammps-18Jan11/src, then the next step will be

3. cd  /usr/local/bin/

4.[/I]
** sudo  ln -s /home/username/Desktop/lammps-18Jan11/src/lmp_ubuntu  /usr/local/bin/   ***# It will copy lmp_ubuntu from its present location to ** /usr/local/bin, and from now lmp_ubuntu can be accessed without specifying its absolute path. :P*

#How to set the root password (Optional)
#Taken from [dcasimir]("http://ubuntu-ky.ubuntuforums.org/member.php?u=993285")
administrator@ubuntu:~$ sudo passwd root
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
[I]
:guitar:


 
[/I]

---

### Post by lammps on 2011-06-11
I am getting following error after the make g++ command in the src folder.

I have edited g++4 in the makefile.g++ to g++. Also I have given path to MPI
MPI_INC =       -DMPICH_SKIP_MPICXX -I/usr/lib/mpich/include
MPI_PATH =      -I/usr/lib/openmpi/include/mpi.h -L/usr/lib/mpich/lib
MPI_LIB =       -lmpich -lpthread

here is the error log. Please provide some suggestion. 



Makefile:42: pair_lj_gromacs.d: No such file or directory
Makefile:42: pair_lj_gromacs_coul_gromacs.d: No such file or directory
Makefile:42: pair_lj_gromacs_coul_gromacs_cuda.d: No such file or directory
Makefile:42: pair_lj_gromacs_cuda.d: No such file or directory
g++ -O -DFFT_FFTW -DLAMMPS_GZIP -I../STUBS -M xdr_compat.cpp > xdr_compat.d
/bin/sh: g++: not found
make[1]: *** [xdr_compat.d] Error 127
make[1]: Leaving directory `/home/james/lammps-12Jun11/src/Obj_ubuntu_serial'
make: *** [ubuntu_serial] Error 2

---

### Post by aysun on 2011-11-02
Hi,
does anyone knows how to build LAMMPS on ubuntu 10.04?i am stucked!!!any help will be appraciated...
Thanks..
aysun.

---


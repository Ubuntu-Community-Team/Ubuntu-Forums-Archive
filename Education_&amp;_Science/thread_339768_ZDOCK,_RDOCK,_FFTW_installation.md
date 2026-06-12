---
title: "ZDOCK, RDOCK, FFTW installation"
date: 2007-01-16
forum: Education &amp; Science
---

### Post by JTzmbl3 on 2007-01-16
I am a grad student who is trying to apply protein docking in my research in plant biology (molecular biology/plant physiology/biochemistry).  Protein docking would for example be how an antibody and an antigen (e.g. a protein on a virus) fit together.

I am very new to Linux and Ubuntu.  I have finally gotten my computer to dual boot with 6.10 / Edgy and XP and get things where I want them to be.  There are various programs (with varying predictive qualities) available.  The two most popular (i.e. reliable) are AutoDock ( [http://autodock.scripps.edu/](http://autodock.scripps.edu/) )and ZDOCK/RDOCK ( [http://zlab.bu.edu/zdock/index.shtml](http://zlab.bu.edu/zdock/index.shtml) ).  I am trying to install ZDOCK and RDOCK.  The files are restricted to academic and non-profit users, but I can list what they are.

ZDOCK 
- a rigid-body docking program
- comes as a a zdock2.3_linux_Athlon.tar
(I'll have to put an update post in .... I'm in XP right now and I forget what is in them at this time)

RDOCK
- a refinement program
- comes as a deltaG_Linux.tar.gz
- requires FFTW (a C subroutine library for computing the discrete Fourier transform)
- this version of RDOCK needs v2, I believe ( [www.fftw.org](www.fftw.org) )
(I'll have to put an update post in .... I'm in XP right now and I forget what is in them at this time)

I did extract them to there own folders and tried compiling (not too sure what that was about) FFTW.  I am just really confused at this point.

If anyone could help with basic installing, I would appreciate it.

---

### Post by Richard Kut on 2007-01-16
Hello JTzmbl3, and welcome! The process of compiling software on Linux usually involves three steps. From a command prompt, type:

./configure
make
sudo make install

The above assumes that you have successfully uncompressed the software into a sub-directory on your hard drive, and that you are currently in that sub-directory.

Please give that a try, and if you are still having problems, then please paste the results of the three commands into this posting.

Good luck!

---

### Post by JTzmbl3 on 2007-01-16
I have three files to extract.  Should I extract them all to the same folder?  Where should I extract them to?  /usr or /home or to some other subfolder?

As promised, I'll list the contents of those files:



zdock2.3_linux_Athlon.tar

creates a folder called Athlon_Linux

block.pl                (2Kb)
create.pl               (2Kb)
create_lig            (18Kb)
create_lig.c           (4Kb)
mark_sur            (99Kb)
mark_sur.f          (14Kb)
README               (2Kb)
uniCHARMM         (10Kb)
zdock                (948Kb)


deltaG_Linux.tar.gz

creates a folder called deltaG_Linux

BND.charmm       (12Kb)
deltaG                 (59Kb)
README                (1Kb)
RTF.charmm        (42Kb)


fftw-2.1.5.tar.gz  (there is a v3, but ZDOCK requires FFTW 2.x)

creates a folder called fftw-2.1.5

it has 42 items (11 folders and 31 files)

some folder examples:  fftw, fortran, matlab, mpi, rfftww, threads
some file examples:  acinclude.m4, bootstrap.sh, config.log, configure.in, depcomp, INSTALL, libtool, mkinstalldirs, README, README.hocks





I'm sorry to have neglected to mention that I did try the 

./configure
make
sudo make install

last night.  I didn't understand what it was doing and when I got done.  I tried clicking of things or typing in commands, but nothing worked.  I really didn't know what I was doing.  

I'll try it again, but I do need to know where I should put these things.  Also, I think one said I didn't have permissions to install some files somewhere.  I tired it again after using 

sudo -i

and I didn't get that error.

I'm also including the the readme files:


for Zdock

ZDOCK 2.3

This is the README file for release 2.3 of ZDOCK program. ZDOCK is an
initial stage protein-protein docking program, developed by Rong Chen 
and Zhiping Weng in 2002. It evaluates Pairwise shape complementarity, 
desolvation and electrostatic energies using Fast Fourier Transform 
algorithm. Detailed description can be found in zdock2.3.pdf. Please 
reference "Chen R., Li L. and Weng Z., ZDOCK: An Initial-stage Protein 
Docking Algorithm, Proteins (in press)".

This distribution includes an executable file (zdock) of the ZDOCK program,
PDB processing file (mark_sur, uniCHARMM, block.pl), and auxiliary files
(create.pl, create_lig) to create predicted complex structures from a ZDOCK
output. All files have been compiled on an AMD Athlon(tm) MP 1900+ processor
([http://www.intel.com/design/PentiumIII/prodbref/index.htm](http://www.intel.com/design/PentiumIII/prodbref/index.htm)) with LINUX
operation system. 

Example:
mark_sur PDB new_PDB
zdock -R receptor.pdb -L ligand.pdb -o zdock.out
create.pl zdock.out

Attention: receptor.pdb, ligand.pdb and create_lig must be in your current
directory when you try to create all predicted structures using create.pl.

Standard PDB format files must be processed by mark_sur before used as the
input of ZDOCK. Formatted PDB files of docking benchmark can be downloaded at
[http://zlab.bu.edu/~rong/dock/download.html](http://zlab.bu.edu/~rong/dock/download.html). If you know that some atoms
are not in the binding site, you can block them by changing their ACE type
(column 55-56) to 19. This blocking procedure can improve docking
performance significantly. A blocking script block.pl is included, type
"block.pl" for usage information.

More options can be found by typing "zdock".

The computing time depends on the sizes of input proteins.  On average, it 
takes 1.5 hours with single processor with the default rotational sampling 
density of 15 degrees (without -D flag). The average computation time will
be 23 hours with 6 degree when -D flag is used.


for RDOCK

README file for deltaG, which evaluates energies for RDOCK after CHARMM
 minimization.

inputs:
receptor and ligand files, after CHARMM minimization

auxiliary files: 
BND.charmm and RTF.charmm (should be located in the current directory 
when deltaG is executed)

output:
file with electrostatics, vdW, and ACE energies (in that order), space
delimited

NOTES:
1. Only the ACE energy from deltaG is used by RDOCK; the van der Waals
and electrostatics terms that RDOCK uses are obtained from CHARMM.
2. The input PDB files for deltaG are assumed to have the polar hydrogens
added, from the CHARMM minimization. If the polar hydrogens are not in the 
file, deltaG will complain and the results will be erroneous (particularly
for the electrostatics and vdW terms).


for FFTW

This is FFTW, a collection of fast C routines to compute the Discrete
Fourier Transform in one or more dimensions.

`OFFICIAL' CODE:

The doc/ directory contains the manual in texinfo, postscript, info,
and HTML formats.  Frequently asked questions and answers can be found
in the FAQ/ directory in a variety of formats (including HTML).

The fftw/ directory contains the source code for the complex transforms,
and the rfftw/ directory contains the source code for the real transforms.

Large portions of the source are automatically generated by a program
in the gensrc/ directory (written in Objective Caml).  You do not need
this program to use FFTW, since FFTW comes with a default set of
pregenerated codelets.  You are, however, welcome to look at and play
with the generator (see the FFTW manual for more information).

The threads/ directory contains an parallel version of FFTW (for
shared-memory machines) that uses threads.  See the "Multi-threaded
FFTW" section of the manual for more information.

The mpi/ directory contains a parallel version of FFTW for transforms
on machines with MPI.  (This code, unlike our other two parallel
transforms, supports distributed memory machines.)  See the "MPI FFTW"
section of the manual for more information.

fortran/ contains some constant definitions for using FFTW from
Fortran (see the FFTW manual), and also a small example program.

Installation instructions are provided in the manual (don't worry, it
is straightforward).

`UNOFFICIAL' CODE (for you to play with):

matlab/ contains code that allows you to call FFTW from MATLAB.

The cilk/ directory contains an parallel version of FFTW written in
Cilk.  Cilk is a cool C-like language in which you can write spawn
foo() : foo will be executed in parallel with the main thread and the
cost of spawn is just a few cycles (compare this with all the mess you
have to do to create a posix thread and pay 3000 cycles for it).  More
info on Cilk can be found at [http://supertech.lcs.mit.edu/cilk/](http://supertech.lcs.mit.edu/cilk/).

CONTACTS
--------

FFTW was written by Matteo Frigo and Steven G. Johnson.  You can
contact them at [email]fftw@fftw.org[/email].  The latest version of FFTW,
benchmarks, links, and other information can be found at the FFTW home
page ([http://www.fftw.org)](http://www.fftw.org)).  You can also sign up to the fftw-announce
mailing list to receive (infrequent) updates and information about new
releases; to do so, go to:

	[http://www.fftw.org/mailman/listinfo/fftw-announce](http://www.fftw.org/mailman/listinfo/fftw-announce)



This file contains a random collection of the various hacks we did (or
did not dare to do) in order to get performance.  It is not intended
to be complete nor up to date, but it may be instructive for people to
read (see also my (Matteo Frigo's) slides on the web page).

1) Negative constants:

        a = 0.5 * b;               a = 0.5 * b;  
        c = 0.5 * d;	           c = -0.5 * d; 
        e = 1.0 + a;	 vs.       e = 1.0 + a;  
        f = 1.0 - c;	           f = 1.0 + c;  

   The code on the left is faster.  Guess why? The constants
   0.5 and -0.5 are stored in different memory locations and loaded
   separately.

2) Twiddle factors:

   For some reason that escapes me, every package I have seen
   (including FFTW 1.0) stores the twiddle factors in such
   a way that the codelets need to access memory in a random
   fashion.  It is much faster to just store the factors in the
   order they will be needed.  This increased spatial locality
   exploits caches and improves performance by about 30% for big
   arrays.

3) Loops:

   You may notice that the `twiddle' codelets contain a loop.
   This is the most logical choice, as opposed to moving the loop
   outside the codelet.  For example, one would expect that

      for (i = 0; i < n; ++i)
          foo();

   be slower than the case where the loop is inside foo().  This is
   usually the case, *except* for the ultrasparc.  FFTW would be 10%
   faster (more or less) if the loop were outside the codelet.
   Unfortunately, it would be slower everywhere else. If you want to
   play with this, the codelet generator can be easily hacked...

4) Array padding:

   (This is a disgusting hack that my programmer's ethic
   pervents me from releasing to the public).  

   On the IBM RS/6000, for big n, the following **** is *way* faster:

   - Take the input array
   - `inflate' it, that is, produce a bigger array in which every
     k-th element is unused (say k=512).  In other words, insert
     holes in the input.
   - execute fftw normally (properly hacked to keep the holes into
     account)
   - compact the array.

   With this hack, FFTW is sensibly faster than IBM's ESSL library.
   Sorry guys, I don't want to be responsible for releasing this
   monster (this works only on the RS/6000, fortunately).

5) Phase of moon:

   Don't take the numbers on the web page too seriously.  The
   architectural details of modern machines make performance
   *extremely* sensitive to little details such as where your code and
   data are placed in memory.  The ultimate example of brain damage is
   the Pentium Pro (what a surprise...), where we had a case in which
   adding a printf() statement to FFTW slowed down another completely
   unrelated fft program by a factor of 20.

   Our strategy to generate huge pieces of straight-line code should
   immunize FFTW sufficiently well against these problems, but you are
   still likely to observe weird things like: FFTW_ESTIMATE can be
   faster than FFTW_MEASURE.

   FFTW-17.0 will compute the phase of the moon in the planner and take
   it into account.

6) Estimator:

   The estimator tries to come up with a `reasonable' plan.
   Unfortunately, this concept is very machine-dependent.  The
   estimator in the release is tuned for the UltraSPARC.

   The following two parameters can be found in fftw/planner.c :

   #define NOTW_OPTIMAL_SIZE 32
   #define TWIDDLE_OPTIMAL_SIZE 12

   They say: use non-twiddle codelets of size close to 32, and twiddle
   codelets of size close to 12.  More or less, these are the most
   efficient pieces of code on the UltraSPARC.  Your mileage *will*
   vary.  Here are some suggestions for other machines.

   Pentium

   #define NOTW_OPTIMAL_SIZE 8   (or 16)
   #define TWIDDLE_OPTIMAL_SIZE 8

   Pentium Pro:

   #define NOTW_OPTIMAL_SIZE 32   (or 16)
   #define TWIDDLE_OPTIMAL_SIZE 2

   
   RS/6000:

   #define NOTW_OPTIMAL_SIZE 32
   #define TWIDDLE_OPTIMAL_SIZE 32

   The basic idea is: compute some plans for sizes you most care
   about, print the plan and plug in the numbers that appear more
   often (or some kind of average).  Note the dramatic difference
   between Pentium an Pentium Pro. (NO LONGER TRUE WITH --enable-i386-hacks)

7) Stack alignment:

   Pentium-type processors impose a huge performance penalty if double-
   precision values are not aligned to 8-byte boundaries in memory.
   (We have seen factors of 3 or more in tight loops.)  Unfortunately,
   the Intel ABI specifies that variables on the stack need only be aligned to
   4-byte boundaries.  Even more unfortunately, this convention is followed
   by Linux/x86 and gcc.

   To get around this, we wrote special macros (HACK_ALIGN_STACK_EVEN
   and HACK_ALIGN_STACK_ODD) that take effect when FFTW is compiled
   with gcc/egcs and 'configure --enable-i386-hacks' is used.  These
   macros are called before the computation-intensive "codelets"
   of FFTW.  They use the gcc __builtin_alloca function to examine the
   stack pointer and align the stack to an even or odd 4-byte boundary,
   depending upon how many values will be pushed on the stack to call
   the codelet.

---

### Post by Richard Kut on 2007-01-16
This section:

> This distribution includes an executable file (zdock) of the ZDOCK program,
PDB processing file (mark_sur, uniCHARMM, block.pl), and auxiliary files
(create.pl, create_lig) to create predicted complex structures from a ZDOCK
output. All files have been compiled on an AMD Athlon(tm) MP 1900+ processor
([http://www.intel.com/design/PentiumI...bref/index.htm](http://www.intel.com/design/PentiumI...bref/index.htm)) with LINUX
operation system. 

seems to say it all. This package looks to contain a pre-compiled binary software, along with some bits of source code for the peripheral applications, and a bit of Perl thrown in. Therefore, there may be no need to compile anything. Just try running the zdock file, and see what happens.

Go to a command prompt, change into the directory that contains the zdock file, and then type:

./zdock

If that fails, then gather up the error messages and paste them into this post. Alternatively, it may be more productive to follow up with the author of the software personally to see what support he could provide.  Note that I am not trying to pass the buck - just trying to get you the most expedient solution.Hope that helps.

---

### Post by Fraizerangus on 2007-09-07
Is anybody out there using the latest version of Zdock or Autodock tools, does anyone have the command lines to prepare and run Zdock with chosen pdb's?

Many thanks

Dan

---


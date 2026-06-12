---
title: "Install Petsc with MPI in Ubuntu"
date: 2008-01-11
forum: Education &amp; Science
---

### Post by moquita on 2008-01-11
Hello:
I would like to install PETSC 2.3.3-p8 (last release) with MPI in a PIV Dual Core with Ubuntu 7.10.
(This is just for a training process before put the code running in a cluster!)

I followed the instructions in PETSC home page, and i did an install with: 
./config/configure.py --with-cc=gcc --with-fc=g77
  --download-mpich=ifneeded

and after that i ran the make test and it was all OK (apparently).
The problem is, when i try to run an code with 2 or more processors, like,
 
mpiexec -np 2 ./ex1
the computer just runs twice the ex1, instead of paralelizing the data. (I tryed this line in another machine and it worked fine!)



I've also tryed:
./config/configure.py --with-cc=gcc --with-fc=g77 
 --with-mpi-dir=/usr/lib/mpich/

but when i do 
make  test

I get
%%%%%%%%%%%
> Running test examples to verify correct installation
> C/C++ example src/snes/examples/tutorials/ex19 run successfully with  
> 1 MPI
> process
> Possible error running C/C++ src/snes/examples/tutorials/ex19 with 2
 MPI  processes
 See [http://www.mcs.anl.gov/petsc/petsc-as/documentation/troubleshooting.html](http://www.mcs.anl.gov/petsc/petsc-as/documentation/troubleshooting.html)
 ssh: connect to host localhost port 22: Connection refused
 p0_2875:  p4_error: Child process exited while making connection to  
 remote
 process on localhost: 0
 p0_2875: (2.404214) net_send: could not write to fd=4, errno = 32
 Graphics example src/snes/examples/tutorials/ex19 run successfully  
 with 1
 MPI process
 Fortran example src/snes/examples/tutorials/ex5f run successfully  
 with 1
 MPI process
 Completed test examples
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

Does anybody know how to solve it?

Thanks in advance,
M

---

### Post by Deeprachu on 2008-10-05
Hmm..I am also working on PETSc since few months, but not in ubuntu..I am planning to work on ubuntu very soon. I don't have an exact solution of your problem, but a couple of suggestion.
-.Why don't you try some individual examples in examples directory present in petsc and see what you get.
-.Are you executing your program in cluster or in a single (or dual) core machine? 
-. Have you created the mpd.hosts file and started the mpd deamon? (This  could be a possible issue.)

---

### Post by lkness on 2008-10-08
Hi. I'm working on getting PETSC runing in ubuntu, but my problem is with the mpd process. When i look at your error message, isn't it saying that it is using ssh and could not connect? So either sshd isn't running or a firewall is in the way, right? Can you ssh to yourself? When you do a "-np 2" on a single cpu machine, doesn't it spawn 2 processes and then use ssh to connect them together to simulate the requested 2 cpus? 

Lanny

---


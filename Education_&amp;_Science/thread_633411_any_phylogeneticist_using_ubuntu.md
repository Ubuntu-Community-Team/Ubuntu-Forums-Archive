---
title: "any phylogeneticist using ubuntu?"
date: 2007-12-06
forum: Education &amp; Science
---

### Post by thermophile on 2007-12-06
just wondering if anyone is running Paup* or arb on their ubuntu machine?  I've built a few trees using fastdnaml which is massively  faster than Paup on my mac, but I don't like the limited models that fastdnaml offers.  I spent a few days last summer trying to get Paup and arb running on my ubuntu box but gave up cause I couldn't get them to either install or run properly.  just wondering if anyone out there has any tips.

thanks

---

### Post by machoo02 on 2007-12-07
I'm a grad student currently studying fish systematics and phylogenetics, and I primarily use Ubuntu.  However, I don't have PAUP* running on my machine, as my lab only has a mac license for it and I can't afford the license cost of the portable version.  I haven't heard of arb yet, but I will look into it.  PHYLIP installs and runs great, as does PhyML and MrBayes...PhyML might be a good substitute for fastdnaml, but it also suffers from a limited choice of models (although not as much as dnaml or fastdnaml)

---

### Post by thermophile on 2007-12-12
arb is mostly a database that is also has an alignment editor and can run trees using either NJ or Phylip.  I run it from X11 on my mac but it is supposed to work on linux too.  it was built by a big group of microbiologist in Germany and it seems like it's mostly used by microbiologist or others looking at rRNA.  but there's no reason that it couldn't work for any type of sequence data.  I'd like to use MrBayes, but essentially no microbiologist use baysian trees

---

### Post by takakia on 2008-11-10
I m phylogenetist and I mostly use ubuntu. but I have a great regard for debian. Sad thing is that MrBayes segfaults in amd64 architechtrue

---

### Post by frogotronic on 2010-04-16
Hello,

  An old thread, but is this still the case for MrBayes?  I'm strongly considering buying PAUP4.0*beta for UNIX/LINUX.  Anyone tried compiling this?  Or does it come with a binary?

- CH

---

### Post by mr chip on 2010-08-23
FWIW, I'm running the standard Ubuntu package for MrBayes on 10.04 amd64 with no problems.  Currently using it to infer phylogenies using hymenopteran DNA sequences from 400 odd taxa.

---

### Post by tymek666 on 2010-08-25
I'm running few programs under Ubuntu:
1. MrBayes
2. ARB
3. BioEdit under Wine
4. BEAST
5. BAPS
6. SITES

Still missing program like Sequencher :(

---

### Post by mr chip on 2010-08-25
I've just built and run a parallel version of Mr Bayes and the improvement is making me grin like an idiot.

I tested it with primates.nex, with lset nst=6 rates=invgamma and  mcmc ngen=10000 samplefreq=10.  With 1 core, the job took 30 seconds, with 2 it took 16 seconds, and with 3 it took 12 seconds (these are just wallclock measurements, haven't had time to test with 4 cores yet).  
Next step is to get MPI working on the network and see what effect throwing 16 cores at Mr Bayes has.

---

### Post by tymek666 on 2010-08-25
> **mr chip said:**
> I've just built and run a parallel version of Mr Bayes and the improvement is making me grin like an idiot.
Did you use this HowTo to get it work:
[http://mrbayes.csit.fsu.edu/wiki/index.php/Advanced_Topics#Compiling_and_Running_the_Parallel_Version_of_MrBayes]("http://mrbayes.csit.fsu.edu/wiki/index.php/Advanced_Topics#Compiling_and_Running_the_Parallel_Version_of_MrBayes")
It says that this is for cluster, maybe because dualcore processor weren't widely available when MrBayes was released.

---

### Post by mr chip on 2010-08-25
> **tymek666 said:**
> Did you use this HowTo to get it work:
[http://mrbayes.csit.fsu.edu/wiki/index.php/Advanced_Topics#Compiling_and_Running_the_Parallel_Version_of_MrBayes](http://mrbayes.csit.fsu.edu/wiki/index.php/Advanced_Topics#Compiling_and_Running_the_Parallel_Version_of_MrBayes)
It says that this is for cluster, maybe because dualcore processor weren't widely available when MrBayes was released.

I used that as a starting point, but it's not entirely helpful for Ubuntu users. Instead of using LAM I used Open MPI, which will work on a single multicore machine and across many machines. On 10.04 desktop, I had to install mpicc, libreadline5-dev and the openmpi packages to build and run mr bayes with MPI enabled

---

### Post by tymek666 on 2010-08-26
> **mr chip said:**
> I used that as a starting point, but it's not entirely helpful for Ubuntu users. Instead of using LAM I used Open MPI, which will work on a single multicore machine and across many machines. On 10.04 desktop, I had to install mpicc, libreadline5-dev and the openmpi packages to build and run mr bayes with MPI enabled
Would you like to post some kind of HowTo here?

---

### Post by mr chip on 2010-08-26
This isn't really a good quality HowTo, but a synopisis of what I covered in the ~30 minutes it took minutes to figure out the ubuntu 10.04 specific info not covered by the Mr Bayes wiki article. I ended up using mpich for the cluster.  Going through my  ~/.bash_history, the Ubuntu 10.04 specific steps and extra information for running a different clustering program to LAM are:

1. Install extra packages. I needed mpich, libmpich2-dev, libmpich2-1.2, and libreadline5-dev. 
2. Build Mr Bayes with the MPI value set to yes. As I have to single cpu version installed too, I renamed the mpi enabled version mbp 
3. Create an mpd config file ~/.mpd.conf with the line MPD_SECRETWORD=
(you'll need to choose a secret word)
4. 'mpd &' will launch the MPICH daemon, which manages processes on the cluster.
5. 'mpirun -np 4 mbp' should launch mr bayes with 4 available processors.
```
                              MrBayes v3.1.2

                      (Bayesian Analysis of Phylogeny)

                             (Parallel version)
                         (4 processors available)

                                     by

                  John P. Huelsenbeck and Fredrik Ronquist

```There's another MPI implementation you can and probably should try, OpenMPI. It should do away with the need to manually launch the mpd before doing the mpirun, but I haven't had time to remove mpich and build mr bayes with the OpenMPI version of mpicc.

---

### Post by tymek666 on 2010-08-27
Thank you, I'll try it out.

---


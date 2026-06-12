---
title: "Is it possible to download and install SAGE from Ubuntu site?"
date: 2012-02-03
forum: Education &amp; Science
---

### Post by arroy_0209 on 2012-02-03
I want to download and install the mathematical software SAGE in ubuntu 10.04 LTS. However I am unable to find this as a package available from ubuntu site though some discussions in forums imply that it is actually available. (For example, the package xfig is available from ubuntu: [http://packages.ubuntu.com/lucid/xfig](http://packages.ubuntu.com/lucid/xfig)). I know that one can download from SAGE homepage but that involves installing some other packages and people report, the method may be complicated depending on whether some other packages are already installed or not. For me it would be easier if I could get the whole thing from ubuntu. Perhaps I am missing the page from where SAGE is available. Can anybody please help me with this issue?

---

### Post by BeRoot ReBoot on 2012-02-03
Is there a reason you can't just install it from the repos?

---

### Post by memilanuk on 2012-02-04
...because the repo version is based on whatever was in Debian Stable *before* 10.04 came out... which means its horribly, horribly out of date.

Used to be they provided a pre-canned VM version that you could install and run on VirtualBox... not seeing that anymore.

---

### Post by arroy_0209 on 2012-02-05
Can anybody please give me an idea of what will be the size of the download if I try to get from sage website itself? This should include sizes of other (extra) necessary packages. (My download size is severely limited by my ISP, so that is a matter of concern.) Is it available on CD in market? (I have not heard yet.)

---

### Post by aasdfasdfg on 2012-02-06
Last year I installed SAGE in Ubuntu. I was unable to find prebuilt packages so ended up compiling it myself. The download itself was about 300 MB. Is that too large for you?

As for the compilation: I had no problems whatsoever, but it took quite a long time to compile so be prepared if you choose this step.

---

### Post by arroy_0209 on 2012-02-06
If I understand corrcetly, the steps to install SAGE are as follows:
1. Download source (sage-4.8-linux-32bit-ubuntu_10.04_lts-i686-Linux.tar.lzma) from local mirror site. Download size is about 413.37MB
2. Install other required packages: ```
sudo apt-get install build-essential m4 gfortran readline-common libreadline-dev
```3. export (optional, please see below) 
4. Extract the tarball: tar -lzma -xvf sage-*.tar.lzma
5. cd sage-*/
6. make

There is one step (no 3 above) that I fail to understand. There is a suggestion:

"If you have a machine with 4 processors, say, type
   the following to configure the build script to perform a parallel
   compilation of Sage using 4 jobs:

       export MAKE="make -j4"
       
With 4 processors, you might also consider "-j5" or "-j6" --
building with more jobs than CPU cores can speed things up."

How do I know how many processsors my computer has? What is the optimum j value? After this "make" command is to be used. The README.txt file says next: "Wait about 1 hour to 14 days, depending on your computer". I do not understand why I will have to wait so long? Is SAGE supposed to download and install more packages itself? That could explain the delay. Can anybody please clarify these two points?

---

### Post by rewyllys on 2012-02-06
To find out how many processors your computer has, use System > Administration > System Monitor.  Then, in System Monitor, choose either the System tab or the Resources tab.

Sorry that I can't help with your other questions.

---

### Post by arroy_0209 on 2012-02-07
Thanks for helping.

The hardware status  shows: Memory 991.9MiB, Processor 0, Processor 1 both being Intel(R) Pentium(R) Dual CPU E220 @2.40GHz.

So in my case should I write "make -j2"?

---

### Post by PGScooter on 2012-02-07
yes, -j2 or -j3. On some types of builds -j2 will be faster, on some -j3. You can't tell without testing it out. It shouldn't make too much of a difference.

---

### Post by arroy_0209 on 2012-02-07
Can you please explain a bit more? why just j2 or j3? why not j4 or j5? 
Is max j value one more than number of processors (my guess)?

Moreover how does one test which is faster? Once I run the command, it will start working for one particular j value. How do I test for the other j value?

---

### Post by aasdfasdfg on 2012-02-07
Compiling is possibly the most processor intensive process you will run into. Essentially, while compiling your computer is taking the however many millions of lines of code involved in SAGE and compiling them into a machine-readable language. Because it is such a long process (and uses tools written before multi-processor systems were super common for end users), people have tried to speed it up by making things try to take advantage of modern multiprocessor architectures. Even under optimal conditions, it is a long process so to some extent, this speedup may not even be noticed.

Basically, passing different j parameters has no effect on what the compilation is doing. If you run into errors, it is independent of what you passed into j. So start out with a reasonable value like j3 and see how it goes. If you get stuck at some errors and have a reason to run make again, you could then experiment with different j values and see if anything else appears to go faster. But realistically, all this worrying will make no difference because it will take a long time anyway.

---


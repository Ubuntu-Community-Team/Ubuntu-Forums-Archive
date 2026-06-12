---
title: "Ubuntu cpu benchmark"
date: 2006-08-02
forum: Desktop Environments
---

### Post by daniel of sarnia on 2006-08-02
Hello all, dose any know of a cpu benchmark that will run on ubuntu. I'm overclocking my cpu and I need somthing to mesure what I get over stock performance. maybe somthing that will calculate gigaflops.

Thanks.

---

### Post by daniel of sarnia on 2006-08-02
bump anyone know of anything good benchmarks?

---

### Post by fourchannel on 2006-08-02
tiobench  ?? maybe? (FourChannel does not know such mysteries in life)

But seriously, I searched for "benchmark" in synaptic and found some for filesystems, network, apache, system stress points, and whatnot.

---

### Post by daniel of sarnia on 2006-08-02
But I'm looking for just a cpu benchmark, and I have not seen anything in synaptic for a cpu benchmark, but like you said filesystems, network, apache, system stress points but nuthing for cpus.

---

### Post by fourchannel on 2006-08-02
[http://lbs.sourceforge.net/](http://lbs.sourceforge.net/) give this site a try.

I think BYTEmark is probably what you are looking for. It's a CPU benchmark. It looks like you will have to compile it from source though, which should not be hard...

first off download BYTEmark [http://www.tux.org/~mayer/linux/nbench-byte-2.2.2.tar.gz]("http://www.tux.org/%7Emayer/linux/nbench-byte-2.2.2.tar.gz")


and open up a terminal and go to the directory where you saved it, i.e. cd /home/USERNAME/download/bytemark or where ever you saved it.

the next step is to uncompress the archive ```
gzip -d nbench-byte-2.2.2.tar.gz
``` 
then we need to extract the files from the tar archive ```
tar -xf nbench-byte-2.2.2.tar
``` 
next we enter into the newly created directory ```
cd NAME_OF_NEW_DIRECTORY
``` 
then the fun part. run these 3 commands to configure and build your software. ```
./configure
make
sudo make install ##### this copies the files from your current directory to the system wide programs directory, usually /usr/bin
``` 
you *can* run the program without running the last command, meaning that after you launch BYTEmark from the current directory and no longer need it, then you can just delete the directory and not have to worry about having another program lost in the installed files on your PC


hope that helps

---

### Post by daniel of sarnia on 2006-08-02
there was no ./configure file, so I just did the make command and this showed up

daniel@kubuntu:~/nbench-byte-2.2.2$ make
gcc -s -static -Wall -O3    pointer.c   -o pointer
gcc  -DLINUX  -s -static -Wall -O3\
                -o pointer pointer.c
rm -f pointer.h
if [ "4" = `./pointer` ] ; then touch pointer.h ;\
        else echo "#define LONG64" >pointer.h ; fi
gcc  -DLINUX  -s -static -Wall -O3\
                -c emfloat.c
gcc  -DLINUX  -s -static -Wall -O3\
                -c misc.c
./sysinfo.sh gcc  -DLINUX  -s -static -Wall -O3
gcc  -DLINUX  -s -static -Wall -O3\
                -c nbench0.c
gcc  -DLINUX  -s -static -Wall -O3\
                -c nbench1.c
gcc  -DLINUX  -s -static -Wall -O3\
                -c sysspec.c
gcc  -DLINUX  -s -static -Wall -O3\
                -c hardware.c
gcc  -DLINUX  -s -static -Wall -O3 \
                emfloat.o misc.o nbench0.o nbench1.o sysspec.o hardware.o\
                -o nbench -lm


and when I did sudo make install it did this:

daniel@kubuntu:~/nbench-byte-2.2.2$ sudo make install
Password:
make: *** No rule to make target `install'.  Stop.

thanks

---

### Post by deeek on 2006-08-02
> **daniel of sarnia said:**
> there was no ./configure file, so I just did the make command and this showed up
...
and when I did sudo make install it did this:

daniel@kubuntu:~/nbench-byte-2.2.2$ sudo make install
Password:
make: *** No rule to make target `install'.  Stop.

thanks
If you take a look in that directory the nbench executable will be there.  Run it in a console: ./nbench

---

### Post by daniel of sarnia on 2006-08-02
yes it works, thank you both. this is perfect for my over clocking escapades. :)

---

### Post by JD82 on 2008-07-01
Try SuperPi for Linux: [ftp://pi.super-computing.org/Linux/super_pi.tar.gz](ftp://pi.super-computing.org/Linux/super_pi.tar.gz)

How to use it:
[LIST=1]
[*]Download
[*]Open a console window and enter the directory where super_pi.tar.gz is saved.
[*]Untar with ```
tar xvf super_pi.tar.gz
```
[*]Run SuperPi with ```
./super_pi 20
```
[/LIST]

20 means 20 bit number, which equals 1m
21 means 21 bit number, which equals 2m
25 means 25 bit number, which equals 32m


Here's my first run: 11.141 Sec

Intel Core 2 Quad Q9450 @3300 MHz on Ubuntu 8.04.1 32bit


```
jd@jd-desktop:~/super_pi$ ./super_pi 20
 Version 2.0 of the super_pi for Linux OS
 Fortran source program was translated into C program with version 19981204 of
 f2c, then generated C source program was optimized manually.
 pgcc 3.2-3 with compile option of "-fast -tp px -Mbuiltin -Minline=size:1000 -Mnoframe -Mnobounds -Mcache_align -Mdalign -Mnoreentrant" was used for the
 compilation.
 ------ Started super_pi run : mar lug 1 15:51:59 CEST 2008
 Start of PI calculation up to 1048576 decimal digits
 End of initialization. Time=       0.172 Sec.
 I= 1 L=       0        Time=       0.492 Sec.
 I= 2 L=       0        Time=       0.564 Sec.
 I= 3 L=       1        Time=       0.564 Sec.
 I= 4 L=       2        Time=       0.564 Sec.
 I= 5 L=       5        Time=       0.560 Sec.
 I= 6 L=      10        Time=       0.564 Sec.
 I= 7 L=      21        Time=       0.564 Sec.
 I= 8 L=      43        Time=       0.560 Sec.
 I= 9 L=      87        Time=       0.564 Sec.
 I=10 L=     174        Time=       0.564 Sec.
 I=11 L=     349        Time=       0.560 Sec.
 I=12 L=     698        Time=       0.564 Sec.
 I=13 L=    1396        Time=       0.560 Sec.
 I=14 L=    2794        Time=       0.560 Sec.
 I=15 L=    5588        Time=       0.560 Sec.
 I=16 L=   11176        Time=       0.552 Sec.
 I=17 L=   22353        Time=       0.544 Sec.
 I=18 L=   44707        Time=       0.528 Sec.
 I=19 L=   89415        Time=       0.488 Sec.
 End of main loop
 End of calculation.    Time=      11.073 Sec.
 End of data output.    Time=       0.068 Sec.
 Total calculation(I/O) time=      11.141(       0.408) Sec.
 ------ Ended super_pi run : mar lug 1 15:52:11 CEST 2008

```

---

### Post by daniel of sarnia on 2008-07-01
thanks, but you know this thread is two years old now

---

### Post by JD82 on 2008-07-01
Yes :D, but is the only thread throughout the forum that talks about cpu benchmarks. And the first on [Google]("http://www.google.it/search?hl=it&rlz=1B3GGGL_itIT274IT274&q=cpu+benchmark+ubuntu&btnG=Cerca&meta=&aq=t").

---


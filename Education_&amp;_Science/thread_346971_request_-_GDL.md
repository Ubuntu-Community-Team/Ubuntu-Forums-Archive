---
title: "request - GDL"
date: 2007-01-26
forum: Education &amp; Science
---

### Post by slaanco on 2007-01-26
I'm having problems with installation of GDL, what is free alternative to IDL. I would be very gratefull if somebody could make .deb file from it for edgy eft (i have 64bit CPU, so I'm not really sure if its belongs here, but it's sscientific program so I put it here :) ), so that the installation would be easier.  Any help will be appreciated.
the source and all info is here [http://gnudatalanguage.sourceforge.net/](http://gnudatalanguage.sourceforge.net/)

many thanx  in advance

---

### Post by Laerte Andrade on 2007-01-30
Well, I don't know how to make a Debian package, but I managed to compile and install GDL in my computer (Edgy too). :D  So perhaps I could help you compiling it. What seems to be the trouble? Is it the configuration (dependencies, etc.) or something during the compilation? Did you install the development packages of the dependencies (those with -dev after the name)?

I must say I'm very impressed with GDL 0.9pre4 so far. Some basic functions of IDL are still missing though.

---

### Post by slaanco on 2007-01-31
I followed instructions of everything i mean I installed all obligatory and also optional libraries compiled them with no errors and then i tried to compile GDL itself I set-up all the paths to those libraries and then after succesfull [I]./configure --with-readlinedir=/usr/local/readline-4.3/ --with-plplotdir=/usr/local/plplot/ --with-Magick=/usr/local/ImageMagick-6.3.1/ --with-netcdf=no --with-fftw=no --with-hdf5=no --with-hdf=no --with-python=no 
(i tried to make the simpliest way)[/I] then I tried make and there was some errors, and I wasn't able to fix them :(

every help will be very appreciated

---

### Post by Laerte Andrade on 2007-02-01
> **slaanco said:**
> I followed instructions of everything i mean I installed all obligatory and also optional libraries compiled them with no errors and then i tried to compile GDL itself I set-up all the paths to those libraries and then after succesfull [I]./configure --with-readlinedir=/usr/local/readline-4.3/ --with-plplotdir=/usr/local/plplot/ --with-Magick=/usr/local/ImageMagick-6.3.1/ --with-netcdf=no --with-fftw=no --with-hdf5=no --with-hdf=no --with-python=no 
(i tried to make the simpliest way)[/I] then I tried make and there was some errors, and I wasn't able to fix them :(

every help will be very appreciated

Well, if I remember correctly, if you installed the right packages for the libraries, you don't need to pass this information to ./configure using *--with-whatever=/usr/local/whatever*. You may try to get this instructions off and see if ./configure still works. If it doesn't, you may still need to install some development libraries using synaptic.

Then you could post the lines in make where the compiling fails, maybe it could give us some idea of what is missing.

Good luck! :)

---

### Post by slaanco on 2007-02-02
I've tried to reinstall all of the libraries and I've got error after *make* of HDF4 >

hdiff_array.o: In function `array_diff':
hdiff_array.c:(.text+0x183f): undefined reference to `sqrt'
collect2: ld returned 1 exit status
make[2]: *** [hdiff] Error 1
make[2]: Leaving directory `/home/slaanco/HDF4.2r1/mfhdf/hdiff'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/slaanco/HDF4.2r1/mfhdf'
make: *** [all-recursive] Error 1

any ideas how can I fixed it ?
EDIT
i tried and managed to get thru with *./configure with no errors with ./configure --with-netcdf=/usr/local/netcdf-3.6.1/ --with-hdf=no --with-hdf5=/usr/local/hdf5-1.6.5/hdf5/ --with-python=no*
what is funny, becasue no matter what I did the configure wasn't able to find my python and my python is installed from the deb files with apt-get so I assume that it should be placed somewhere where you can usually would look for it. anyway i tied make and result was >
dimension.hpp: In member function &#8216;SizeT dimension::Remove(SizeT)&#8217;:
dimension.hpp:164: error: &#8216;assert&#8217; was not declared in this scope
make[3]: *** [gdl-assocdata.o] Error 1
make[3]: Leaving directory `/home/slaanco/gdl-0.8.11/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/slaanco/gdl-0.8.11/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/slaanco/gdl-0.8.11'
make: *** [all] Error 2

any ideas ?

---

### Post by Laerte Andrade on 2007-02-05
> **slaanco said:**
> 
EDIT
i tried and managed to get thru with *./configure with no errors with ./configure --with-netcdf=/usr/local/netcdf-3.6.1/ --with-hdf=no --with-hdf5=/usr/local/hdf5-1.6.5/hdf5/ --with-python=no*

Well, i can tell you what I did. I managed to configure, compile and install in Edgy using only:

[I]./configure --with-python=no
make[/I]

So, if taking out the netcdf, hdf, and hdf5 flags cause some problem in ./configure, I would say you still need to install some development libraries using apt-get or synaptic.

---

### Post by slaanco on 2007-02-07
thanx |:) i will try it

---

### Post by marrabld on 2007-02-17
I had the same problems.

I am running 32bit edgy.

sudo apt-get install netcdfg-dev libhdf5-serial-dev libplplot-dev plplot9-driver-xwin libhdf4g-dev libreadline5-dev gsl-bin libgsl0-dev

then

./configure --with-python=no --with-Magick=no
make
cd src
./gsl

hope it helps!

---

### Post by slaanco on 2007-02-17
thanx but no change at all i ended up with 2 errors, her§s the log.

make[3]: Entering directory `/home/slaanco/gdl-0.8.11/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/netcdf-3 -I/usr/include/hdf -I/usr/include/hdf     -g -O2 -MT gdl-assocdata.o -MD -MP -MF ".deps/gdl-assocdata.Tpo" -c -o gdl-assocdata.o `test -f 'assocdata.cpp' || echo './'`assocdata.cpp; \
        then mv -f ".deps/gdl-assocdata.Tpo" ".deps/gdl-assocdata.Po"; else rm -f ".deps/gdl-assocdata.Tpo"; exit 1; fi
dimension.hpp: In member function ‘SizeT dimension::Remove(SizeT)’:
dimension.hpp:164: error: ‘assert’ was not declared in this scope
make[3]: *** [gdl-assocdata.o] Error 1
make[3]: Leaving directory `/home/slaanco/gdl-0.8.11/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/slaanco/gdl-0.8.11/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/slaanco/gdl-0.8.11'
make: *** [all] Error 2

---

### Post by marrabld on 2007-02-17
i forgot to mention that i downloaded the latest version GDL-0.9pre4.

I don't know if that would make a difference

---

### Post by slaanco on 2007-02-17
yup it does :) i was able to build it even with ./configure , but then when i started gdl, it showed error about magick library so, I've ./configure --with-Magick=no and everything goes now. 
but there is a small thing  i need to resolve, when i start gdl i get this

slaanco@apeiron:~$ gdl
GDL - GNU Data Language, Version 0.9
For basic information type HELP,/INFO
'GDL_STARTUP'/'IDL_STARTUP' environment variables both not set.
No startup file read.
GDL> 


any ideas ?

and thanx a lot with help

---

### Post by marrabld on 2007-02-18
Try this 

export IDL_STARTUP=/home/myself/src
export GDL_STARTUP=/home/myself/src 

"myself" obviously being you home directory

let me know how you go.

:guitar:

---

### Post by slaanco on 2007-02-19
thanx, it worked
 :)

---

### Post by marrabld on 2007-02-19
No Worries :popcorn:

---

### Post by slaanco on 2007-02-20
another problem with ./configure --with-magick=no u wont be able to process .jpg files. 
the problem manifest itself after succesfull build. When u try to run GDL it says that some libMagick file is missing. any ideas ?:confused:

---

### Post by slaanco on 2007-02-20
> **marrabld said:**
> Try this 

export IDL_STARTUP=/home/myself/src
export GDL_STARTUP=/home/myself/src 

"myself" obviously being you home directory

let me know how you go.

:guitar:

*update*
it worked but after reboot i've got the same thing as before

---

### Post by marrabld on 2007-08-06
Sorry mate I've been away from the forums for a while.  to get it working with Feisty (Ive upgraded) with libmagik but without Python.
```
    sudo apt-get install libreadline5-dev libgsl0-dev libplplot-dev libmagick9-dev libmagick++9-dev netcdfg-dev libhdf4g-dev libhdf5-serial-dev

```

```
./configure –with-python=no
make
sudo make install
```

Hope you get this and it helps.

---

### Post by Roux on 2007-08-30
Hi

I'm trying to install GDL0.9 on my laptop with Ubuntu Dapper and I also have some issues while compiling:

I installed properly the necessary development libraries (plplot, readline, and gsl), and then ran successfully the configure routine with this command:

```
./configure --with-plplotdir=/usr/include/plplot/ --with-netcdf=no --with-hdf=no --with-hdf5=no --with-Magick=/usr/include/Magick++/ --with-python=no
```

Then I ran make, which crashed when compiling plotting.cpp with this message:

```
    mv -f .deps/gdl-libinit_gm.Tpo .deps/gdl-libinit_gm.Po
    g++ -DHAVE_CONFIG_H -I. -I..      -g -O2 -MT gdl-plotting.o -MD -MP -MF .deps/gdl-plotting.Tpo -c -o gdl-plotting.o `test -f 'plotting.cpp ' || echo './'`plotting.cpp
    plotting.cpp : In function «void lib::plot(EnvT*)»:
    plotting.cpp :1106: error: «class GDLGStream» has no member named «gvpd»
    make[3]: *** [gdl-plotting.o] Error 1
    make[3]: quit the folder « /home/roux/GDL/gdl- 0.9pre5/src »
    make[2]: *** [all-recursive] Error 1
    make[2]: quit the folder « /home/roux/GDL/gdl- 0.9pre5/src »
    make[1]: *** [all-recursive] Error 1
    make[1]: quit the folder « /home/roux/GDL/gdl- 0.9pre5 »
    make: *** [all] Error 2
```

I tried to look up this problem on the trackers on Sourceforge but didn't see anything related to this.

It looks like a problem in the code, but since it's a three months old release, I assume there shouldn't be any problem like that so I really have no idea what to do...

Any idea what I might try?

---

### Post by slaanco on 2007-09-12
I had some problems while installing of gdl-0.9pre5. but after checking the forums on GDL project page i was able to fix it, try to install numarray it worked for me, although it was different error, or ask on the gdl forums.

otherwise i have no clue :(:confused:

---


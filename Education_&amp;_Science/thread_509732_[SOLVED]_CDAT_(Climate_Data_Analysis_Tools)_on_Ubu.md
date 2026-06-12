---
title: "[SOLVED] CDAT (Climate Data Analysis Tools) on Ubuntu"
date: 2007-07-25
forum: Education &amp; Science
---

### Post by aJayRoo on 2007-07-25
I want to try out using [CDAT](http://badc.nerc.ac.uk/help/software/cdat/) to analyse time series climate data. I managed to do the express install following [these](http://www-pcmdi.llnl.gov/software-portal/Members/jlin/ubuntuinstall) instructions however when I try to make a plot I get an error suggesting that gplot cannot be found. If I type gplot at a normal command prompt the program is found yet I cannot use functions within CDAT that require the use of gplot. Also it might be worth noting that plotting from VCDAT (the gui frontend to CDAT) works without a problem.

I was wondering if anyone had any experience of using CDAT on Ubuntu? I would appreciate any pointers on how to get it running smoothly. Thanks.

---

### Post by Eric_T on 2007-07-26
Don't know about CDAT, but the Norwegian Meteorological Institute just recently open sourced their visualization software:
[http://met.no/diana/](http://met.no/diana/)
All the usual formats aren't available yet, but other than that, it's got a lot of good features.

---

### Post by xadder on 2007-07-27
The web-side says that netcdf will be supported by Diana in Spring 2007. Do you know if that's happened already? (not Spring, the netcdf support  :-)

---

### Post by aJayRoo on 2007-07-27
Thanks for the link it looks quite interesting. I also require netcdf support however I was looking for information specific to CDAT as the other researchers working on the same project as me are using CDAT on our cluster. I was really looking for information on how to get that set up on my personal machine. I'm guessing not many people do that though!

---

### Post by aJayRoo on 2007-08-26
Well, I'm guessing there aren't many CDAT users out there but since I solved my problem I thought I would share the (simple) solution. It turns out that all I needed to  do was add the CDAT bin directory to my path! Doing this gave me a fully functioning CDAT install. Also just in case anyone is wondering CDAT-4.0 does not seem to play nice with Ubuntu however version 4.1 works very well!

---

### Post by always.arvind on 2008-10-31
Hi, 

I am trying to install CDAT 4.3 on ubuntu 8 , but the installation is not working.  

Has anyone had success on that ?

---

### Post by lisati on 2008-10-31
> **always.arvind said:**
> Hi, 

I am trying to install CDAT 4.3 on ubuntu 8 , but the installation is not working.  

Has anyone had success on that ?

8.04 or the recently relased 8.10?

---

### Post by ALittleSlow on 2009-02-18
> **always.arvind said:**
> Hi, 

I am trying to install CDAT 4.3 on ubuntu 8 , but the installation is not working.  

Has anyone had success on that ?

I just got CDAT 5.0.0 built on Ubuntu 8.04 Hardy Heron, though it's not yet fully functioning. What problem are you having?

Also, if you haven't already, check the Ubuntu section at [http://www2-pcmdi.llnl.gov/cdat/download/installation-guide/install-environment](http://www2-pcmdi.llnl.gov/cdat/download/installation-guide/install-environment).
I had to also install patch and libpng-dev from the Ubuntu server.
The Python module bz2 mysteriously did not appear in the dyn-load directory; I copied it from the standard Ubuntu Python directory since it was the same version of Python.

---

### Post by jjunju on 2009-03-22
> **ALittleSlow said:**
> I just got CDAT 5.0.0 built on Ubuntu 8.04 Hardy Heron, though it's not yet fully functioning. What problem are you having?

Also, if you haven't already, check the Ubuntu section at [http://www2-pcmdi.llnl.gov/cdat/download/installation-guide/install-environment](http://www2-pcmdi.llnl.gov/cdat/download/installation-guide/install-environment).
I had to also install patch and libpng-dev from the Ubuntu server.
The Python module bz2 mysteriously did not appear in the dyn-load directory; I copied it from the standard Ubuntu Python directory since it was the same version of Python.

hei

I am really stuck and i need a step by step guide. the guides at pcdmi are very ambiguous. I have already set the environments and downloaded the 5.o to  a folder 5.0.0 which is on my home dir. I am trying to install to a new directory cdat5 and cdat_ext on home but i keep getting these errors: 

jjunju@ubuntu:~/5.0.0$ ./configure --prefix=/home/jjunju/cdat5 --with-externals=/home/jjunju/cdat_ex --with-python=/usr/share/doc/Python --enable-ioapi --with-opendap --disable-netpbm
show_svn.c: In function 'main':
show_svn.c:14: warning: format '%s' expects type 'char *', but argument 3 has type 'char (*)[50]'
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.
jjunju@ubuntu:~/5.0.0$

---

### Post by kleeman on 2009-03-22
The Ubuntu section on the pcmdi site lists the packages required to build cdat..
From your output it is pretty clear you do not have some of these installed.
Fire up synaptic and search for the packages listed and install them one by one. Then try to build......

---


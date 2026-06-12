---
title: "can't run   SecondLife_i686_1_14_0_2"
date: 2007-04-26
forum: Gaming &amp; Leisure
---

### Post by suoko on 2007-04-26
I've got problems with feisty and SecondLife_i686_1_14_0_2

this is the error:

io@asus:/opt/SecondLife$ ./secondlife 
bin/do-not-directly-run-secondlife-bin: error while loading shared libraries: libelfio.so: cannot open shared object file: No such file or directory

version 14_0_1 works fine

any hints?

---

### Post by thingy on 2007-04-26
Looks like you need to install some dependancies:

libelfio, libopenjpeg, and libxmlrpc-epi

Source: [http://outflux.net/blog/archives/2007/01/10/attempting-a-secondlife-build-on-ubuntu/](http://outflux.net/blog/archives/2007/01/10/attempting-a-secondlife-build-on-ubuntu/)

---

### Post by suoko on 2007-05-01
those are not easy instructions...

---

### Post by Darko-TheRaven on 2007-05-01
yea, i had the same problem, just open synaptic and search the names of the dependencies and select them for install. (a little easier than the apt-get cmd line stuff)

---

### Post by arch stanton on 2007-05-01
Anyone having problems with Secondlife crashing every 5 min or so ..with nividia drivers?

---

### Post by DJ_Peng on 2007-05-11
I'm crashing frequently, but I thought it was due to being in a very busy area with not so much RAM. I'm running the 9631 drivers for my GeForce2 MX 100 video card and 749 MB of RAM.

---


---
title: "Intallation of  udunits"
date: 2006-01-21
forum: Desktop Environments
---

### Post by appopson on 2006-01-21
hi,
](*,) 

there is someone who can help me ?

I can not install udunits on my labtop?

Udnits can be downloaded at this address

 [http://www.unidata.ucar.edu/packages/udunits](http://www.unidata.ucar.edu/packages/udunits)

Thank's

---

### Post by drunkndog5 on 2006-02-13
I don't know if you still need this but I got this working today on my laptop.  First I had to install f2c.  
Then in the src directory edit the CUSTOMIZE file to include at the end : LD_MATH='-lm'

From there I used a customized configure set up 
CC='/usr/bin/gcc -Df2cFortran' PERL='usr/bin/perl' CPPFLAGS='-DNDEBUG -DpgiFortran' CFLAGS='-O -fno-builtin' sudo ./configure

I'm not sure if you need all of that I picked different parts up from different errors, but this is what seemed to work for me.

from there it was just 
sudo make
sudo make test
sudo make install

If you have any problems let me know I was playing with this for a while so have a little bit of an understanding.  

Neil

---

### Post by mwtoews on 2007-10-04
(old thread, I know, but the above didn't work for me).

I'm using Dapper LTS, and compiling udunits-1.12.4. I used:

./configure --prefix=/usr/local CPPFLAGS=-Df2cFortran CC=gcc CFLAGS=-O LD_MATH=-lm
make
make test
sudo make install

These four commands worked perfectly on my setup, without errors. Hopefully, someday UDUNITS will be updated to accommodate systems found now-a-days.

---

### Post by Mehmet Karatay on 2007-11-08
Thank you mwtoews. Your instructions worked perfectly. 

Mehmet

---


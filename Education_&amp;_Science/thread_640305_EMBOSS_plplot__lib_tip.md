---
title: "EMBOSS plplot  lib tip"
date: 2007-12-14
forum: Education &amp; Science
---

### Post by lbthrice on 2007-12-14
Hi all,

I checked around the forums a little to see if this information was posted previously but could not find it...however my searching kung fu leaves something to be desired, so I apologize if this is already out there.

For anyone trying to compile EMBOSS (European Molecular Biology Suite) on Ubuntu Feisty (7.04):

the ./configure will show that you need to update/install gd libraries for plplot

if you do not watch the ./configure output then the lack of required gd library will manifest as an error when you try to run an EMBOSS program, like wossname.  You will get:
 
'libnucleus.so.5 does not exist' 

...or something of that nature...sorry can't recall the error verbatim

just go to synaptic and install plplot from there!  then make clean,  ./configure, make and then make install.  This will yield a working EMBOSS install.

Another way to do it is to download the .rpm instead of the tar.gzip distros and use alien to transform the .rpm to .deb.

Good news: it looks like EMBOSS will be available as a .deb in the ubuntu Hardy repository!

---

### Post by Jota37 on 2008-01-07
Hey, thanks a lot, libthrice!

You just saved me a lot of time. Strange, the configure script does not complain about anything, the problem is not obvious at all...

I did what you suggested and it worked fine here (Ubuntu 7.10). Thanks again!

Cheers
J

---

### Post by Jota37 on 2008-01-07
Oops, **lbthrice**, not libthrice, sorry... Do you have to prepare LB three times, always? :-)

---


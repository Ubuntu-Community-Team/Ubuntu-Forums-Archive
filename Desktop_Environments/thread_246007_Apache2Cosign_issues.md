---
title: "Apache2/Cosign issues"
date: 2006-08-28
forum: Desktop Environments
---

### Post by adh2002 on 2006-08-28
I've recently been working on installing a web access program to access our departments intranet remotely.  To do so, I must use a program called Cosign.  ([http://www.umich.edu/~umweb/software/cosign/](http://www.umich.edu/~umweb/software/cosign/)) which requires the use of Apache2.  I installed all of the prerequsites (build-essential package (instead of Sun C Compiler) and Open SSL was already installed).  Following the instructions to configure Apache2 to work with Cosign, I receive this error: 'configure: error: cannot find apache2'.  I'm not sure why this is appearing because I have Apache2 installed.  Although, in the instructions it mentioned that there may be some tweaking required on the Apache end.  It failed to tell me what needed to be tweeked.  I was hoping someone else was also trying to do the same thing and could possibly help me out.  Thanks.

---

### Post by antcamx on 2006-09-11
Hi!

I configured with this option and it works ...

./configure --enable-apache2=/usr/sbin/apxs

Antonio C. :D

---


---
title: "LaTeX Gaim plugin"
date: 2006-05-22
forum: Desktop Environments
---

### Post by thrillhouse on 2006-05-22
I'm trying to get the gaim-latex plug in working.  I was able to get it to compile but when I try and send an IM with some latex in it, all I get is a file with a red x in it.  Any ideas?

---

### Post by thrillhouse on 2006-05-23
Ok, a little more help.  I have the following packages installed (in relation to this problem):

gs-gpl (8.01-5ubuntu5)
imagemagick (6:6.2.3.4-1ubuntu1.1)
libt1-5 (5.0.2-3)
libwww-ssl0 (5.4.0-9ubuntu0.5.10)
tetex-base (2.0.2c-8)
tetex-bin (2.0.2-30ubuntu3.5)
tetex-doc (2.0.2c-8)
tetex-extra (2.0.2c-8)
texinfo (4.7-2.2ubuntu2.1)
gaim (1:1.5.0-lubuntu3)
gaim-latex (0.3-1)  - From an rpm repository

Any helpful suggestions would be much obliged.  Attached is a screenshot of what the attempted LaTeX IM looks like (i used $$ 7 $$ for my test case).  Thanks.

---

### Post by Yoda222 on 2006-06-07
If it is in an old version (0.3 or 0.4) it's a known bug (known, but not understood) which is made that you cannot display image which are les than 1024 bytes (1 kB, don't remember if 1024 work, but 1025 work and 1023 doesn't work)

Two solutions : 1. try longer messages. 2. ask the packager to made a new version (0.4 is on sourceforge)

To be sure that this is a version problem try a message which do a large image.

---

### Post by thrillhouse on 2006-06-12
Your correct.  

\psi_{tot}(x,-t_0,r) = \frac{1}{(2\pi)^2} \int\!\!\!\int
\tilde\Psi_{tot}\left(k_x,\frac{c}{2}\sqrt{k_x^2 + k_r^2},r=0\right)

Works fine but any subsets of those do not.  Where can I get an rpm or deb or version 0.4.  I dont want to have to compile this myself if possible.

Thanks.

---


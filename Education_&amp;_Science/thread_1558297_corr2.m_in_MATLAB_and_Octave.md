---
title: "corr2.m in MATLAB and Octave"
date: 2010-08-22
forum: Education &amp; Science
---

### Post by sammy0131 on 2010-08-22
[FONT=Arial][SIZE=2]Hi, I'm trying hard to migrate on Ubuntu and started changing the scripts that i wrote for MATLAB to those for Octave.

I found that I've got a different result when I'm running "corr2" function in MATLAB and
Octave.

I use the same size of two matrices and then used as:

R = corr2(matrixA, matrixB);

in MATLAB R is one correlation coefficient just as:
[http://www.mathworks.com/access/helpdesk/help/toolbox/images/corr2.html](http://www.mathworks.com/access/helpdesk/help/toolbox/images/corr2.html).

However, when I run the same script in Octave, the answer turns out to be a
matrix. For example is I used 5000x600 matrix, the R is 600x600.

I'd very much appreciate if anyone can explain to me why this is happening.

Thanks in advance,[/SIZE][/FONT]

---

### Post by carandraug on 2010-08-29
This was solved in the [octave-dev mailing list]("http://www.mail-archive.com/octave-dev@lists.sourceforge.net/msg04320.html").

[QUOTE=Marco Atzeri]I guess that to replicate Matlab 

you need to call corr2(a(:),b(:)) 

as for cov
[http://octave.sourceforge.net/nan/function/cov.html](http://octave.sourceforge.net/nan/function/cov.html)
[/QUOTE]

---


---
title: "MATLAB uigetdir uigetfile"
date: 2005-12-27
forum: General Help
---

### Post by wasm on 2005-12-27
HELLO

This is my first post on this forum


I installed MATLAB 7.01 under UBUNTU 5.1

The installation carried out fine

The problem is that uigetdir and uigetfile starts but I can't browse and select folders and file

MATLAB doesn't give any error

What should I do?

thanks in advance wasm

---

### Post by adamkane on 2006-03-08
Post bug to Ubuntu Bugzilla
[https://launchpad.net/malone](https://launchpad.net/malone)

---

### Post by yoav on 2006-11-08
I'm having the same problem. Were you ever able to solve it?

Thanks,
Yoav

---

### Post by adamkane on 2006-11-09
MATLAB on Ubuntu:
[http://help.nceas.ucsb.edu/index.php/Matlab_on_Ubuntu_5.04](http://help.nceas.ucsb.edu/index.php/Matlab_on_Ubuntu_5.04)

There is also a great free alternative to MATLAB, Mathematica, Maple, if you are so interested.

Lyx + Maxima:
[http://www.jstatsoft.org/v17/s01/v17s01.pdf](http://www.jstatsoft.org/v17/s01/v17s01.pdf)

---

### Post by sjara on 2006-11-14
Unsetting the LANG variable before running matlab (R2006b on edgy) worked for me.
See [http://www.mathworks.com/support/solutions/data/1-VD2UO.html]("http://www.mathworks.com/support/solutions/data/1-VD2UO.html")

---

### Post by jhaitas on 2006-12-13
this does not completely solve the issue... uigetfile still doesn't behave in a normal manner

---

### Post by LeDopore on 2007-02-05
Hi jhaitas,

I'm having exactly the same issue.  Have you found out a way to fix it yet?

Thanks,

Patrick

---

### Post by yoav on 2007-02-16
Unsetting the LANG variable worked for me. 

Thanks!
Yoav

---


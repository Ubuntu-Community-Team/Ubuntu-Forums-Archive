---
title: "Xfoil question"
date: 2009-03-07
forum: Education &amp; Science
---

### Post by Eezyville on 2009-03-07
Is there any way to script commands in xfoil. I got this huge project in this class that requires alot of xfoil input and I'm lazy. If you have anything then I'll try it. Thanks.

---

### Post by dave00001 on 2011-02-28
1)simply make a text file like this:


naca 0012
oper
visc
100000
alfa 5

quit

2)Save it as "xfoil.run"

3)run it with:

xfoil <xfoil.run> logfile

4) you're done.  The output will be printed to the logfile.  Basically, anything you put in the xfoil.run file will be the commands taken into xfoil.  

good luck - sorry I'm a year late :)

---


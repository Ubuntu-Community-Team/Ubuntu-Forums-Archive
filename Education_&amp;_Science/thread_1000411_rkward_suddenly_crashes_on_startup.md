---
title: "rkward suddenly crashes on startup"
date: 2008-12-02
forum: Education &amp; Science
---

### Post by spamalot on 2008-12-02
hello,
i was using rkward and suddently it crashed. can't relaunch either. completely removed software and reinstalled. to no avail.

thanks!

@ubuntu:~$ rkward

R version 2.8.0 (2008-10-20)
Copyright (C) 2008 The R Foundation for Statistical Computing
ISBN 3-900051-07-0

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

  Natural language support but running in an English locale

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

Error in load(name, envir = .GlobalEnv) : 
  value of 'SET_ATTRIB' must be a pairlist or NULL, not a 'list'
Fatal error: unable to restore saved data in .RData

ASSERT failure in QCoreApplication::sendEvent: "Cannot send events to objects owned by a different thread. Current thread a02f10. Receiver '' (of type 'KNotificationManager') was created in thread 7635f0", file kernel/qcoreapplication.cpp, line 274
KCrash: crashing... crashRecursionCounter = 2
KCrash: Application Name = rkward path = <unknown> pid = 9654
sock_file=/home/er/.kde4/socket-ubuntu/kdeinit4__0
rkward: Fatal IO error: client killed

---

### Post by spamalot on 2008-12-02
found a *related* thread, the difference is have been using the same version of R and Ubuntu w/o problem for a while (weeks).

[http://ubuntuforums.org/showthread.php?p=6206508](http://ubuntuforums.org/showthread.php?p=6206508)

---

### Post by spamalot on 2008-12-02
ps: R version 2.8.0 (2008-10-20)

---

### Post by spamalot on 2008-12-02
Standalone R does not work either, except if I specify R --vanilla. Rkward probably not at fault then. Problem is similar to (.Rdata etc.)

[https://stat.ethz.ch/pipermail/r-help/2008-June/163685.html](https://stat.ethz.ch/pipermail/r-help/2008-June/163685.html)

That is it. Issue resolved.

---


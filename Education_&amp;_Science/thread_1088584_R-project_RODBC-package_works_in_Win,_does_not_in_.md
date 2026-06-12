---
title: "R-project: RODBC-package works in Win, does not in Ubuntu"
date: 2009-03-06
forum: Education &amp; Science
---

### Post by asdir on 2009-03-06
Hi guys,

when I try to use RODBC to get a channel to an Excel file, I get the following error:

ex = odbcConnect("Crude Rape Oil Data worksheet 050309.xls")
Warning messages:
1: In odbcDriverConnect(st, ...) :
  [RODBC] ERROR: state IM012, code 0, message [unixODBC][Driver Manager]DRIVER keyword syntax error
2: In odbcDriverConnect(st, ...) : ODBC connection failed


Obviously the RODBC-library is loaded, so that is not the problem. Moreover I installed it via synaptic, so there should not be dependency issues either. So, what is the problem and how do I solve it?

I had similar problems with R under Linux before and it always worked under Windows. Is there something in particular that is causing this? Or did I forget one step when I installed R?

---

### Post by asdir on 2009-03-06
After a lot of googling and fiddling with R and my system, I found that a package (and maybe some symlinks) are missing. I posted a bug and reported my solution: 

[https://bugs.launchpad.net/ubuntu/+source/rodbc/+bug/338824](https://bugs.launchpad.net/ubuntu/+source/rodbc/+bug/338824)

Moreover it might be necessary to use the symlinks described in the following link. I used them and at least it did not hurt.

[http://lists.freebsd.org/pipermail/freebsd-questions/2005-November/103939.html](http://lists.freebsd.org/pipermail/freebsd-questions/2005-November/103939.html)

Boy, am I glad that the time I lost on this is work time and not my own. :-)

---

### Post by asdir on 2009-03-06
Seems I was too quick. The RODBC package was installed ok, but the original problem persists. Suggestions anyone?

---

### Post by ahmatti on 2009-03-06
I think you can only use RODBC to read excel files in windows.  (this is be mentioned in the package help if I remember correctly). There is a function read.xls in package gdata, which can be used to read excel files to R.

---

### Post by asdir on 2009-03-08
Is there a method then to read .ods-files directly (other than converting them to xls and taking gdata or converting to csv)? 

Anyway: Thanks for your answer. That means that R still works as well under Linux as under Windows. :-)

---

### Post by ahmatti on 2009-03-09
Google brings up this post in the R mailing list: [https://stat.ethz.ch/pipermail/r-help/2009-February/187130.html](https://stat.ethz.ch/pipermail/r-help/2009-February/187130.html). Apparently there is a package for what you need [http://www.omegahat.org/ROpenOffice/](http://www.omegahat.org/ROpenOffice/) .

---


---
title: "DCP 150C Scanner in 8.10 not working"
date: 2009-01-09
forum: General Help
---

### Post by ronjan41 on 2009-01-09
I have got the printer working but XSane does not recognise my Brother DCP 150C scanner.

---

### Post by adamlau on 2009-01-09
Your scanner does not appear to be supported by the SANE backend in either stable, or CVS:

[http://www.sane-project.org/sane-mfgs.html#Z-BROTHER](http://www.sane-project.org/sane-mfgs.html#Z-BROTHER)
[http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-BROTHER](http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-BROTHER)

---

### Post by plucky on 2009-01-09
You have to install the scanner driver from the Brother website.

See this [link](http://solutions.brother.com/linux/en_us/download_scn.html) for the download location.The install instructions are also on the website.Read carefully and make sure you fulfill all the pre-requisites.
You need to use the .deb file to install.


Good Luck

---


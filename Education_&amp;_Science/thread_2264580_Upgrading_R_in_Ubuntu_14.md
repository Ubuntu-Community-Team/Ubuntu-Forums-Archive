---
title: "Upgrading R in Ubuntu 14"
date: 2015-02-08
forum: Education &amp; Science
---

### Post by Antonio_Martin on 2015-02-08
I'm using R version 3.0.2 and I'd like to upgrade it to version 3.1.2 on Ubuntu 14.04 LTS.

I've tried to do all this:

[I]sudo gedit /etc/apt/sources.list
# deb [http://cran.es.r-project.org/bin/linux/ubuntu](http://cran.es.r-project.org/bin/linux/ubuntu) trusty/
[FONT=Consolas]gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9
[/FONT][FONT=Consolas]gpg -a --export E084DAB9 | sudo apt-key add -
[/FONT]sudo apt-get update
sudo apt-get upgrade
[/I]
However, I cannot upgrade the program:

[I]R.Version()
[/I]*$version.string*
*[1] "R version 3.0.2 (2013-09-25)"*

Could anyone help me?

---

### Post by steeldriver on 2015-02-08
The # character indicates the start of a comment line - did you remove that? otherwise the cran.es.r-project.org repository will be ignored

---

### Post by Antonio_Martin on 2015-02-09
That was the problem. Thank you :)

---


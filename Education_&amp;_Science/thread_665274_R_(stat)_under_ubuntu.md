---
title: "R (stat) under ubuntu"
date: 2008-01-12
forum: Education &amp; Science
---

### Post by htex on 2008-01-12
Hello all;
I want to know how I can install R project in my ubuntu desktop 6.10.
knowing that I haven't internet connection. what binary packages taht i must download.
Thant you in advance

---

### Post by mali2297 on 2008-01-12
I guess that you could download [r-base-core]("http://packages.ubuntu.com/edgy/math/r-base-core") together with its dependencies, but I would find it somewhat cumbersome.

---

### Post by euler_fan on 2008-01-13
My preferred method is to follow the directions from [CRAN]("http://cran.r-project.org/") on adding a sources.list entry then installing through Synaptic.

Thing is, Edgy is no longer supported. but you can still get the packages up to the point they stopped updating their .deb repository. The add-on packages should mostly still work for a good while though.

---

### Post by hzambran_cl on 2008-01-17
I didn't use Ubuntu 6.10, but in the last two versions R packages are included  in the original Ubuntu Live DVD (I use the DVD because I don't have internet connection in my house, and this DVD comes with a lot of packages not provided in the default installation CD). You can download the Live DVD from:

[http://nginyang.uvt.nl/](http://nginyang.uvt.nl/)

My advice, for a good starting point with R, is to install the following:

$ sudo apt-get install build-essential g77 	#just in case...
$ sudo apt-get install r-base r-recommended
$ sudo apt-get install r-base-dev 

You can find additional packages looking for "r-cran" in Synaptic.

Regards.

Mauricio

---

### Post by htex on 2008-01-20
Thank u for your help.

---

### Post by shaunsmith_99 on 2009-09-27
Thanks for the help!! I used R back with Fiesty Fawn, and I could have SWORN that I cruized by it in the add/remove programs tab and now nothing! huh. :confused::confused: Well, these directions you posted here work great - thanks!

---


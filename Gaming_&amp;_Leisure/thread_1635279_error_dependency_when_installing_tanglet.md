---
title: "error dependency when installing tanglet"
date: 2010-12-01
forum: Gaming &amp; Leisure
---

### Post by kn0c on 2010-12-01
I downloaded the ubuntu deb file to tanglet from [http://gottcode.org/tanglet/](http://gottcode.org/tanglet/) when i tried installing i get this error

Error: Dependency is not satisfiable: libqtcore4 (>= 4:4.7.0~beta1)
When i look in the synaptic and it says i already have that installed.
I'm using lucid netbook remix. 

Any feedback would be appreciated. Thanks

---

### Post by Perfect Storm on 2010-12-02
Lucid have version 4.4.6 of that file [http://packages.ubuntu.com/search?keywords=libqtcore4&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=libqtcore4&searchon=names&suite=lucid&section=all)

That is why it doesn't work.

---

### Post by hantms on 2010-12-14
So does Maverick.   Any guess when libqtcore4 >= 4:4.7.0~beta1 will be availasble for Ubuntu?  

Cannot install Virtualbox without it.

---

### Post by sohail_linux on 2010-12-15
add tangliet in /etc/apt/sources.list and the **aptitude update **, then search the package by **aptitude search pkg-name  **if it is listed there then **aptitude install pkg-name.  **if there was no apt source path of tanglite , then install the dependent package using **aptitude **(it will resolve all dependencies itself), and the install tanglite pkg using **dpkg -i pkg-name.deb**

---


---
title: "Ubuntu unity interface"
date: 2011-01-23
forum: Desktop Environments
---

### Post by zainlodhi on 2011-01-23
I have windows 7 installed on my PC but I am using Ubuntu 10.10 as a virtual machine using virtualbox. I installed unity interface in Ubuntu but it is not working giving me an error of CD live etc. 
Before this I was using Ubuntu on my PC not in virtual box but as a real one installed on my PC and with that Unity interface was working properly but in virtual box it has some sort of problem which i am not getting either hardware or software?

---

### Post by zainlodhi on 2011-01-23
I am not getting its solution guys .....

---

### Post by 3Miro on 2011-01-23
Unity requires 3D graphics acceleration. Virtual Box has a bad 3D graphics support. Try enabling it and installing the VB guest addons (it is in the VB manual). However, most likely you will not be able to run Unity in Virtual Box.

---

### Post by zainlodhi on 2011-03-01
Could u tell me the names of the VB guest addons which are required for running the Ubuntu unity interface in virtual box?

---

### Post by 3Miro on 2011-03-01
> **zainlodhi said:**
> Could u tell me the names of the VB guest addons which are required for running the Ubuntu unity interface in virtual box?

Go to the Virtual Box web-page and get the manual:

[http://www.virtualbox.org/wiki/Documentation](http://www.virtualbox.org/wiki/Documentation)

This is exactly what you need:

[http://www.virtualbox.org/manual/ch04.html#id404776](http://www.virtualbox.org/manual/ch04.html#id404776)

Also check the section for 3D acceleration and how to set it.

[http://www.virtualbox.org/manual/ch04.html#guestadd-3d](http://www.virtualbox.org/manual/ch04.html#guestadd-3d)

The .pdf manual has more pictures in it, you may like it better than the links above.

As I said before, this may or may not work ...

---


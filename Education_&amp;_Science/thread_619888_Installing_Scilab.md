---
title: "Installing Scilab"
date: 2007-11-21
forum: Education &amp; Science
---

### Post by earendil1234 on 2007-11-21
Hi all,

I am new to Ubuntu and would like to install the Scilab software.
I have typed in the 
sudo apt-get install scilab

but this is the response that I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package scilab is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package scilab has no installation candidate

How should I tackle this problem? 

BTW, I have downloaded the scilab-4.1.2-src.tar.gz from the website as well... but I dont know how to proceed...


Thanks

---

### Post by akniss on 2007-11-22
Go to System > Administration > Synaptic Package Manager
Under the Settings menu, choose Repositories.
Make sure the fourth choice (multiverse) has a check next to it, then click close.
Now if you search for scilab, you should be able to right click on scilab, and choose Mark for Installation.

---

### Post by earendil1234 on 2007-11-22
Thanks! It works now. :)

---

### Post by afrodeity on 2011-08-23
Anybody know where to put modules? Which directory is the default?

---


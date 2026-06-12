---
title: "[SOLVED] Crysta+Kubuntu 7.10"
date: 2008-01-29
forum: Desktop Effects &amp; Customization
---

### Post by dynamethod on 2008-01-29
SOLVED: i just ran sudo apt-get install --reinstall x-dev libx11-dev kdebase-dev and this fixed the problem :-)


Hi there, im trying to install the Crystal tar from : 
[http://www.kubuntu-art.org/content/show.php?content=13969&forumpage=2&PHPSESSID=df1c1c24ea96962c880c7eebd0ee9d9d](http://www.kubuntu-art.org/content/show.php?content=13969&forumpage=2&PHPSESSID=df1c1c24ea96962c880c7eebd0ee9d9d)

i currently have installed the default 1.0.3 version

but when i try to configure the version from the above link with:

./configure --prefix=`kde-config --prefix`   

i get this error:

checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!

so was wondering how do i go about fixing this problem?  baring in mind i dont know alot about configuring etc, thanks!

---

### Post by luisromangz on 2008-01-29
You need to install the header packages needed by the program you are trying to compile. If you have installed a previous version, chances are that the dependencies of both versions are the same, so you can make apt-get download the build dependencies with this command:

sudo apt-get build-dep kwin-style-crystal

---

### Post by dynamethod on 2008-01-29
cool tyvm for the info, im getting this though: 

E: Unable to find a source package for kwin-style-crystal

---

### Post by dynamethod on 2008-01-29
this is bizarre because this same error is coming up when i try to configure ANY source file:

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

whats up with this?

---

### Post by dynamethod on 2008-01-29
and i have libx11-dev installed too btw

---


---
title: "How to Install UFRAW 0.15?"
date: 2009-02-10
forum: General Help
---

### Post by mattlach on 2009-02-10
Hey all,

I searched in synaptic and found that the Interpid repository only contains UFRAW .13.  My particular camera model requires version .15

Is there a way to install newer versions of the software?

---

### Post by ibuclaw on 2009-02-10
You could manually compile it.

[NOTE]
To paste you will require a Terminal open:
**Applications -> Accessories -> Terminal**
To paste into a terminal, press: **Ctrl+Shift+V**

To install the build dependencies:
```
sudo apt-get build-dep ufraw
```

[EDIT]
After asking an affiliate who is using Intrepid to test this, he reported that you are required to explicitly install the **liblcms1-dev** package in intrepid.
```
sudo apt-get install liblcms1-dev
``` 

Then download the sourcecode/patches from the Jaunty Source Repos using this rather long command:
```
wget http://archive.ubuntu.com/ubuntu/pool/universe/u/ufraw/ufraw_0.15.orig.tar.gz; wget http://archive.ubuntu.com/ubuntu/pool/universe/u/ufraw/ufraw_0.15-1.diff.gz; tar -xf ufraw_0.15.orig.tar.gz; cd ufraw-0.15/ && zcat ../ufraw_0.15-1.diff.gz | patch -p1
```

Then configure and compile the application for your computer.
```
./configure && make
```
then install
```
sudo make install
```


Hopefully that should have you all set.


Regards
Iain

---

### Post by mattlach on 2009-02-10
Thank you, I appreciate your help.  

I am very familiar with compiling my own software using make (especially after my many years with Gentoo.)

I was concerned this might break dependencies.
What I did - instead - was to download a deb package of this version of the software from an ubuntu mirror, and installed the package by double clicking on it.  This automatically figured out the dependencies, and made sure my dependency tree was maintained.

I only ever compile stuff from source if I absolutely have to, because I like keeping stuff clean, and linked to the package manager and dependency tree at all times.

---

### Post by ibuclaw on 2009-02-11
You can build deb packages from sources.

Here is an example HOWTo listed on these forums:
[http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)


Or you could opt for a more automated installation with the package **checkinstall**.
That is, instead of running **sudo make install**, you run
```
sudo checkinstall
```
instead.

But it is not aways guaranteed to build successfully unlike manual building ...

Regards
Iain

---

### Post by mcduck on 2009-02-11
You can also get .deb packag for UFRaw from getdeb.net: [http://www.getdeb.net/app/UFRaw]("http://www.getdeb.net/app/UFRaw")

---


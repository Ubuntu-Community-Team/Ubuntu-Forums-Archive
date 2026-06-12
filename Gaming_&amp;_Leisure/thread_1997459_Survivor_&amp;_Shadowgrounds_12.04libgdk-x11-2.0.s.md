---
title: "Survivor &amp; Shadowgrounds 12.04libgdk-x11-2.0.so.0: undefined symbol: _XGetRequest"
date: 2012-06-05
forum: Gaming &amp; Leisure
---

### Post by tuppe666 on 2012-06-05
After finally getting trine working on Sandybridge. I thought I would try Survior and Shadowgrounds again. After unziping the .run file and copying liglade2 into the lib32 directory. I think I am almost working. Unfortunately I now get

```
./survivor-launcher 
./survivor-launcher: symbol lookup error: /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0: undefined symbol: _XGetRequest

```

Any help is appreciated

---

### Post by Perfect Storm on 2012-06-05
Try instead remove the lib your moved, then install ia32-libs

```
sudo apt-get install ia32-libs
```

---

### Post by tuppe666 on 2012-06-05
without libglade-2.0.so.0 added to lib32 directory it fails like this :)

```
./survivor-launcher 
./survivor-launcher: error while loading shared libraries: libglade-2.0.so.0: cannot open shared object file: No such file or directory

```

---

### Post by Perfect Storm on 2012-06-05
I guess you downloaded the 32-bit package and extracted libglade from here; [http://packages.ubuntu.com/precise/i386/libglade2-0/download](http://packages.ubuntu.com/precise/i386/libglade2-0/download)

Another way, if you bought shadow grounds via humble Bundle you can revoke the game in Desura - then install it that way as it will take care of the libs for for you.

---

### Post by tuppe666 on 2012-06-05
Yes I copied the file from there...but I am still left with the error afterwards "undefined symbol: _XGetRequest"

---

### Post by orbus on 2012-08-29
> **tuppe666 said:**
> Yes I copied the file from there...but I am still left with the error afterwards "undefined symbol: _XGetRequest"
Hi,

Is there any solution about this?
Anyone?

---

### Post by boddhisatva on 2012-11-16
I've found a solution. Download this package:
[http://packages.ubuntu.com/oneiric/i386/libgtk2.0-0/download](http://packages.ubuntu.com/oneiric/i386/libgtk2.0-0/download)
Unpack the the files **libgdk-x11-2.0.so.0** and **libgdk-x11-2.0.so.0.2400.6** from the archive **data.tar.gz** inside the package and move these two files as root to 
**/usr/lib/i386-linux-gnu/**
Overwrite or (safer) rename the original file.

---


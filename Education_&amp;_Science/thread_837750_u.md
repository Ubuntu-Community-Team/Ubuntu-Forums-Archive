---
title: "u"
date: 2008-06-22
forum: Education &amp; Science
---

### Post by ayesha kalra on 2008-06-22
Hi all

I just upgraded to Hardy and found that octave is not starting now. This is the error message I am getting

```

octave: error while loading shared libraries: libumfpack.so.1: cannot open shared object file: No such file or directory

```

Obviously, I do not have libumfpack.so.1, or do not have it at the right location, or there is a name change involved. Any suggestions here will be helpful.

Thanks
Ayesha

---

### Post by mali2297 on 2008-06-24
Have you tried reinstalling octave?

There is a file libumfpack.so.3.1.0 in [libsuitesparse-3.1.0]("http://packages.ubuntu.com/hardy/i386/libsuitesparse-3.1.0/filelist"). Do you have that package?

---

### Post by thisismalhotra on 2008-06-24
Double post lol

try ..

```
sudo apt-get update
sudo apt-get build-dep octave
```

---

### Post by hugmenot on 2008-06-24
why build-dep?

---

### Post by ayesha kalra on 2008-06-24
@thisismalhotra - 

sudo apt-get build-dep octave 

did not work. However, 

sudo apt-get build-dep octave3.0

gave the following error message 

The following NEW packages will be installed:
  libqhull-dev libsuitesparse-dev
0 upgraded, 2 newly installed, 0 to remove and 19 not upgraded.
Need to get 1794kB of archives.
After this operation, 6341kB of additional disk space will be used.
Do you want to continue [Y/n]?

I upgraded. Octave still does not start. 

This is the error message:


octave: error while loading shared libraries: libumfpack.so.1: cannot open shared object file: No such file or directory


Ayesha

---

### Post by hugmenot on 2008-06-24
The apt-get build-dep was noise actually.
Do you have libsuitesparse installed? If not install it.

[See here]("http://packages.ubuntu.com/search?mode=filename&suite=gutsy&section=all&arch=i386&searchon=contents&keywords=libumfpack.so.1")

---


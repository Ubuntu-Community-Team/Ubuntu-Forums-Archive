---
title: "C compiler for Ubuntu"
date: 2009-02-24
forum: General Help
---

### Post by sudheerah on 2009-02-24
Where to get C compiler to install in Ubuntu.


Thax
Shabar

---

### Post by geirha on 2009-02-24
Install the [build-essential](apt:build-essential) package. It will install gcc, make and some other commonly used tools for development. 

```
gcc hello.c
./a.out
```

---

### Post by sudheerah on 2009-02-24
Hi geirha,

Thax for quick reply....

Is this 7K in size?
Could you elaborate on installation steps


Thax

Shabar

---

### Post by geirha on 2009-02-24
It's probably around 15MiB in total, with the libraries taking up most of that space. To install, click the link in my first post, or go to System -> Administration -> Synaptic package manager, search for build-essential and install it. A third way to install it is to type in a terminal: ```
sudo aptitude install build-essential
```

---

### Post by sudheerah on 2009-02-24
All downloaded installation files are (build-essential_11.4_i386.deb) around 7-8 KB. You meant 15 MB after installation, Is it?

---

### Post by geirha on 2009-02-24
Ah, yes uncompressed size. That's including the dependencies of build-essential, which include gcc, g++, libc6-dev, make and dpkg-dev.

---

### Post by jacksaff on 2009-02-24
build-essential is a meta-package. It contains nothing itself except for a list of all the packages considered essential for compiling programs.
Hence build-essential is just 7kB, but when you install it using a package manager such as aptitude (sudo aptitude install build-essential) the package manager will automatically download and install all of the essential packages. So typing that command will download about 15MB.

---

### Post by sudheerah on 2009-02-24
Thax a lot guys...

Have a nice day

---


---
title: "Problem with glade"
date: 2005-02-23
forum: Desktop Environments
---

### Post by Dearhell on 2005-02-23
I have installed glade-2 with apt-get.

I also have installed this packages: 

glade-common-2
glade-gnome-2
libglade2-0
libglade2-dev

I use this command in order to compile: 

gcc program.c -o program `pkg-config --cflags --libs libglade-2.0`

But I have a problem when I try to compiling a program: 

> Package libglade-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libglade-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libglade-2.0' found


I have searched on google to fix this problem, but I can't find any succesful solution. 

libglade-2.0 it's perfectly installed, I don't know why this error appears. 

Any idea would be welcome

Regards

---

### Post by Dearhell on 2005-02-23
I have fixed it, it seems that libgtk2-dev didn't download well, I have downloaded it again and now at last works fine.  \\:D/

---

### Post by BabyUbuntu on 2005-06-19
i tried to install libglade2-dev.. but i got problem

root@babyuubuntu:~ # apt-get install libglade2-dev
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.2.ds1-20ubuntu13) but 2.3.2.ds1-22 is to be installed
  libc6-i686: PreDepends: libc6 (= 2.3.2.ds1-20ubuntu13) but 2.3.2.ds1-22 is to be installed
  libfontconfig1-dev: Depends: libfontconfig1 (= 2.2.3-4ubuntu7) but 2.3.2-1 is to be installed
  libxft-dev: Depends: libxft2 (= 2.1.2-6ubuntu1) but 2.1.7-1 is to be installed
  locales: Depends: glibc-2.3.2.ds1-20ubuntu13
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@babyubuntu:~ #

root@babyubuntu:~ # apt-get -f install libglade2-dev
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.2.ds1-20ubuntu13) but 2.3.2.ds1-22 is to be installed
  libc6-i686: PreDepends: libc6 (= 2.3.2.ds1-20ubuntu13) but 2.3.2.ds1-22 is to be installed
  libfontconfig1-dev: Depends: libfontconfig1 (= 2.2.3-4ubuntu7) but 2.3.2-1 is to be installed
  libxft-dev: Depends: libxft2 (= 2.1.2-6ubuntu1) but 2.1.7-1 is to be installed
  locales: Depends: glibc-2.3.2.ds1-20ubuntu13
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@babyubuntu:~ #

what i have to do? delete installed packages above and install ubuntu packages ?
thank u

---


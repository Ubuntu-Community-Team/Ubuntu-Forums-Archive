---
title: "devel packages"
date: 2005-10-28
forum: Desktop Environments
---

### Post by anono on 2005-10-28
I'm trying to compile and it won't work.
Where can I find glib2-devel and glibc-devel?
Now he says the packages can't be found, can someone give me a source to add?

---

### Post by Remmelas on 2005-10-28
apt-cache search glib2 | grep dev
outputs:
libpolyp0-glib2.0-dev - Library for the polypaudio sound server
libglib2.0-dev - Development files for the GLib library
so, sudo apt-get install libglib2.0-dev

---

### Post by anono on 2005-10-28
Thank you, but it still does not work.

peter@anna:/home/peter/Desktop/appletouch-0.08# make
make -C /lib/modules/2.6.12-9-powerpc/build SUBDIRS=/home/peter/Desktop/appletouch-0.08 modules
make: *** /lib/modules/2.6.12-9-powerpc/build: No such file or directory.  Stop.
make: *** [default] Error 2

What would I be missing?

---

### Post by anono on 2005-10-29
Sorry for kicking this one but I really need help please, someone.

---

### Post by Trab on 2005-10-29
[QUOTE=anono]Sorry for kicking this one but I really need help please, someone.[/QUOTE]

why are u doing it the hard way? does ur software not have a .deb or .rpm somewhere that can be converted?
it looks like ur missing something needed for make, i forget what the files are called, but look around in synaptic...
u need the c complier no?

.deb and .rpm would really simplify ur life :-D
```
sudo alien *.rpm
```
then/or
```
sudo dpkg -i *.deb
```

---

### Post by Ugeek on 2005-10-29
its in main repository. if u are connected to internet u should be able to install it through synaptic, otherwise go to packages.ubuntu.com.
cheers

---

### Post by anono on 2005-10-29
ok, but I need the 0.14.3 version. it is *not* included in breezy!
apt tells you it does but it is not, it's an older one.
check it  ;-)

but it's allright, it compiled, I did lack header files.
thanks

---


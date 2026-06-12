---
title: "dpkg erroe  HELP ME PLEASE"
date: 2006-08-07
forum: Desktop Environments
---

### Post by Magiczero on 2006-08-07
Hi I am getting this error when I open Synaptic HELP ME!!

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

What is this? How do I fix it?  I have ran sudo dpkg --configure -a in terminal and I get this


tanner@ubuntu:~$ sudo dpkg --configure
Password:
dpkg: --configure needs at least one package name argument

Type dpkg --help for help about installing and deinstalling packages[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL)[*].

Options marked[*] produce a lot of output - pipe it through `less' or `more' !
tanner@ubuntu:~$


What do I do now?  How can I fix this problem?

Thanks

---

### Post by Ramses de Norre on 2006-08-07
```
sudo dpkg --configure **-a**
```

---

### Post by Magiczero on 2006-08-07
Thanks

---


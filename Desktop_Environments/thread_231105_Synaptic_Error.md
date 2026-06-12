---
title: "Synaptic Error"
date: 2006-08-06
forum: Desktop Environments
---

### Post by Magiczero on 2006-08-06
Hi  I am getting this error when I open Synaptic HELP ME!!

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

What is this?  How do I fix it?

---

### Post by codypumper on 2006-08-06
Have you tried running sudo dpkg --configure -a in terminal?

---

### Post by Magiczero on 2006-08-07
yes I have and here is what I get..

tanner@ubuntu:~$ sudo dpkg --configure
Password:
dpkg: --configure needs at least one package name argument

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
tanner@ubuntu:~$




what do I now?  

Thanks

---

### Post by dans0n on 2006-08-07
you forgot the "-a"

---


---
title: "Installing setserial package?"
date: 2009-06-22
forum: General Help
---

### Post by HawkeyeGuru on 2009-06-22
I want to install the package 'setserial'  on a fujutsu 3500.   I've got the file setserial-2.17.tar.gz  on my desktop an have the untarred file in a dir called 'package'.   It is not a .deb package.  .  I've tried running 'apt-get install setserial-2.17'  from the package dir. It says couldn't find package setserial-2.17.
 
Some one please explane how to install this.
 
Thanks

---

### Post by michy99 on 2009-06-22
setserial is in the repositories. You should be able to install it with```
sudo apt-get install setserial
```What you downloaded is probably source files which would have to be compiled first. Try the apt-get  install instead.

---

### Post by HawkeyeGuru on 2009-06-22
I should have said that I don't have a working internet connection either.

---

### Post by michy99 on 2009-06-22
If it is source code, you can try to compile and install, but you might run into the problem that you don't have some file that the code depends on. Also, if you have not compiled before, you probably don't have the tools installed to compile with.

The usual way to install from source code is:```
./configure
make
sudo make install
```

---

### Post by HawkeyeGuru on 2009-06-22
Thanks, but that is way over my head.

---

### Post by oofnik on 2009-06-23
Did you install from a CD? If so, you should be able to use the CD as a repository.

Also, you can download the package from a repository mirror manually from another computer and install it that way. [Here's a link.]("http://archive.ubuntu.com/ubuntu/pool/main/s/setserial/setserial_2.17-45_i386.deb")

---


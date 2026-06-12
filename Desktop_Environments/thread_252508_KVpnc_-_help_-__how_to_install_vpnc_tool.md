---
title: "KVpnc - help -  how to install vpnc tool"
date: 2006-09-06
forum: Desktop Environments
---

### Post by eschreib on 2006-09-06
Greetings friends, I have installed KVpnc [specifically KVpnc 0.8.2.1-0ubuntu3] on ubuntu (2.6.15-26-386).
I got the vpnc tarball [vpnc-0.3.3.tar.gz]-> extracted to my ./desktop [folder vpnc-0.3.3].
I went in terminal as su, and tried to 'make', with errors below.  

Any assistance appreciated.

ed d0t  schreibman  +  gmail  d0t  com 

==Begin Make file vomit trail =====

root@xcx:/home/eschreibman/Desktop/vpnc-0.3.3# make
make: libgcrypt-config: Command not found
gcc -W -Wall -O -g '-DVERSION="0.3.3"'    -c -o vpnc.o vpnc.c
vpnc.c:40:20: error: gcrypt.h: No such file or directory
vpnc.c:102: error: ‘GCRY_MD_MD5’ undeclared here (not in a function)
vpnc.c:103: error: ‘GCRY_MD_SHA1’ undeclared here (not in a function)
and so on........

---

### Post by nick-jopa on 2006-12-09
Hello
I have the same problem under kubuntu:( Could anyone help, plz?

---

### Post by shutterbc on 2006-12-26
I'm taking a guess here but it looks like libgcrypt-config is missing.  Is libgcrypt11 installed?

---

### Post by runux on 2007-10-26
Check in /usr/bin whether there is libgcrypt-config file or not.
If its not there then install the following package:

apt-get install libgcrypt11-dev

then the problem "libgcrypt-config command-not found" will be solved.
I hope it will work.8-)

---


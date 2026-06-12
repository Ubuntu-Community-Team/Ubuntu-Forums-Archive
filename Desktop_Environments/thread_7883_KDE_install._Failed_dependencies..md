---
title: "KDE install. Failed dependencies."
date: 2004-12-12
forum: Desktop Environments
---

### Post by gwon on 2004-12-12
I reinstalled Ubuntu from CD this morning, since I was finally able to use my entire hard disk for linux.

I'm trying to install KDE, but whenever I run 'sudo apt-get install kde' I get the folling message. Should I be installing something else first?

```
craig@ubuntu:~ $ sudo apt-get install kde
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde: Depends: kde-core but it is not going to be installed
       Depends: kde-amusements but it is not going to be installed
       Depends: kdeaddons but it is not going to be installed
       Depends: kdeadmin but it is not going to be installed
       Depends: kdeartwork but it is not going to be installed
       Depends: kdegraphics but it is not going to be installed
       Depends: kdemultimedia but it is not going to be installed
       Depends: kdenetwork but it is not going to be installed
       Depends: kdepim but it is not going to be installed
       Depends: kdeutils but it is not going to be installed
       Depends: quanta but it is not going to be installed
E: Broken packages

```


My sources.list:

```
deb http://archive.ubuntu.com/ubuntu/ warty universe
deb-src http://archive.ubuntu.com/ubuntu/ warty universe
deb http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ warty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ warty multiverse
deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main
```

---

### Post by l33tman on 2004-12-12
I booted into recovery mode and did the apt-get and kde installed but then my user password did not work nor root passwd. Any ideas? 

l33tman :o

---

### Post by gwon on 2004-12-12
I answered my own question. I had messed up with the sources.list

changed to:

```
deb http://archive.ubuntu.com/ubuntu/ warty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted
deb http://archive.ubuntu.com/ubuntu/ warty universe
deb-src http://archive.ubuntu.com/ubuntu/ warty universe
deb http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ warty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ warty multiverse
deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main
```

---


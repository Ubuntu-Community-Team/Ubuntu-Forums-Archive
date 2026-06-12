---
title: "Dependencies problems when installing JAVA"
date: 2006-06-29
forum: Desktop Environments
---

### Post by sliorda on 2006-06-29
My /etc/apt/sources.list is:
```
deb http://www.beerorkid.com/compiz dapper main
deb http://xgl.compiz.info/ dapper main

deb http://il.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://il.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

deb http://il.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://il.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

deb http://il.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://il.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

```

When trying to install JAVA plugin to firefox, i got this:
```
root@laptopy:~# apt-get install sun-java5-jre
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  j2re1.4-mozilla-plugin: Depends: j2re1.4 but it is not going to be installed
  sun-java5-jre: Depends: sun-java5-bin (= 1.5.0-06-1) but it is not going to be installed or
                          ia32-sun-java5-bin (= 1.5.0-06-1) but it is not installable
  sun-java5-plugin: Depends: sun-java5-bin (= 1.5.0-06-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

I've tried with the "-f" flag, but it didn't work either.

Any tips?

---


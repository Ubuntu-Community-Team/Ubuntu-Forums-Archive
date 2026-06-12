---
title: "HowTo install &quot;akonadi-google&quot;"
date: 2011-10-20
forum: Desktop Environments
---

### Post by produnis on 2011-10-20
Hi folks,
this is how I install the akonadi-agent "[akonadi-google]("http://progdan.cz/2011/09/akonadi-google-resource-tasks-support/")". This agent allows to sync all of your google-canlendars, contacts and tasks with akonadi. 

This works for me (Kubuntu Oneiric 64bit);


```
sudo apt-get install cmake build-essential kdelibs5-dev kdepimlibs5-dev libqjson-dev libphonon-dev xsltproc
git clone git://anongit.kde.org/akonadi-google
cd akonadi-google
mkdir build
cd build
cmake ../ -DCMAKE_INSTALL_PREFIX=/usr
make
sudo make install
```

After that, you will find the three new agents in the akonadi menu.

---

### Post by jajaX on 2011-11-25
Hi ! (sorry for my bad english !)

before a big thanks ;)

next, I want test that for remove "akonadi-googledata".

I try to install "akonadi-google" but I have got an error.

I must install "libakonadi-dev" too ;)

not need to restart akonadi server, it's fine :P

big thanks again !!!

---

### Post by jajaX on 2011-11-26
Hi !

add "pkg-config" (for packages obligatory).

thanks ;)

---

### Post by TomB19 on 2011-11-29
I'm staggered to read someone has akonadi working.  I just did a clean install on a system with format and Kontact won't start because of akonadi errors.

---


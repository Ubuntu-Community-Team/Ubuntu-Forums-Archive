---
title: "remove kde"
date: 2008-05-17
forum: Desktop Environments
---

### Post by junaid.kollam on 2008-05-17
I installed ubuntu and installed kubuntu by this command
 sudo apt-get install  kubuntu-kde4-desktop
and i want to remove it.I tried this command
 sudo apt-get remove  kubuntu-kde4-desktop
But i can log into kubuntu now also.How can i remove kde 
from my system?

---

### Post by angry_johnnie on 2008-05-18
kubuntu-kde4-desktop is just a metapackage.  That means it's not really the desktop itself. It just points at packages.  That is why you can still log in to kde4, even after removing it.

Since you installed it with apt-get (google for aptitude versus apt-get to get an idea :-)), what you will have to do is open synaptic (System > Administration > Synaptic), look for all the packages related to kde4, and mark them for complete removal.  It will take some time and patience, but that's the way it goes. :-)

As for the whole aptitude/apt-get thing, take a look [here]("http://psychocats.net/ubuntu/aptitude") and [here]("http://www.pthree.org/2007/08/12/aptitude-vs-apt-get/").  Aptitude is better at keepking track of things, and makes it infinitely easier to remove the stuff you don't want.  Just don't mix them (aptitude and apt-get).  They don't quite get along. :-)

---

### Post by abracadaver on 2008-06-01
> **angry_johnnie said:**
> kubuntu-kde4-desktop is just a metapackage.  That means it's not really the desktop itself. It just points at packages.  That is why you can still log in to kde4, even after removing it.

Since you installed it with apt-get (google for aptitude versus apt-get to get an idea :-)), what you will have to do is open synaptic (System > Administration > Synaptic), look for all the packages related to kde4, and mark them for complete removal.  It will take some time and patience, but that's the way it goes. :-)

As for the whole aptitude/apt-get thing, take a look [here]("http://psychocats.net/ubuntu/aptitude") and [here]("http://www.pthree.org/2007/08/12/aptitude-vs-apt-get/").  Aptitude is better at keepking track of things, and makes it infinitely easier to remove the stuff you don't want.  Just don't mix them (aptitude and apt-get).  They don't quite get along. :-)

I had the same problem and ended up doing this:

apt-cache pkgnames | grep kde4 | xargs sudo apt-get -y autoremove

Try it without the -y first to see what will be removed.

-Shawn

---

### Post by Zorael on 2008-06-02
If KDE4 (as I understand you're referring to?), do this.
```
$ sudo aptitude purge ~nkde4
```

---

### Post by abracadaver on 2008-06-02
> **Zorael said:**
> If KDE4 (as I understand you're referring to?), do this.
```
$ sudo aptitude purge ~nkde4
```

Works, but not everything is removed.  After running your suggestion I run and get this:

$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 libenchant1c2a librdf0 libqt4-qt3support libsqlite0 librasqal0 libsoprano4
  kdelibs5-data libcaptury0 libqt4-sql libphonon4 libkonq5-templates libcapseo0 libraptor1
  kdebase-runtime-data
The following packages will be REMOVED:
  kdebase-runtime-data kdelibs5-data libcapseo0 libcaptury0 libenchant1c2a libkonq5-templates libphonon4
  libqt4-qt3support libqt4-sql libraptor1 librasqal0 librdf0 libsoprano4 libsqlite0 libstrigiqtdbusclient0
0 upgraded, 0 newly installed, 15 to remove and 0 not upgraded.
After this operation, 33.5MB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 168475 files and directories currently installed.)
Removing kdebase-runtime-data ...
Removing kdelibs5-data ...
Removing libcaptury0 ...
Removing libcapseo0 ...
Removing libenchant1c2a ...
Removing libkonq5-templates ...
Removing libphonon4 ...
Removing libqt4-qt3support ...
Removing libqt4-sql ...
Removing libsoprano4 ...
Removing librdf0 ...
Removing librasqal0 ...
Removing libraptor1 ...
Removing libsqlite0 ...
Removing libstrigiqtdbusclient0 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place


-Shawn

---

### Post by fickenbaisage on 2008-06-02
Psychocats(not me) come to the rescue again!

Since you installed kde using apt-get, it;s going to be tricky to remove it, here's a simple guide: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Run the 3rd command from that website to completely remove kde.

---

### Post by Xiong Chiamiov on 2008-06-03
If you use aptitude instead of apt-get there is no need for autoremove, as it does it automatically whenever it runs.

---


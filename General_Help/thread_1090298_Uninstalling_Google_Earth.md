---
title: "Uninstalling Google Earth"
date: 2009-03-08
forum: General Help
---

### Post by ykcirt on 2009-03-08
Hi. I _manually_ installed Google Earth yesterday from the binary at [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

It wasn't working properly today, so I decided to remove it to reinstall at a later time (and use GoogleMaps instead). 

```
~$ sudo apt-get autoremove googleearth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package googleearth

```

That's all I knew and it didn't work. How do I uninstall it properly?

---

### Post by munishvit on 2009-03-08
At this end, same problem I got...
> $ sudo apt-get autoremove googleearth
On my system [COLOR="Red"]Google Earth's window flicks[/COLOR]. Does any body has idea, what can be done in order to make it working on 8.04?

**Edit:**
Indeed, I got the following messages:
root@lappy:/home/munish# apt-get autoremove googleearth
[COLOR="Gray"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package googleearth is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 libpythonize0 librdf0 libqt4-qt3support
  libsearchclient0 libmimelib1c2a libflac++6 python-dev kde-icons-oxygen
  libexiv2-2 librasqal0 python2.5-dev pykdeextensions cryptsetup libsoprano4
  perl-suid libept0 libksba8 gnupg-agent libxapian15 poster libqt4-sql debtags
  libdbus-qt-1-1c2 libphonon4 rdiff-backup ksysguardd libstrigihtmlgui0
  psutils libkonq5-templates libpoppler-qt2 libraptor1 libjpeg-progs
  pinentry-qt librsync1 gpgsm
The following packages will be REMOVED:
  cryptsetup debtags gnupg-agent gpgsm kde-icons-oxygen ksysguardd
  libdbus-qt-1-1c2 libept0 libexiv2-2 libflac++6 libjpeg-progs
  libkonq5-templates libksba8 libmimelib1c2a libphonon4 libpoppler-qt2
  libpythonize0 libqt4-qt3support libqt4-sql libraptor1 librasqal0 librdf0
  librsync1 libsearchclient0 libsoprano4 libstrigihtmlgui0
  libstrigiqtdbusclient0 libxapian15 perl-suid pinentry-qt poster psutils
  pykdeextensions python-dev python2.5-dev rdiff-backup
0 upgraded, 0 newly installed, 36 to remove and 6 not upgraded.
After this operation, 86.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 149965 files and directories currently installed.)
Removing cryptsetup ...
Removing debtags ...
Removing gnupg-agent ...
Removing gpgsm ...
Removing kde-icons-oxygen ...
Removing ksysguardd ...
Removing libdbus-qt-1-1c2 ...
Removing libept0 ...
Removing libexiv2-2 ...
Removing libflac++6 ...
Removing libjpeg-progs ...
Removing libkonq5-templates ...
Removing libksba8 ...
Removing libmimelib1c2a ...
Removing libphonon4 ...
Removing libpoppler-qt2 ...
Removing libpythonize0 ...
Removing libqt4-qt3support ...
Removing libqt4-sql ...
Removing libsoprano4 ...
Removing librdf0 ...
Removing librasqal0 ...
Removing libraptor1 ...
Removing rdiff-backup ...
Removing librsync1 ...
Removing libstrigihtmlgui0 ...
Removing libsearchclient0 ...
Removing libstrigiqtdbusclient0 ...
Removing libxapian15 ...
Removing perl-suid ...
Removing pinentry-qt ...
Removing poster ...
Removing psutils ...
Removing pykdeextensions ...
Removing python-dev ...
Removing python2.5-dev ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place[/COLOR]
root@lappy:/home/munish#

---

### Post by Partyboi2 on 2009-03-08
> **ykcirt said:**
> Hi. I _manually_ installed Google Earth yesterday from the binary at [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

It wasn't working properly today, so I decided to remove it to reinstall at a later time (and use GoogleMaps instead). 

```
~$ sudo apt-get autoremove googleearth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package googleearth

```That's all I knew and it didn't work. How do I uninstall it properly?

Open a terminal and change into /opt/google-earth
```
cd /opt/google-earth
```
then run uninstall
```
./uninstall
```

---

### Post by ykcirt on 2009-03-08
> **Partyboi2 said:**
> Open a terminal and change into /opt/google-earth
```
cd /opt/google-earth
```
then run uninstall
```
./uninstall
```



I get this:
```
/opt/google-earth$ ./uninstall
Could not find a usable uninstall program. Aborting.

```

But I looked at the content of that directory and there is definitely an uninstall there.. strange.

---

### Post by ykcirt on 2009-03-08
Ah, I worked it out. Turned out to be one of those Super User issues. Thanks for the help.

---

### Post by munishvit on 2009-03-08
> **Partyboi2 said:**
> Open a terminal and change into /opt/google-earth
```
cd /opt/google-earth
```
then run uninstall
```
./uninstall
```

Thanks partyboi

---

### Post by roach33 on 2009-03-13
> **ykcirt said:**
> Ah, I worked it out. Turned out to be one of those Super User issues. Thanks for the help.
Care to share?

---

### Post by oldos2er on 2009-03-13
> **roach33 said:**
> Care to share?

 You need to run the uninstall script as root (admin):
```
sudo /opt/google-earth/uninstall
```

---


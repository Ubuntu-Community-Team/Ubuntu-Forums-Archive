---
title: "KVirc is old. Where to get a recent version"
date: 2005-03-27
forum: Desktop Environments
---

### Post by soul_rebel on 2005-03-27
I see the version of KVirc in the repositories is very old, I don't understand why. Maybe it's a licensing issue?
Anyway i have seen a screenshot of a (k)ubuntu desktop with  kvirc 3.x so there should be a way to get a working .deb
Anyone knows where?

---

### Post by soul_rebel on 2005-03-28
Ok i'll reply myself (sometimes happens)
i got the packages the windows way, from the kvirc website:
[http://kvirc.net/?id=releases&platform=unix&version=3.2.0&group=debian](http://kvirc.net/?id=releases&platform=unix&version=3.2.0&group=debian)
I wasn't used to that anymore.

I just don't understand why that package can't be copied in universe
bye

---

### Post by PMO6022 on 2005-03-28
Shows up for me in Hoary:

> pmorris@ubuntu:~ $ apt-cache search kvirc
kvirc - Fully scriptable graphical IRC client with plugin support
kvirc-data - Data files for KVIrc
kvirc-dev - Development files for KVIrc
kvirc-doc - Help files for KVIrc
pmorris@ubuntu:~ $

---

### Post by simple on 2005-05-29
good eye sniper. but that version is 2.1.3 and the latest stable version is 3.2.0, which i want to get and have it install through synaptic. i went and got it from the main site and it's telling me i need x libraries to configure or something, when i do have them installed..so i figured through synaptic it would install better, any help compiling it, when it asks for x libraries which i have installed?

> ################################################################################### CONFIGURE ERROR:
### Can not find the X libraries.
### Make sure that X is installed on your system and try to run configure again,### this time passing the --x-includes and --x-libraries options.
### You may also take a look at the config.log file in this directory,
### that will tell you which checks have failed and maybe more about the
### reason of the failure.
###
### If you use an environment that does not require X support such as Qt-Mac
### you may try to rerun configure with --disable-x-support
################################################################################

---

### Post by simple on 2005-05-29
[QUOTE=simple]good eye sniper. but that version is 2.1.3 and the latest stable version is 3.2.0, which i want to get and have it install through synaptic. i went and got it from the main site and it's telling me i need x libraries to configure or something, when i do have them installed..so i figured through synaptic it would install better, any help compiling it, when it asks for x libraries which i have installed?[/QUOTE]:whistle:

---

### Post by redgilda on 2005-12-19
I would like to update this Kvirc too... on the official website it says

[http://www.kvirc.net/?id=releases&platform=unix&version=3.2.0&group=debian](http://www.kvirc.net/?id=releases&platform=unix&version=3.2.0&group=debian)

that its possible to update from within the system (or so I understood)

> The official debian packages are available at http://ftp.<country>.debian.org/debian/pool/main/k/kvirc/
Debian users can automatically update from KVIrc 2.x by adding the following line to their /etc/apt/sources.list:
 deb http://ftp.<country>.debian.org/debian/ experimental main

but when I try to alter the sources.list - it doesnt really work.. im not sure which URL to put exactly...? and am getting 404 errors, or sth..

help? pr if anyone could point me to an easy way to upgrade Kvirc? Ive no idea how to 'compile sources' or anything......  I just really like Ubuntu, thats all ;-)

---

### Post by Starcraftmazter on 2006-12-29
Yeh, first two links don't work, 3rd one does.

I tried to install the .deb package, says it needs kdelibs4, which is installed. I installed the dev package also, but still won't work :(

---


---
title: "VLC Player offline Installtion help"
date: 2009-01-23
forum: General Help
---

### Post by jrkraj on 2009-01-23
hi friends,

Yesterday I download the vlc player and extract it into my desktop  and type the below codes in terminal but it didn't Install
Please help me.

```
sudo apt-get update
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
```

---

### Post by halovivek on 2009-01-23
> **jrkraj said:**
> hi friends,

Yesterday I download the vlc player and extract it into my desktop  and type the below codes in terminal but it didn't Install
Please help me.

```
sudo apt-get update
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
```

HI the above one are used when you are connected to internet.
Follow these steps.
Go to the desktop and double click the vlc downloaded file. just give the root password and will install automatically

---

### Post by jrkraj on 2009-01-24
I Have downloaded vlc-0.9.8a.tar.bz2 extract files click install file but its like text file.

---

### Post by jrusso2 on 2009-01-24
> **jrkraj said:**
> I Have downloaded vlc-0.9.8a.tar.bz2 extract files click install file but its like text file.

It probably has to be compiled.  Check the readme.  I am sure you will have the same dependency issues.

---

### Post by EXCiD3 on 2009-01-24
You should use [Keryx]("http://keryx.betaserver.org") to download the .deb files and all the dependencies easily.

---

### Post by mb_webguy on 2009-01-24
VLC has a lot of dependencies.  The last time I tried to compile it I spent a long time tracking down and installing those other packages, and it's not something you should attempt offline.

My suggestion would be to download the packages -- you'll need at least vlc and vlc-nox -- from the [Ubuntu package archive]("http://packages.ubuntu.com/search?searchon=names&keywords=vlc") and use those for the offline installation.

---

### Post by x33a on 2009-01-24
get vlc and dependencies from here (latest version 0.9.8a):

[http://archive.getdeb.net/dump/intrepid/vlc/](http://archive.getdeb.net/dump/intrepid/vlc/)

then use: sudo dpkg -i *.deb, and voila!! you have the latest version installed.

---


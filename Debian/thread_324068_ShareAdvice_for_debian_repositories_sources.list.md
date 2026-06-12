---
title: "Share/Advice for debian repositories sources.list"
date: 2006-12-23
forum: Debian
---

### Post by patrick295767 on 2006-12-23
What would you recommand ?

debian: sarge, etch or sid ... 


thx

---

### Post by tturrisi on 2006-12-23
What debian?  sarge, etch or sid (stable, testing or unstable)?
I use etch (testing) and this is my sources.list:
```
deb http://ftp.debian.org/debian/ etch main non-free contrib
deb-src http://ftp.debian.org/debian/ etch main non-free contrib
deb http://security.debian.org/ etch/updates main contrib non-free
deb-src http://security.debian.org/ etch/updates main contrib non-free
deb http://debian-multimedia.org/ etch main
```

debian-multimedia do this to enable:
```
sudo gedit /etc/apt/sources.list

Add the following repository address:
deb http://www.debian-multimedia.org etch main

gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --armor --export 1F41B907 | sudo apt-key add -

sudo apt-get update
```

sudo apt-get install w32codecs libdvdcss2 liblame0  mplayer msttcorefonts

---


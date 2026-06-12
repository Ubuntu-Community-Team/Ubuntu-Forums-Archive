---
title: "Xine"
date: 2005-01-09
forum: Desktop Environments
---

### Post by christooss on 2005-01-09
Which codecs I have to install for xine.

apt-get install w32codecs                               doesn't work

---

### Post by Arbite on 2005-01-09
w32codecs
Divx codecs

Works here
This is how my sources.list looks like

Hope it can be of help


# deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

---

### Post by fng on 2005-01-09
That last line of your sources.list does the trick Arbite.

'w32codecs' inst in the ubuntu-repositories.
edit /etc/apt/sources.list and add the last line of Arbite's example to it.
Save
apt-get update
apt-get install w32codecs

---


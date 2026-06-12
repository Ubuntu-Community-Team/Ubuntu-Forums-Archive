---
title: "Help with Liferea Installation"
date: 2006-01-17
forum: Desktop Environments
---

### Post by tellnes on 2006-01-17
Hei,

I love liferea, its a new version out, its not available using apt-get, i have downloaded a ubuntu dpkg file of it, but is now unsuccessfull installing it, it misses newer versions of div libs and so..
Is there any command i can use with dpkg to install all the neccesary files it needs too..so it downloads the additional libs and vers it needs for liferea 1.0?

-t-

---

### Post by Lambert on 2006-01-17
Did the version you download come from dapper repos? If so all you can do is add dapper repos so dependencies are met but this can really be a bad decision as it could break other things.

I would try to download source and build for your current system first or request an update to the backports for latest version. Backports looks to have .9.7 beta.

[http://prdownloads.sourceforge.net/liferea/liferea-1.0.tar.gz?download]("http://prdownloads.sourceforge.net/liferea/liferea-1.0.tar.gz?download")

edit:
I gave it a shot to see how a compile went and it was very smooth for me.

I already have a lot of extras installed so not sure what you'll need but I would suggest installing build-essential; libgtkhtml2-dev.

Not knowing your experience but believe with a taste for liferea you have some....

download from above link then move to directory and untar file

```
 cd /path/to/file
``` ```
tar zxvf liferea-1.0.tar.gz
``` ```
cd liferea-1.0
``` ```
./configure
``` ```
sudo make && make install
```

---

### Post by shizow on 2006-01-26
is this working with liferea 1.0.2, too?

---


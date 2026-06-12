---
title: "compiling lipstik 2.1"
date: 2005-12-11
forum: General Help
---

### Post by Paool on 2005-12-11
after ./confugure I've got an error:

configure: error: Can't find X includes. Please check your installation and add the correct paths!

I've installed xlibs-static-dev package, but it doesn't solved the problem. What package I need?

sorry for my english :)

---

### Post by Knomefan on 2005-12-11
Hi, the easiest way to make sure that you have everything installed that is needed is to install all the build dependencies for the lipstick version in breezy with:
```
 sudo apt-get build-dep kde-style-lipstick 
```

Now you should have everything you need.

---

### Post by Paool on 2005-12-11
paool@daisy:~$ sudo apt-get build-dep kde-style-lipstick
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci... Gotowe
E: Nie uda&#322;o si&#281; odnale&#378;&#263; &#378;ród&#322;a dla pakietu kde-style-lipstick
paool@daisy:~$


there's no sources for this package :(

---

### Post by Knomefan on 2005-12-11
Huh?
Weird, do you have the source repository enabled?
It should look something like this in you /etc/apt/source.list:
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy main restricted

---

### Post by Paool on 2005-12-11
yes, I have it... this is my sources.list

```
deb http://pl.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse 
deb-src http://pl.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse 

deb http://pl.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse 
deb-src http://pl.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse 
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse 

deb http://pl.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
deb-src http://pl.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 

deb http://www.kadu.net/download/binary/ubuntu/repo breezy main 

deb http://kubuntu.org/packages/kde35 breezy main

deb http://kubuntu.org/packages/amarok-1.3.7 breezy main

deb http://tomasz.nukysrealm.net/psi-pedrito ./
```

---

### Post by Knomefan on 2005-12-11
You could try to add
deb-src [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main
and see if it works then.

---

### Post by Paool on 2005-12-11
still doesn't work... :( (I've done apt-get update)

edited: haha, I know where's the problem. no kde-style-lipstiCk but lipstik :D

It works now, thanks :)

---

### Post by Paool on 2005-12-11
I've removed kde-style-lipstik package, compiled new version and I haven't new theme to choose in system settings... :(

---

### Post by jpmontalbo on 2005-12-11
did you try
```
./configure --prefix=/usr
```

also have you installed kdebase-dev?

---

### Post by Paool on 2005-12-12
yeah, that's it! :D Now I have lipstik 2.1, big thanks for you guys! :KS

---


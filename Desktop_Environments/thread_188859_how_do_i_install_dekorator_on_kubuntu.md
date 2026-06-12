---
title: "how do i install dekorator on kubuntu?"
date: 2006-06-04
forum: Desktop Environments
---

### Post by nocloud on 2006-06-04
can anybody tell me how to install dekorator?

---

### Post by cyracks on 2006-06-04
in synaptic or 
```

sudo apt-get install dekorator

```

---

### Post by nocloud on 2006-06-04
when i use sudo apt-get install dekorator, i get the following message:
Couldn't find package dekorator

also, since i upgraded to dapper, synaptic seems to have disappeared....

---

### Post by nocloud on 2006-06-04
does anybody know?

---

### Post by cyracks on 2006-06-04
```

sudo apt-get install synaptic

``` and edit the **/etc/apt/sources.list** to be like:

deb [http://si.archive.ubuntu.com/ubuntu/]("http://si.archive.ubuntu.com/ubuntu/") dapper main restricted universe multiverse

deb [http://si.archive.ubuntu.com/ubuntu/]("http://si.archive.ubuntu.com/ubuntu/") dapper-updates main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu/]("http://security.ubuntu.com/ubuntu/") dapper-security main restricted universe multiverse

---

### Post by nocloud on 2006-06-04
i added the  dapper main restricted universe multiverses but i am still getting E:Couldn't find package dekorator

are there any other ways to install dekorator?

---

### Post by cyracks on 2006-06-04
I have it under the universe section. Here is my complete sources.list

deb [http://si.archive.ubuntu.com/ubuntu/]("http://si.archive.ubuntu.com/ubuntu/") dapper main restricted universe multiverse
deb [http://si.archive.ubuntu.com/ubuntu/]("http://si.archive.ubuntu.com/ubuntu/") dapper-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/]("http://security.ubuntu.com/ubuntu/") dapper-security main restricted universe multiverse
deb [http://kubuntu.org/packages/amarok-14beta3]("http://kubuntu.org/packages/amarok-14beta3") dapper main
deb [http://theli.free.fr/packages/dapper/]("http://theli.free.fr/packages/dapper/") ./
deb [http://xgl.compiz.info/]("http://xgl.compiz.info/") dapper main
deb-src [http://xgl.compiz.info/]("http://xgl.compiz.info/") dapper main
deb [http://www.beerorkid.com/compiz]("http://www.beerorkid.com/compiz") dapper main
deb [http://kubuntu.org/packages/kde-353]("http://kubuntu.org/packages/kde-353") dapper main
deb [http://download.skype.com/linux/repos/debian/]("http://download.skype.com/linux/repos/debian/") stable non-free

[B]Edit:
[/B]admin@tricky:~$ apt-cache search dekorator
dekorator - KDE theme manager
kwin-style-blended - a window decoration theme for KDE

---

### Post by Waywocket on 2006-06-04
Did you remember to ```
sudo apt-get update
```?

---

### Post by nocloud on 2006-06-04
[QUOTE=Waywocket]Did you remember to ```
sudo apt-get update
```?[/QUOTE]

are you supposed to run that command after updating sources.list?

---

### Post by Waywocket on 2006-06-04
Yes, that or an equivalent command, such as reloading in Synaptic.

---

### Post by Ptero-4 on 2007-01-30
> **nocloud said:**
> are you supposed to run that command after updating sources.list?

Yes nocloud. That command tells apt (apt-get, aptitude, adept, synaptic) to read the sources.list file which will give it the newest list of available packages and repositories.

---


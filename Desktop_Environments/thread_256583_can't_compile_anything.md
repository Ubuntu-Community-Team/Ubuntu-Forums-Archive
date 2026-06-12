---
title: "can't compile anything"
date: 2006-09-13
forum: Desktop Environments
---

### Post by konst88 on 2006-09-13
hello
i always getting configure errors on any program i try to run configuration script.
maybe it is a problem with -dev packages, wich i cant install cuz synaptic says it cant mark all packages..
plz help me!!

for example, i try to configure Kopete:
```
checking for Qt... configure: error: Qt (>= Qt 3.3 and < 4.0) (library qt-mt) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
Make sure that you have compiled Qt with thread support!
```

when i mark libqt-mt-dev in synaptic, it says:
```
libqt3-mt-dev:
 Depends: libfreetype6-dev but it is not going to be installed
 Depends: libxft-dev but it is not going to be installed

```
errors like this i am getting on every -dev package i am trying to install.
before that, i allways succeded to configure Kopete.
help?

---

### Post by Ramses de Norre on 2006-09-13
What's the output when you do ```
sudo aptitude install libfreetype6-dev
```

---

### Post by konst88 on 2006-09-13
nice program this aptitude...
he wants to downgrade some packages..

---

### Post by Ramses de Norre on 2006-09-13
I guess you are using compiz repos? The packages you have at higher versions were released by quinn and give gnome terminal true transparancy. They aren't in the repos nomore though due to some bugs. 
So you'll have to choose between the true transparancy (with a couple of bugs) or the original dapper packages and the possibility to install libfreetype6 and libcairo dev packages.

(and aptitude is way better in dependency problems than apt-get! (and not only in dependency problems))

---

### Post by Ramses de Norre on 2006-09-13
Double post due to forum weirdness..

---

### Post by konst88 on 2006-09-13
yea, i used compiz before, but i removed it.
i will use aptitude from now on, thx a lot!!
i just hope it will solve these problems..

---

### Post by Ramses de Norre on 2006-09-13
Than you can downgrade them ;)
Do an aptitude upgrade after downgrading to make sure you've got the newest version of all packages.

---

### Post by konst88 on 2006-09-13
but synaptic still uses apt-get, right?
is it any way to make him use aptitude instead, or it is any other GUI program that uses aptitude?
i just like to search for packages using the GUI...

---

### Post by lamego on 2006-09-13
Yes, synaptic does use APT.
Anyway you can search using apt with:
```
apt-cache search keyword

```

---

### Post by Ramses de Norre on 2006-09-13
Or aptitude search ;)
Aptitude has his own semi-GUI which you can launch with just sudo aptitude, but I don't like it myself..
I think they're planning to move synaptics to a smarter porgram like aptitude but I don't know whether this will allready be done in edgy..

In fact I think using cli is more productive for installing but that's up to you.. you can always use synaptic for searching and stuff and then install using aptitude.

---

### Post by konst88 on 2006-09-13
thx guys, you saved my system!!=D> =D> =D> 
you are great!! :D :D :D

---

### Post by lamego on 2006-09-14
If you are looking for Kopete 0.12.2 for Dapper (i386), you can get the deb packaged here:
[http://www.getdeb.net/getdeb.php?file=kopete_3.5.4%2Bkopete0.12.2-0ubuntu1_i386.deb](http://www.getdeb.net/getdeb.php?file=kopete_3.5.4%2Bkopete0.12.2-0ubuntu1_i386.deb)

---

### Post by konst88 on 2006-09-14
thx, but i already compiled it, and it works great.

---


---
title: "cannot find gdebi in testing repository"
date: 2008-03-27
forum: Debian
---

### Post by keratos on 2008-03-27
I cant seem to find gdebi in the debian testing repo

any ideas?

---

### Post by benuski on 2008-03-27
Its not in testing right now because the version in unstable is buggy.  You can just use "dpkg -i <whatever>.deb" as root on the command line.

---

### Post by keratos on 2008-03-27
yeah, thats what I presumed ... just wanted confirmation.

Okay , acknowledge that one , will download and dpkg -i blahblahblah.

---

### Post by SunnyRabbiera on 2008-03-27
well if you wanted to you can just use alien to convert the gdebi package from ubuntu to debian, as gdebi is pretty solid here.
Also if you want another GUI front end to install debian packages, you can try kpackage, its a KDE app but its a decent front end.

---

### Post by keratos on 2008-03-27
> **SunnyRabbiera said:**
> well if you wanted to you can just use alien to convert the gdebi package from ubuntu to debian, as gdebi is pretty solid here.
Also if you want another GUI front end to install debian packages, you can try kpackage, its a KDE app but its a decent front end.

???

I have no problem installing Ubuntu packages and Debian using dpkg or indeed from ubuntu/debian repos.

Erm, unless I'm gravely mistaken, alien is for RPM to DEB.

---

### Post by polmir on 2008-04-03
Why you do not use from synaptic and dpkg

```
apt-get intall synaptic
```

[search Debian]("http://packages.debian.org/search?keywords=gdebi&searchon=names&suite=all&section=all&sourceid=mozilla-search")

> well if you wanted to you can just use alien to convert the gdebi package from ubuntu to debian,...

**deb -> to deb how?**

---

### Post by kellemes on 2008-04-03
Why not get it from sid?

---

### Post by jdhore on 2008-04-03
> **kellemes said:**
> Why not get it from sid?

Because a lot of times using a Sid package brings in a lot of unwanted Sid dependencies that could cause issues.

---

### Post by kerry_s on 2008-04-03
gdebi is in stable.
i use etch/lenny.

```
deb http://ftp.debian.org/debian/ etch main contrib non-free  
deb http://ftp.debian.org/debian/ lenny main contrib non-free  

deb http://security.debian.org/ etch/updates main contrib non-free 
deb http://security.debian.org/ lenny/updates main contrib non-free 

deb http://www.debian-multimedia.org/ lenny main 


```

---

### Post by jdhore on 2008-04-03
> **kerry_s said:**
> gdebi is in stable.
i use etch/lenny.

```
deb http://ftp.debian.org/debian/ etch main contrib non-free  
deb http://ftp.debian.org/debian/ lenny main contrib non-free  

deb http://security.debian.org/ etch/updates main contrib non-free 
deb http://security.debian.org/ lenny/updates main contrib non-free 

deb http://www.debian-multimedia.org/ lenny main 


```

Etch/Lenny is VERY smart as 99% of apps allow newer version of dependencies, but not older...

---

### Post by kerry_s on 2008-04-04
> **jdhore said:**
> Etch/Lenny is VERY smart as 99% of apps allow newer version of dependencies, but not older...

now your catching on. i use the etch kernel cause it runs better on my laptop, but everything else is lenny.

mines a custom install on 450mhz 256mb ram, it's built to be fast.
:lolflag:

---

### Post by kellemes on 2008-04-04
> **jdhore said:**
> Because a lot of times using a Sid package brings in a lot of unwanted Sid dependencies that could cause issues.

I know, but you can use pinning /etc/apt/preferences to set branch-priorities and install gdebi like so..
```
apt-get install gdebi/unstable
```

This is how I keep a mixed system anyway..

---

### Post by jdhore on 2008-04-04
> **kellemes said:**
> I know, but you can use pinning /etc/apt/preferences to set branch-priorities and install gdebi like so..
```
apt-get install gdebi/unstable
```

This is how I keep a mixed system anyway..

True, but IMO, if a user wants gdebi, they prolly don't want to muck with /apt/preferences ...

---

### Post by kellemes on 2008-04-04
> **jdhore said:**
> True, but IMO, if a user wants gdebi, they prolly don't want to muck with /apt/preferences ...

Very good point. ;-) Didn't think of that.

---


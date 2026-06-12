---
title: "./configure error -- bzlib devel package?"
date: 2005-09-01
forum: Desktop Environments
---

### Post by veraction on 2005-09-01
I'm trying to ./configure for something called dclib 3.7 (I think that's what it's called).

Configure works fine until:

```
checking bzlib.h presence... no
checking for bzlib.h... no
configure: error: bzlib headers not found. install bzlib devel package
```

I checked Synaptic Package Manager & I have bzip2 installed.. however I think that I need bzip2-devel or something.

I've been googling a bit but can't find any solution.

Any advice?

---

### Post by arnieboy on 2005-09-01
[QUOTE=veraction]I'm trying to ./configure for something called dclib 3.7 (I think that's what it's called).

Configure works fine until:

```
checking bzlib.h presence... no
checking for bzlib.h... no
configure: error: bzlib headers not found. install bzlib devel package
```

I checked Synaptic Package Manager & I have bzip2 installed.. however I think that I need bzip2-devel or something.

I've been googling a bit but can't find any solution.

Any advice?[/QUOTE]
do the following:
```
sudo apt-get remove libdc0 libdc0-dev
```
next, download the dclib and valknut packages from:
[http://peppesbodega.nu/gallery/Debian%20Packages/Apps/Valknut](http://peppesbodega.nu/gallery/Debian%20Packages/Apps/Valknut)
then do the following:
```
sudo dpkg -i dclib_0.3.7*.deb
sudo dpkg -i valknut_0.3.7*.deb
```

that should get u all set. then u dont have to compile the dclib packages from source.

---

### Post by Perfect Storm on 2005-09-01
It's: **libbz2-dev**
It should be there :)



.:=The AI Dude=:.

---

### Post by veraction on 2005-09-01
Ok, thanks a lot. I was able to get the ./configure to work after installing that package (I was searching for things like bzip-devel) and after installing another package.

Also was able to get valknut to work which was nice ;) dcgui-qt was giving me nightmares when I was using it last year (Its older version of valknut -- doesn't save any settings)

---

### Post by Moeng on 2008-07-08
> **Artificial Intelligence said:**
> It's: **libbz2-dev**
It should be there :)



.:=The AI Dude=:.

Yes, using "sudo apt-get install libbz2-dev" fixed this problem for me.  Thanks

---


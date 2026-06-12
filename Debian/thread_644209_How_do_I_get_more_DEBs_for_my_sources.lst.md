---
title: "How do I get more DEBs for my sources.lst?"
date: 2007-12-18
forum: Debian
---

### Post by jingo811 on 2007-12-18
I've been forced to install Debian Etch on a PC with no Internet connection since it was wireless.  So the only lines I have in my sources.lst are these 3 which doesn't seem to be enough.  Then I had to enable the "apt-cdrom add" in order to get the wireless working.

```
deb http://security.debian.org/ etch/updates main contrib
deb-src http://security.debian.org/ etch/updates main contrib
(and the line for the apt-CD ROM, I'm not sitting on that PC right now)
```

But now I need more sources.lst because I don't seem to be able to ```
apt-get install mkfs, mkdosfs and gparted. 
``` I can apt-cache search for them but I can't download them.
And I don't want to insert my Debian CD every time I apt-get something so I'm gonna comment it out and try add some more sources.lst thingys.

I stumbled on this link is this what I'm looking for and how do I make the syntax right?  It doesn't look like having the same syntax as the default Debian sources.lst?
```
deb http://security.debian.org/ etch/updates main contrib
deb-src http://security.debian.org/ etch/updates main contrib
```

[http://www.debian.org/mirror/mirrors_full#SE](http://www.debian.org/mirror/mirrors_full#SE)

Help please.

---

### Post by pelle.k on 2007-12-18
"man sources.list".
I think this is how it is supposed to look;
```
## main and contrib
deb http://ftp.sunet.se/pub/Linux/distributions/debian/ etch main contrib
deb-src http://ftp.sunet.se/pub/Linux/distributions/debian/ etch main contrib
## non-free
#deb http://ftp.sunet.se/pub/Linux/distributions/debian/ etch non-free
#deb-src http://ftp.sunet.se/pub/Linux/distributions/debian/ etch non-free
```

---

### Post by b9anders on 2007-12-19
a standard source list for most users would look something like this:

```
deb http://ftp.debian.org/debian/ etch main contrib non-free
#deb-src http://ftp.debian.org/debian/ etch main contrib non-free

deb http://security.debian.org/ etch/updates main contrib non-free
#deb-src http://security.debian.org/ etch/updates main contrib non-free

##Debian multimedia##
#Install debian-multimedia-keyring to authenticicate#
deb http://www.debian-multimedia.org stable main
```

the multimedia repo is not official but very useful and generally trusted. If you simpy copy/paste that into your sources, and do 'aptitude update', you should have full access to all packages.

For even more, there's [http://www.apt-get.org/](http://www.apt-get.org/)

btw, just to be sure - if you actually typed in

```
apt-get install mkfs, mkdosfs and gparted.
```

it wouldn't work. Needs to be 

```
apt-get install mkfs mkdosfs gparted
```

Also, aptitude is the preferred front-end for apt in debian now, not apt-get.

---

### Post by jingo811 on 2007-12-19
> **b9anders said:**
> ......
.......
Also, aptitude is the preferred front-end for apt in debian now, not apt-get.

Tnx for posting the standard list and giving me tips.  Yeah I read aptitude has better dependency management than apt-get but aptitude has screwed me over 2 major times when I wanted to uninstall LAMP and some other minor program.  Then it just wiped out my entire gnome-desktop including all programs I've installed separately without asking me.

I'm not going near taskcel and aptitude ever again during my life time :) besides all the über elite linux guys at my school don't use aptitude they use apt-get so I'm gonna follow their foot steps.

---

### Post by benuski on 2007-12-19
> **b9anders said:**
> a standard source list for most users would look something like this:

```
deb http://ftp.debian.org/debian/ etch main contrib non-free
#deb-src http://ftp.debian.org/debian/ etch main contrib non-free

deb http://security.debian.org/ etch/updates main contrib non-free
#deb-src http://security.debian.org/ etch/updates main contrib non-free

##Debian multimedia##
#Install debian-multimedia-keyring to authenticicate#
deb http://www.debian-multimedia.org stable main
```



You're not supposed to use ftp.debian.org anymore, as it experiences lots of downtime and does not get updates as fast.  Use the mirror with your country code, so if you live in the US, use ftp.us.debian.org instead of ftp.debian.org.

---

### Post by jingo811 on 2007-12-20
```
deb http://ftp.debian.org/debian/ etch main contrib non-free
#deb-src http://ftp.debian.org/debian/ etch main contrib non-free
```

I'm not good with manpages but why have you commented out the
#deb-src http:/ftp.........part in the standard sources.list?
Why include it if you're not going to use it by standard measures?  What does the deb-src do compared to the deb only line?

---

### Post by pelle.k on 2007-12-20
It lets you fetch source packages. If you want to make your own debs, etc.

---

### Post by b9anders on 2007-12-21
it's useful for compiling for source. Most people don't need this for updates however, so might as well just comment it out until the time when you do want to compile something from source, save time when updating your sources.

---

### Post by jingo811 on 2007-12-21
ic.

---


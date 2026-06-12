---
title: "Impossible to get some dvd authoring"
date: 2006-01-18
forum: General Help
---

### Post by marcostt on 2006-01-18
I am desperate...

I am traying to get some dvd authoring and is not possible... I have tried to install with apt-get qdvdauthor, dvdstyler, tovid... and always get some error message, for example that I need some libs that I can not download anyway, or that is not that package in teh repository... For example, with the package manager I can choose dvdstyler to install, but whem I execute the "Commit changes" to do it, I get hte next error message: "There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages." And exactly the same with qdvdauthor.

This is my sources list (I probe to comment nerim or kyria, but nothing change):

> deb-src [http://packages.kirya.net](http://packages.kirya.net) stable main contrib non-free 
deb [http://packages.kirya.net](http://packages.kirya.net) stable main contrib non-free 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main 
# deb [http://kubuntu.org/packages/kde35rc2](http://kubuntu.org/packages/kde35rc2) breezy main 
# deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./ 
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main 
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted 

## Uncomment the following two lines to fetch updated software from the network
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) breezy main restricted 
deb-src [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) breezy main restricted 

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) breezy-updates main restricted 
deb-src [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) breezy universe 
deb-src [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) breezy universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 
deb-src [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe 

---

### Post by Choad on 2006-01-18
using adept (k menu> system> package manager (adept)) i searched for "dvd" and installed something called "dvdauthor" and it had no problems. so try doing it through adept?

---

### Post by marcostt on 2006-01-18
> using adept (k menu> system> package manager (adept)) i searched for "dvd" and installed something called "dvdauthor" and it had no problems. so try doing it through adept?

Yes. I did installed dvdauthor, but I want the gui qdvdauthor. Anyway, trying to use dvdauthor to transform mpg to vob, I get errors... I think I have a serious conflict with librarys, but I dont know how to resolve it... I think the problem must be in the sources.list.

---

### Post by marcostt on 2006-01-19
This is the console result of trying to install qdvdauthor (sorry, it is in spanish, but I think is easyly understanded:

```
Los siguientes paquetes tienen dependencias incumplidas:
  qdvdauthor: Depende: libqt3c102-mt (>= 3:3.3.4) pero no es instalable
              Depende: libxine1 (>= 1.0.1) pero no es instalable
E: Paquetes rotos
```

But I can install that packages...

If I try to install transcode (needed to use dvdauthor):

```
Los siguientes paquetes tienen dependencias incumplidas:
  transcode: Depende: libdps1 (> 4.1.0) pero no es instalable
E: Paquetes rotos

```

I stiil think that there is a conflict with the repositories in my sources.list, but I dont know how to resolve it.

Please, help.

---

### Post by GeneralZod on 2006-01-19
Including "marillat" is almost always a bad idea - if I were you, I'd drop it and then update apt.  

Open synaptic, search for qdvdauthor, double-click on qdvdauthor and see what versions are available and from where (there's a special tab for this; in English, I think it's called "Versions").

---

### Post by marcostt on 2006-01-19
Ok, I have disabled marillat. But now, there is not package of qdvdauthor to install. There is a package of dvdstyler, but no information about version (n/a), and when I try to install it, I can not: just do nothing when I click the install bottom.

?

---

### Post by marcostt on 2006-01-21
Please, maybe some one that can install qdvdauthor or dvdstyler and transcode... can show here his sources.list in order I can copy and download the programs...

Thanks in advance.

---

### Post by GeneralZod on 2006-01-21
I just installed it just now.  Here is my sources.list:

```

# deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 


# deb http://gb.archive.ubuntu.com/ubuntu/ breezy main restricted 
# deb-src http://gb.archive.ubuntu.com/ubuntu/ breezy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
# deb http://gb.archive.ubuntu.com/ubuntu/ breezy-updates main restricted 
# deb-src http://gb.archive.ubuntu.com/ubuntu/ breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.


deb http://gb.archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse 
deb http://gb.archive.ubuntu.com/ubuntu/ breezy-security universe main restricted multiverse 
deb http://gb.archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse 

deb-src http://gb.archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse 
deb-src http://gb.archive.ubuntu.com/ubuntu/ breezy-security universe main restricted multiverse 
deb-src http://gb.archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse 




## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse 
deb-src http://gb.archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted 

deb http://security.ubuntu.com/ubuntu/ breezy-security universe 
deb-src http://security.ubuntu.com/ubuntu/ breezy-security universe 

#w32codecs
# deb ftp://ftp.nerim.net/debian-marillat/ etch main 

deb http://soulmachine.net/breezy/ unstable/ 

# deb http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse 
# deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse 
# deb-src http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse 
# deb-src http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse 


deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free 
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free 

deb http://people.ubuntu.com/~doko/OOo2 ./


```

Edit: VVV

Great! :)

---

### Post by marcostt on 2006-01-21
Yes! I got it now... I hope now works well :)

Thank you very much

---


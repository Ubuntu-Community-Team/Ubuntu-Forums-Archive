---
title: "Nepomuk missing dependency in KDE SC 4.4  beta 2"
date: 2009-12-22
forum: Desktop Environments
---

### Post by lerrup on 2009-12-22
I am trying KDE 4.4 but keep getting an error for Nepomuk as it needs the Virtuoso RDF server, which does not appear to be installable.

Anyone know how this can be solved as it would be good to get this resolved...

---

### Post by brommage on 2009-12-22
I think Soprano is a restricted package.  Make sure you've got "universe" and "multiverse" selected in System Settings > Add and Remove Software > Settings > Edit Software Sources (or just add them to the PPA under /etc/apt/sources.list)

Nepomuk was broken for me on upgrade to 4.3.80.  I reactivated it after installing 4.3.85, and the package manager automatically triggered an install of the missing dependencies.

---

### Post by peterbuldge on 2009-12-22
[http://kde.org/announcements/announce-4.4-beta2.php](http://kde.org/announcements/announce-4.4-beta2.php)

the release announcement definitely implies that virtuoso is working now in beta 2.  Installing now, fingers crossed

---

### Post by peterbuldge on 2009-12-22
I've already have soprano installed and restricted packages enabled and its still telling me that it can't start nepomuk because of a virtuoso problem.  I can find the virtuoso libs if I run locate though but they aren't being seen by nepomuk.

no virtuoso packages come up when I search aptitude.  the virtuoso backend doesn't appear to actually be a separate package but is instead built into soprano now. Is this correct?  if not, that may be part of why I'm having trouble.

edit:
apparently, according to the devel irc, virtuoso IS a separate package and it's still not ready.  If your package manager automatically triggered an install of anything it was probably sesame.

---

### Post by piedro on 2009-12-23
Hi! 

I tried with kde 4.3.85 and it's telling me I have to install the soprano backend. Did that. Now: Indexing is running but I still get this message: 

> Nepomuk semantic search requires virtuoso rdf server running. 

Is there a workaround available? I can't find one ... 

thx, p.

---

### Post by shizow on 2009-12-24
same problem here with KDE 4.4 beta2

> 
Nepomuk Semantic Desktop needs the Virtuoso RDF server to store its data. Installing the Virtuoso Soprano plugin is mandatory for using Nepomuk.


maybe there is no package of virtuoso yet? [https://bugs.kde.org/show_bug.cgi?id=218836](https://bugs.kde.org/show_bug.cgi?id=218836)

there seems to be a package for jaunty but not karmic [https://bugs.launchpad.net/ubuntu/+bug/331757](https://bugs.launchpad.net/ubuntu/+bug/331757)

---

### Post by Ubuntiac on 2009-12-24
I'm having the same problem. I filed a bug with KDE and Sebastian Trueg said:
> You need to install the Virtuoso server itself. It is very well possible that
no packages exist yet which means that you will have to compile it yourself.
For KDE 4.4 final packages will be available.


As said above though, there doesn't seem to be any package with Virtuoso in it's name in the packagemanager. I think they probably just forgot to package it...

---

### Post by carsy on 2009-12-24
There is a thread about this here:

[http://kubuntuforums.net/forums/index.php?topic=3107077.0](http://kubuntuforums.net/forums/index.php?topic=3107077.0)
"Strigi"

Especially reply #9 by rog131.
Once More With Feeling
a.k.a "I want it NOW !!"

Disregard the link in reply #4. It applies to Java-based Sesame backend
"How To Enable Nepomuk/Strigi Desktop Search in Kubuntu 9.10/KDE4.3"

This worked for me after hours of messing around before getting to the Kubuntu and Ubuntu Forums. Strigi, Nepomuk all working fine now. Akonadi Server in Kontact is happy (or at least not complaining any more). Now I'm trying to figure out how to play with this new toy.

Previously used Redlands and Sesame. Virtuoso is a speed demon by comparison.

Carl

---


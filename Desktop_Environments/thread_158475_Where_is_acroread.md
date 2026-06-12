---
title: "Where is acroread?"
date: 2006-04-11
forum: Desktop Environments
---

### Post by That Other Guy on 2006-04-11
I hate to post this, because it's such a stupid question, but where is acroread (and associated firefox plugins)?  I can't find it through apt-get:

```
mike@virga:~$ sudo apt-get install acroread
Reading package lists... Done
Building dependency tree... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package acroread has no installation candidate

```

I think I've got all the needed repositories active:

```
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ breezy main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy main restricted 

deb http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted 

deb http://us.archive.ubuntu.com/ubuntu/ breezy universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy universe 

deb http://us.archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted 

deb http://security.ubuntu.com/ubuntu/ breezy-security universe 
deb-src http://security.ubuntu.com/ubuntu/ breezy-security universe 

deb http://kubuntu.org/packages/kde352/ breezy main 
deb ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.2/kubuntu/ breezy main 
deb http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.5.2/kubuntu/ breezy main 
deb http://mirror.cc.columbia.edu/pub/software/kde/stable/3.5.2/kubuntu/ breezy main 

deb http://wine.sourceforge.net/apt binary/
 
```

---

### Post by Ferri on 2006-04-11
I believe you have to add "multiverse" to these two lines:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe [COLOR="Red"]multiverse[/COLOR]
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe [COLOR="Red"]multiverse[/COLOR]

---

### Post by That Other Guy on 2006-04-11
That's the ticket, Ferri.  Cripes - I knew I had multiverse in the sources list, but didn't catch that it was only on backports. Thanks.  I knew this was a stupid question.

---


---
title: "Ubuntu-Opera Issue"
date: 2006-07-25
forum: Desktop Environments
---

### Post by chucksheen on 2006-07-25
I have Ubuntu 6.0.6 installed and download Opera 9. When I launch the install a window tells me in red:

"Error: Dependancy is not satisfiable: lib13t-mt"

I've done some searching and I'm confused.

Any suggestions?

PS.  I posted this in the Opera forums and I've gotten no response yet.
[http://my.opera.com/community/forums/topic.dml?id=150878](http://my.opera.com/community/forums/topic.dml?id=150878)

---

### Post by aysiu on 2006-07-25
How about getting it from the Ubuntu commercial repository?

1. [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

2. ```
sudo aptitude update && sudo aptitude install opera
```

---

### Post by bulldog on 2006-07-25
How did you installed it?
With aptitude it should work,I did it myself and no problems.

---

### Post by chucksheen on 2006-07-25
I'm using Firefox that came with Ubuntu.

I downloaded it.

Firefox download manager, clicked open.

Error.

---

### Post by aysiu on 2006-07-25
Yeah. Don't download it. Use *aptitude* to install it. Those are the instructions I gave you earlier.

---

### Post by bulldog on 2006-07-25
You're better off when you use the repository's for Ubuntu.
With apt-get or aptitude or graphical with synaptic all the dependency's where set right for you.
Try the solution given by Aysiu to repair your install off Opera.

---

### Post by chucksheen on 2006-07-25
I wish I could just download Opera and install it.

Here is what I got from terminal:

(gedit:10564): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by chucksheen on 2006-07-26
I'm surprised I haven't resolved the issue after posting in the Opera and Ubuntu forums.

:confused:

---


---
title: "Can't find k9copy or xdvdshrink in the repositories"
date: 2006-04-26
forum: Desktop Environments
---

### Post by fanoodlehey on 2006-04-26
As the title suggests I can't find these apps.

I'm using adept and I want to get one of these because K3B won't read encrypted DVDs.

Here's my sources.list
```

deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

deb http://deb.opera.com/opera/ etch non-free

deb http://kubuntu.org/packages/kde351 breezy main

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/

## created by arnieamuleadded

```

Any ideas?
Thanks.

---

### Post by arnieboy on 2006-04-26
1) xdvdshrink is a windows only software which u can run with wine on breezy.
download the windows executable and install it with wine.

2) for installing k9copy do the following:
add the following lines to your sources.list:
> deb [http://repos.knio.it/](http://repos.knio.it/) breezy main contrib non-free
deb-src [http://repos.knio.it/](http://repos.knio.it/) breezy main contrib non-free 
save and exit and do the following:
```
gpg --keyserver hkp://pgp.mit.edu --recv-keys 35A92053
gpg --armor --export 35A92053 | sudo apt-key add - 
sudo apt-get update
sudo apt-get install k9copy
```

---

### Post by fanoodlehey on 2006-05-01
Thanks for the help.

I keep getting the following response:
gpg: requesting key 35A92053 from hkp server pgp.mit.edu
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

Any ideas?

---

### Post by arnieboy on 2006-05-01
[QUOTE=fanoodlehey]Thanks for the help.

I keep getting the following response:
gpg: requesting key 35A92053 from hkp server pgp.mit.edu
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

Any ideas?[/QUOTE]
dont worry about that. just go ahead and install k9copy.

---

### Post by AAUBUNTU on 2006-05-02
[QUOTE=arnieboy]1) xdvdshrink is a windows only software which u can run with wine on breezy.
download the windows executable and install it with wine.[/QUOTE]

[xdvdshrink]("http://dvdshrink.sourceforge.net") is actually a bash script.  You're thinking of [dvdshrink]("http://www.dvdshrink.org") which is a windows program that will run in Wine.

---

### Post by fanoodlehey on 2006-05-03
OK. I went ahead and installed it. Worked out fine. I've yet to use it so hopefully it will do what I want.

Thanks for all the help.

---


---
title: "F-stop package missing?"
date: 2006-09-10
forum: Desktop Environments
---

### Post by kkinder on 2006-09-10
Is it just me or has the f-stop package gone missing? Does anyone else see it?

---

### Post by Ramses de Norre on 2006-09-10
Don't you mean F-Spot?

---

### Post by kkinder on 2006-09-10
Yes, the camera program. Do you see?

---

### Post by Ramses de Norre on 2006-09-10
It's in the repos, the package is called "f-spot". Make sure you've got all repos enabled if you can't find it (it's in universe).

---

### Post by kkinder on 2006-09-10
I don't see it and I have universe enabled. Here's my sources.list file:
```

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by Ramses de Norre on 2006-09-10
That's pretty weird.. I've got the package here, I use the general severs (no country code).
You can also get the package [here]("http://packages.ubuntu.com/dapper/gnome/f-spot").

---

### Post by kkinder on 2006-09-10
Curious. I did an apt-get update this morning, it wasn't there, and I did one again just now, and it's there. I haven't changed my sources file. Heh.

Thanks for digging it up.

---


---
title: "sudo apt-get update not working"
date: 2006-01-08
forum: General Help
---

### Post by sites on 2006-01-08
i'm working on a fresh install.  but it stopped updating.  now i'm getting this....

E:  Opening /etc/apt/sources.list - ifstream::ifstream (2 No such file or directory)

also, synaptic quit working.  all my hardware was recognized without loading further modules.  i've been installing software, using both synaptic & the terminal.  but now neither of them work.  i dont know how i broke it.

---

### Post by aysiu on 2006-01-08
[http://www.ubuntuforums.org/showthread.php?t=54749](http://www.ubuntuforums.org/showthread.php?t=54749)

---

### Post by sites on 2006-01-08
doesnt look like the same problem.  my repositories were updated and previously running just fine.

---

### Post by aysiu on 2006-01-08
[QUOTE=sites]doesnt look like the same problem.  my repositories were updated and previously running just fine.[/QUOTE] Just in case it's a similar but different problem, would you mind posting your /etc/apt/sources.list?

---

### Post by sites on 2006-01-09
ls /etc/apt/sources.list
gives me... no such file or directory

do i need to open it in an editor?

---

### Post by aysiu on 2006-01-09
Try ```
cat /etc/apt/sources.list
``` and post the output here.

---

### Post by sites on 2006-01-09
ok i found a .save file (but should i save a copy as the source.list file?)
here's what it says:

## Uncomment the following two lines to fetch updated software from the network
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe multiverse

---

### Post by aysiu on 2006-01-09
Alt-F2 ```
gksudo gedit /etc/apt/sources.list
``` paste in what you posted here and then save it. Then ```
sudo apt-get update
```

---

### Post by Bender NZ on 2006-01-09
And drop the bottom two entries off the list you pasted, they're double ups of sources you already have.

---


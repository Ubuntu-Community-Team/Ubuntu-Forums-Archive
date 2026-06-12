---
title: "E16 unavailable from Synaptic?"
date: 2005-12-02
forum: Desktop Environments
---

### Post by j.hill on 2005-12-02
Once upon a time I had e16 on my computer.  Then I got rid of it, so I could try e17 without worrying about conflicts.  (Still a n00b....)  I added a respository for e17, installed it, decided it was not for me, uninstalled it, deactivated the new repository, and went to reinstall e16......but I can't.  It's still listed in Synaptic, but without a version number; and when I try to mark it for installation, I get this:

```
Package enlightenment has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list
```

But it was in universe before and it should still be in universe now, right?  I only had it off my computer for maybe two weeks -- they wouldn't have removed e16 but kept all the dependencies and ancillary programs -- would they?

Assuming that e16 is still in universe, how can I get Synaptic to let me have it?  (I haven't tried apt-get, assuming that it will behave the same way; is that a bad assumption?)

As a side note:  am I the only one who prefers e16 to e17?

---

### Post by Xian on 2005-12-02
Yeah, it's still in Universe. 
Check your source list for inclusion.

```
$ apt-cache policy enlightenment
enlightenment:
  Installed: (none)
  Candidate: 1:0.16.6-3ubuntu3
  Version table:
     1:0.16.6-3ubuntu3 0
        500 http://archive.ubuntu.com breezy/universe Packages
```

```
$ sudo aptitude install enlightenment
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
The following NEW packages will be automatically installed:
  enlightenment-data fnlib-data imlib-base imlib1 imlib11 libfnlib0
  libpng10-0
The following NEW packages will be installed:
  enlightenment enlightenment-data fnlib-data imlib-base imlib1 imlib11
  libfnlib0 libpng10-0
0 packages upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 4968kB of archives. After unpacking 9593kB will be used.
Do you want to continue? [Y/n/?] 
```

---

### Post by teaker1s on 2005-12-02
my sources I can get it

 ## deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy main restricted  

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy-updates main restricted  
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy-updates main restricted  

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy universe  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted



deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) breezy universe main restricted
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

## FTP mirror from [http://free.fr](http://free.fr) (french ISP)
##deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
##deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

---

### Post by j.hill on 2005-12-03
OK, so here's what I've got:

```
$ apt-cache policy enlightenment
enlightenment:
  Installed: (none)
  Candidate: (none)
  Package pin: (not found)
  Version table:
     1:0.16.6-3ubuntu3 999
        500 http://archive.ubuntu.com breezy/universe Packages
```

Is it a problem that I have no "candidate"?  I also notice that I have no "package pin", whatever that is.

---

### Post by idlewild on 2005-12-11
I've got the same problem here, what does the 999 (instead of 0) after the version number signify?

```
$ apt-cache policy enlightenment
enlightenment:
  Installed: (none)
  Candidate: (none)
  Package pin: (not found)
  Version table:
     1:0.16.6-3ubuntu3 999
        500 http://archive.ubuntu.com breezy/universe Packages
```

---

### Post by william_nbg on 2006-01-31
Same problem here.

But I tried e17, first and decided to go back to e16, 17's not ready yet.

---

### Post by bluevoodoo1 on 2006-02-14
Yes, same problem here....

---

### Post by bluevoodoo1 on 2006-02-15
I got mine working. There was a HOW-TO on how to get e17 that I started and never finished. One of the steps was to create a 'preferences' file in the /etc/apt/ folder. Then paste some stuff about e17 in it. Well, deleted that file now I see e16 back in synaptic.

---


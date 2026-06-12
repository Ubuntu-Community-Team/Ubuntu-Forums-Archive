---
title: "Synaptic quit working"
date: 2006-07-20
forum: Desktop Environments
---

### Post by bboop on 2006-07-20
Synaptic suddenly quit working - starts to open then nothing.\
I am running dapper on desktop w/ kde, serial modem. 
All was well until I started this PM. Ran fine yesterday. Last thing I did was to begin to try and set up pda connect as per thread "how to set up & use synce". I used apt-get as per instructions for that though. Didn't get operation finish before electrical storm came in & I shut all down.

Sources file is this:

## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper main dupdate french
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) kubuntu main

Could use some ideas if anyone has any. TIA

---

### Post by philippe_carlo on 2006-07-20
You probably need to run 
```

sudo apt-get install -f

```

for apt to recover from the thunderstorm and complete installing packages.

---

### Post by bboop on 2006-07-20
I wil try this but, sorry for not being clear in 1st post - computer was totally shut off & disconnected from power when storm hit. I had shut down after the package was finished downloading, just didn't finish getting pda recongnized process. Sorry again. Will post back if this helps.

Thank you very much - it did the trick, will put this in my file for ubuntu tips so I'll have it if needed again.
I appreciate the help:D

---


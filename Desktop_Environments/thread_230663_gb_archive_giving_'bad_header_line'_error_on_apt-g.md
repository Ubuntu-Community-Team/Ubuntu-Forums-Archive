---
title: "gb archive giving 'bad header line' error on apt-get update"
date: 2006-08-06
forum: Desktop Environments
---

### Post by Rich99 on 2006-08-06
I'm using a new install of dapper drake, using my local (gb) archives.  /etc/apt/sources.lst looks like this:

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

deb [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) dapper-seveas freenx extras custom
deb-src [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) dapper-seveas freenx extras custom

deb [http://debian.space-based.de/debs/](http://debian.space-based.de/debs/) experimental main
deb-src [http://debian.space-based.de/debs/](http://debian.space-based.de/debs/) experimental main



However when I do an apt-get update, I get errors for the official repositories:

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/Relea](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/Relea) se.gpg  Bad header line

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i38](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i38) 6/Packages.gz  Bad header line

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/bina](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/bina) ry-i386/Packages.gz  Bad header line

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sou](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sou) rces.gz  Bad header line

Failed to fetch 
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/sour](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/sour) ce/Sources.gz  Bad header line

Failed to fetch [http://debian.space-based.de/debs/dists/experimental/Release](http://debian.space-based.de/debs/dists/experimental/Release)  Un able to find expected entry  main/source/Sources in Meta-index file (malformed R elease file?)

Any ideas why this is?

---

### Post by matjaz_pirnovar on 2006-08-08
I'm getting the same note.

(Then I changed my sources.list to utah mirror and still get two bad header line notes.)

What does it mean?
Which header lines? Where are they?

---


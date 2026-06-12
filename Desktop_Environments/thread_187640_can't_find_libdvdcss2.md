---
title: "can't find libdvdcss2"
date: 2006-06-03
forum: Desktop Environments
---

### Post by kasemodz on 2006-06-03
I'm looking for that libdvdcss required by dvdbackup and others and just can't seem to find it. I searched on synaptic but no results. My reositires have the standarad ubuntu repository that came after the install. How can I get this codec. I need it asap

Btw.. I still have the ubuntu breezy 5.10 right now.

---

### Post by Rackerz on 2006-06-03
You need to enable the universe and multiverse repositories. Uses this sources.list.

Open up a Terminal and type;
```
sudo gedit /etc/apt/sources.list
```

Then delete whatever is in the file and replace it with this;
> ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

Then save the file and type in the Terminal 'sudo aptitude update'. Then go and find the package in synaptic.

---

### Post by tribaal on 2006-06-03
In case you still wonder / have problems, the ultimate ressource for me was [this page]("https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29").

Cheers!

- trib'

---

### Post by Rackerz on 2006-06-03
[QUOTE=tribaal]In case you still wonder / have problems, the ultimate ressource for me was [this page]("https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29").

Cheers!

- trib'[/QUOTE]

That is also a very good page for information on this.

---


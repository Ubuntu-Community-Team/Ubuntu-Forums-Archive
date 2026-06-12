---
title: "problem with sources.list"
date: 2006-07-25
forum: Desktop Environments
---

### Post by randell6564 on 2006-07-25
Hi!

Up until today, I have had no problems fetching everything after doing a 'sudo apt-get update'

But now I'm getting this at the terminal:

[B]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Relea](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Relea) se  Unable to find expected entry  main/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used  instead.[/B]

Any ideas?

This is my '/etc/apt/sources.list'

[B]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
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
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


[/B]

Thanks!

---

### Post by ozorba on 2006-07-25
Have you tried the following commands in a termina?

sudo apt-get update
If you get errors then retry. It may be that the servers are too busy.

If you do not get errors then do

sudo apt-get upgrade

--
OZ

---

### Post by randell6564 on 2006-07-25
> **ozorba said:**
> Have you tried the following commands in a termina?

sudo apt-get update
If you get errors then retry. It may be that the servers are too busy.

If you do not get errors then do

sudo apt-get upgrade

--
OZ

Hi!  Yes, I did a 'sudo apt-get update'.  Thats when I show the preveous "failed to fetch" error message.

As far as "upgrade" not sure that I want to do that.  What will get upgraded?

---

### Post by lamego on 2006-07-25
There are a lot of mirrors, just pick another one for which you have good connectivity.

---

### Post by randell6564 on 2006-07-25
> **lamego said:**
> There are a lot of mirrors, just pick another one for which you have good connectivity.


OK, but... Where do I go to "pick" one?  You are saying that I can add a repo to my sources.list that has good connectivity right?  Where do you get new mirrors?

Thanks!

---

### Post by lamego on 2006-07-25
There is a rule for the mirror names, country.archive.ubuntu.com
Countries:
us.
uk.
es.
pt.
br.
...

---

### Post by randell6564 on 2006-07-25
> **lamego said:**
> There is a rule for the mirror names, country.archive.ubuntu.com
Countries:
us.
uk.
es.
pt.
br.
...

So... I want 'us.archive.ubuntu.com'?

This is what I would add to my repos?  Wait, I already have that!  So maybe try another country is what you are saying?

---


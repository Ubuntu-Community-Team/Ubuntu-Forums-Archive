---
title: "Packages missing from my repositories"
date: 2006-06-24
forum: Desktop Environments
---

### Post by Fafnir on 2006-06-24
This is weird. I upgraded to Dapper a few weeks ago and I'm happy with it, but there seem to be huge numbers of packages missing from the repositories. I literally have nine programs total in the Science section, for example - while [this]("http://packages.ubuntu.com/dapper/misc/") would seem to indicate quite a few more. I'm guessing the site isn't inaccurate (it's the number one result for 'Ubuntu packages' from Google), and it's taking its data from the official repositories, so what gives?

I've obviously tried apt-get update, which did nothing. I have all Dapper repositories enabled (LTS binary/source, LTS Updates binary/source, LTS Security Updates binary/source, LTS Backports). All except Security Updates are set to check for packages in Main, Restricted, Universe and Multiverse. I've even tried adding all the Breezy repositories - still nothing. It's not a problem with Synaptic, since apt-get won't find the packages either. Here's a copy of my sources.list:

```


deb http://gb.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://gb.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://gb.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

``` The commented-out sections seem to be from Breezy.

So, how do I get Synaptic to recognise the other packages?

Thanks in advance!

---

### Post by tonyr on 2006-06-24
You can change all **breezy** instances to **dapper**.  Uncomment the **breezy universe**
lines, change **breezy** to **dapper**, add **multiverse** at the end, and try again.

---

### Post by Fafnir on 2006-06-24
[QUOTE=tonyr]You can change all **breezy** instances to **dapper**.  Uncomment the **breezy universe**
lines, change **breezy** to **dapper**, add **multiverse** at the end, and try again.[/QUOTE]

Nope - didn't work. Sorry, I should have mentioned - Synaptic does detect some universe and multiverse packages, just very few of them! Thanks anyway.

---

### Post by tonyr on 2006-06-24
Apologies, my fault, I see that the **universe** and **multiverse** repositories are
mentioned in the first set at the top.  Did you try other repositories: **eu**, **us**, **ca** (and 
straight archive.ubuntu.com) ?   What are some of the specific packages?  I can
try to verify that I can or cannot see them, too.

---

### Post by Fafnir on 2006-06-24
Now why didn't I think of that? :-) Yup - eu works like a charm. Guess the UK repository must be having a little trouble - thanks for the help!

---


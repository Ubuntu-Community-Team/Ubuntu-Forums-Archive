---
title: "Did I break my apt-get? Need some help"
date: 2006-08-03
forum: Desktop Environments
---

### Post by epikos on 2006-08-03
So I got the little tray icon pop-up saying I needed to update, so I did. But it stalled sitting at 0% forever. So I rebooted, ran sudo apt-get update, and got a ton of weird output that I don't understand. Here's what it spit out:

tlong@odyssey:/etc/apt$ sudo apt-get update
Get: 1 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [191B]
Get: 2 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release [2147B]
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Errftp://cipherfunk.org dapper Release.gpg
  The server refused the connection and said: Sorry, cipherfunk.org already has 20 users logged on.  Try again in 10 minutes.
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Ign [ftp://cipherfunk.org](ftp://cipherfunk.org) dapper Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get: 4 [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages [13.0kB]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get: 5 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Ign [ftp://cipherfunk.org](ftp://cipherfunk.org) dapper/main Packages
Get: 6 [http://archive.czessi.net](http://archive.czessi.net) dapper Release.gpg [483B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Ign [ftp://cipherfunk.org](ftp://cipherfunk.org) dapper/main Sources
Get: 7 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release [4886B]
Get: 8 [http://archive.czessi.net](http://archive.czessi.net) dapper Release [16.9kB]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Errftp://cipherfunk.org dapper/main Packages
  The server refused the connection and said: Sorry, cipherfunk.org already has 21 users logged on.  Try again in 10 minutes.
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Errftp://cipherfunk.org dapper/main Sources
  The server refused the connection and said: Sorry, cipherfunk.org already has 21 users logged on.  Try again in 10 minutes.
Get: 9 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Get: 10 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages [1055B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Ign [http://archive.czessi.net](http://archive.czessi.net) dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Get: 11 [http://archive.czessi.net](http://archive.czessi.net) dapper/main Packages [4287B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper Release.gpg
Get: 12 [http://archive.czessi.net](http://archive.czessi.net) dapper/multiverse Packages [14B]
Get: 13 [http://archive.czessi.net](http://archive.czessi.net) dapper/restricted Packages [14B]
Get: 14 [http://archive.czessi.net](http://archive.czessi.net) dapper/preview Packages [1240B]
Get: 15 [http://archive.czessi.net](http://archive.czessi.net) dapper/universe Packages [8071B]
Get: 16 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages [773B]
Get: 17 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages [2180B]
Get: 18 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources [522B]
Get: 19 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper Release
Get: 20 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources [671B]
Get: 21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Sources
Get: 23 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Packages
Get: 24 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Packages
Get: 25 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Sources
Get: 26 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Sources
Get: 27 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Packages
Errftp://ftp.free.fr dapper/free Packages
  Unable to fetch file, server said ‘Failed to open file.  ’
Get: 28 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Packages
Errftp://ftp.free.fr dapper/non-free Packages
  Unable to fetch file, server said ‘Failed to open file.  ’
Get: 29 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Sources
Errftp://ftp.free.fr dapper/free Sources
  Unable to fetch file, server said ‘Failed to open file.  ’
Get: 30 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Sources
Errftp://ftp.free.fr dapper/non-free Sources
  Unable to fetch file, server said ‘Failed to open file.  ’
Get: 31 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Get: 32 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release [19.6kB]
Get: 33 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [14B]
Get: 34 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get: 35 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [14B]
Get: 36 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Get: 37 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources [14B]
Get: 38 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Get: 39 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources [14B]
Get: 40 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources [14B]
Errhttp://users.lichtsnel.nl dapper-seveas Release.gpg
  Could not connect to users.lichtsnel.nl:80 (129.125.101.191), connection timed out
Errhttp://idefix.eup.uva.es ./ Release.gpg
  Could not connect to idefix.eup.uva.es:80 (157.88.64.191), connection timed out
Fetched 76.5kB in 2m0s (634B/s)
Failed to fetch [http://users.lichtsnel.nl/~seveas/dists/dapper-seveas/Release.gpg](http://users.lichtsnel.nl/~seveas/dists/dapper-seveas/Release.gpg)  Could not connect to users.lichtsnel.nl:80 (129.125.101.191), connection timed out
Failed to fetch [ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/Release.gpg](ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/Release.gpg)  The server refused the connection and said: Sorry, cipherfunk.org already has 20 users logged on.  Try again in 10 minutes.
Failed to fetch [http://idefix.eup.uva.es/paquetes/gaim2.0/./Release.gpg](http://idefix.eup.uva.es/paquetes/gaim2.0/./Release.gpg)  Could not connect to idefix.eup.uva.es:80 (157.88.64.191), connection timed outFailed to fetch [ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/main/binary-i386/Packages.gz](ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  The server refused the connection and said: Sorry, cipherfunk.org already has 21 users logged on.  Try again in 10 minutes.
Failed to fetch [ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/main/source/Sources.gz](ftp://cipherfunk.org/pub/packages/ubuntu/dists/dapper/main/source/Sources.gz)  The server refused the connection and said: Sorry, cipherfunk.org already has 21 users logged on.  Try again in 10 minutes.
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz)  Unable to fetch file, server said ‘Failed to open file.  ’
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz)  Unable to fetch file, server said ‘Failed to open file.  ’
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/source/Sources.gz)  Unable to fetch file, server said ‘Failed to open file.  ’
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/source/Sources.gz)  Unable to fetch file, server said ‘Failed to open file.  ’
Reading package lists... Done
W: GPG error: [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: GPG error: [http://archive.czessi.net](http://archive.czessi.net) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A714EB87D1B1F415
W: You may want to run apt-get update to correct these problems
W: Some index files failed to download, they have been ignored, or old ones used instead.


I don't really know whats wrong, but I don't think I've changed anything recently. Coudl someone look at that and tell me whats wrong?

Thanks.
Epikos

PS: I have pasted my sources.list below, if its needed.
# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb [http://users.lichtsnel.nl/~seveas](http://users.lichtsnel.nl/~seveas) dapper-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
deb-src [http://users.lichtsnel.nl/~seveas](http://users.lichtsnel.nl/~seveas) dapper-seveas all

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) dapper main

# Penguin Liberation Front (packages)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free

# Penguin Liberation Front (sources)
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free

# Bleeding edge wine packages (packages)
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# Bleeding edge wine packages (sources)
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## QuinnStorm (Compiz)
#[http://ubuntuforums.org/attachment.php?attachmentid=7449&d=1143067510](http://ubuntuforums.org/attachment.php?attachmentid=7449&d=1143067510)
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main

## Mario Debian's GAIM 2.0 Repo
deb [http://idefix.eup.uva.es/paquetes/gaim2.0/](http://idefix.eup.uva.es/paquetes/gaim2.0/) ./

## czessi.net (Kubuntu)
#[http://www.czessi.net/kczessi.gpg](http://www.czessi.net/kczessi.gpg)
deb [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) dapper main multiverse restricted preview universe

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free

---

### Post by Dr. Nick on 2006-08-03
I would wait and try again, you got several messages about "20 users already logged in" It may just be a peak time and the servers are to busy for you right now

to fix this error
W: GPG error: [http://www.beerorkid.com]("http://www.beerorkid.com/") dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E

run this from a terminal 

wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -

---

### Post by epikos on 2006-08-03
I got rid of the gpg/pgp key errors, but I'm still getting things like Unable to fetch file, server said ‘Failed to open file.  ’

And then all the lines starting with get, hit, or ign. I don't remember seeing Ign before. and at the end of an apt-get update I get Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

Anyone have an idea how I can get apt-get working again?

---

### Post by Dr. Nick on 2006-08-03
Ok, on the "penguin lieration front" I went to their site and saw this

> This project is now in dormant state, as the plf/ubuntu team resigned due
to lack of time. If you want more detail or want to help, please contact 
misc, either on irc ( #plf@irc.freenode.net ), or send a email on 
misc at zarb.org .


So I would go back into your sources.list and remove them

# Penguin Liberation Front (packages)
deb [ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/]("ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/") dapper free non-free

# Penguin Liberation Front (sources)
deb-src [ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/]("ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/") dapper free non-free


Then re-run 
sudo apt-get update

and post the output again if you get errors

---

### Post by ThunderTor on 2006-11-14
[QUOTE=
to fix this error
W: GPG error: [http://www.beerorkid.com]("http://www.beerorkid.com/") dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E

run this from a terminal 

wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -[/QUOTE]

I just experienced the same key error, and discovered this thread with some googling, but for some odd reason just marking and pasting the above mentioned command, the terminal just stood there blinking forever, after some problem solving I split the two commands and changed the wget commmand to this, 

[QUOTE=] wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O beerorkid.key
sudo apt-key add beerorkid.key[/quote]

Just in case someone has this problem. :)
Running 6,10 Edgy atm

---


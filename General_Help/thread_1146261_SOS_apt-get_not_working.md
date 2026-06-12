---
title: "SOS apt-get not working"
date: 2009-05-02
forum: General Help
---

### Post by lordbux on 2009-05-02
hi
err i am having trouble with both* ap-get update and aptget install* 
no luck fixing it myself
pleas help.

here is the output of *apt-get update*
```

sudo apt-get update
Ign http://security.ubuntu.com gutsy-security Release.gpg
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_GB
Get: 1 http://archive.canonical.com gutsy Release.gpg [189B]
Ign http://archive.ubuntu.com gutsy Release.gpg
Ign http://archive.ubuntu.com gutsy/main Translation-en_GB
Get: 2 http://repository.akirad.net akirad-gutsy Release.gpg [197B]
Ign http://repository.akirad.net akirad-gutsy/main Translation-en_GB
Get: 3 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Ign http://us.archive.ubuntu.com dapper/main Translation-en_GB
Ign http://us.archive.ubuntu.com dapper/restricted Translation-en_GB
Get: 4 http://deb.orangearchive.net gutsy Release.gpg [189B]
Ign http://deb.orangearchive.net gutsy/main Translation-en_GB
Ign http://security.ubuntu.com gutsy-security/main Translation-en_GB
Ign http://security.ubuntu.com gutsy-security Release
Hit http://repository.akirad.net akirad-gutsy Release
Ign http://us.archive.ubuntu.com dapper/universe Translation-en_GB
Ign http://us.archive.ubuntu.com dapper/multiverse Translation-en_GB
Hit http://us.archive.ubuntu.com dapper Release
Hit http://deb.orangearchive.net gutsy Release
Ign http://security.ubuntu.com gutsy-security/universe Packages
Ign http://archive.ubuntu.com gutsy/universe Translation-en_GB
Ign http://archive.ubuntu.com gutsy-updates Release.gpg
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_GB
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_GB
Get: 5 http://archive.ubuntu.com dapper Release.gpg [189B]
Ign http://archive.ubuntu.com dapper/universe Translation-en_GB
Ign http://archive.ubuntu.com dapper/multiverse Translation-en_GB
Ign http://archive.ubuntu.com gutsy Release
Hit http://repository.akirad.net akirad-gutsy/main Packages
Hit http://us.archive.ubuntu.com dapper/main Packages
Hit http://deb.orangearchive.net gutsy/main Packages
Ign http://security.ubuntu.com gutsy-security/main Packages
Ign http://archive.ubuntu.com gutsy-updates Release
Hit http://us.archive.ubuntu.com dapper/restricted Packages
Hit http://us.archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper/multiverse Packages
Err http://security.ubuntu.com gutsy-security/universe Packages
  404 Not Found
Hit http://archive.ubuntu.com dapper Release
Ign http://archive.ubuntu.com gutsy/main Packages
Err http://security.ubuntu.com gutsy-security/main Packages
  404 Not Found
Ign http://archive.ubuntu.com gutsy/universe Packages
Ign http://archive.ubuntu.com gutsy-updates/universe Packages
Ign http://archive.ubuntu.com gutsy-updates/main Packages
Get: 6 ftp://ftp.videolan.org dapper Release.gpg
Err http://archive.ubuntu.com gutsy/main Packages
  404 Not Found [IP: 91.189.88.45 80]
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Ign http://archive.canonical.com gutsy/partner Translation-en_GB
Hit http://archive.ubuntu.com dapper/multiverse Sources
Err http://archive.ubuntu.com gutsy/universe Packages
  404 Not Found [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com gutsy-updates/universe Packages
  404 Not Found [IP: 91.189.88.45 80]
Hit http://archive.canonical.com gutsy Release
Err http://archive.ubuntu.com gutsy-updates/main Packages
  404 Not Found [IP: 91.189.88.45 80]
Ign http://archive.canonical.com gutsy/partner Packages
Ign ftp://ftp.videolan.org dapper Release.gpg
Ign http://archive.canonical.com gutsy/partner Sources
Hit http://archive.canonical.com gutsy/partner Packages
Get: 7 ftp://ftp.videolan.org dapper/universe Translation-en_GB
Hit http://archive.canonical.com gutsy/partner Sources
Ign ftp://ftp.videolan.org dapper/universe Translation-en_GB
Get: 8 ftp://ftp.videolan.org dapper Release
Ign ftp://ftp.videolan.org dapper Release
Get: 9 ftp://ftp.videolan.org dapper/universe Packages
Ign ftp://ftp.videolan.org dapper/universe Packages
Hit ftp://ftp.videolan.org dapper/universe Packages
Fetched 5B in 9s (1B/s)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


```

it seems as if there is some serious trouble.

and when i try to install something 
it says _*could not fetch packages pleas try apt-get update*_

please help me someone
and thanks in advance

opensource live for ever.
thankyou

---

### Post by drs305 on 2009-05-02
You have both dapper and gutsy repositories, both of which are no longer supported. You can used old repositories or install a newer version. Gutsy reached EOL (end-of-life on [noparse]April 18 [/noparse]) so the repositories are probably no longer available.

Added: If you are running gutsy, for the time being you can edit your source.list file and replace the main address in each line with: **[http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu)**
This is the location of EOL repositories. They are not updated.

---

### Post by lordbux on 2009-05-03
so...
does this mean ..when each of the versions reach its EOL then 
i will have to install something new.:guitar:

---

### Post by zvacet on 2009-05-03
> so...
does this mean ..when each of the versions reach its EOL then 
i will have to install something new

Yes,but upgrade is option to.You have mixed source list and if you want to upgrade start from there.Replace your source list with this one 

> deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted

##Universe

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy universe
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates universe

## Multiverse

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Backports

#deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
#deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse 

Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

After this you should be able to upgrade to Hardy witch is LTS (long term support).If you want latest version then it is good to have separate home partition.If you don´t have it make one following [this]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html") tutorial.When you make separate home just install new version of Ubuntu on top of your old root partition.

---

### Post by lordbux on 2009-05-03
AND HAI THANK YOU
that was gr8

but
 is that  i cant use  gusty anymore....
and even if i change to hardy as soon as hardy dies should i change to another
....it's ok with me ofcourse:P
:confused: but..i dont understand why this should be done
can some one kindly please explain how this entire thing work:guitar:

thank you
long live open source:guitar:
...

---

### Post by geirha on 2009-05-03
Every release has a support lifetime of 1.5 years with the exception of long term support (LTS) releases, which has a support lifetime of 3 years (5 years for the server version). If you don't want to go through the hassle of upgrading often, then upgrade to Hardy, which is an LTS release. It's supported until April 2011.

Every fourth/fifth release is an LTS release, and you can upgrade directly from one LTS release to the next, so stick with Hardy until the next LTS release comes along, then upgrade directly to that (either April or October 2010). With each new LTS release, you'll be able to use it for 2-3 years before having to upgrade again.

You'll find instructions for how to upgrade here: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by drs305 on 2009-05-03
Here is how long the current and past releases last/lasted.

[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

---


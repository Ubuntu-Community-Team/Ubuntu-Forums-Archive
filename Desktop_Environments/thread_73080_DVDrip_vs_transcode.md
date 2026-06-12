---
title: "DVDrip vs transcode"
date: 2005-10-08
forum: Desktop Environments
---

### Post by Felave on 2005-10-08
i would like install DVDrip...
it needs of transcode...
but i don't successed to install it.......

i have readed
[http://ubuntuguide.org/#dvdrip](http://ubuntuguide.org/#dvdrip)
[http://ubuntuforums.org/showthread.php?t=548](http://ubuntuforums.org/showthread.php?t=548)

...
the problem is the dependences...

before, with ubuntu backport ALL FUNCTION!!!!!!!!!..

now... NOTHING!!!

Someone have installed DVDrip... and How???

Thanks

please cut and past your source.list file if the yours functions!

---

### Post by GeneralZod on 2005-10-08
Backports recently abandoned an old mirror; make sure your backports line looks like this:

```

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse

```

If not, change it and reload the packages list.  If that doesn't help, post the errors here!

---

### Post by Felave on 2005-10-08
yes yes....
i have yet that

this is my source.list file

```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe
deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse
## Old Mirrormax Backports, now dead Oct. 1 2005 
##deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
##New Official Backports
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
```

---

### Post by GeneralZod on 2005-10-08
Can you post the errors you receive, please?

---

### Post by Hephaestus on 2005-10-12
For me the same thing. I'm using Hoary.

This is the error I get:


De volgende pakketten hebben niet-voldane vereisten:
  dvdrip: Vereisten: transcode (>= 2:0.6.14) maar het is niet installeerbaar
E: Niet-werkende pakketten:

(yes it is Dutch) :smile:

---

### Post by michael_salcher on 2005-10-12
according to the babel fish:

The following packages have unsatisfied requirements: dvdrip: Requirements: transcode (= 2:0.6.14) but it is not installable: Non-working packages:

---

### Post by xtacocorex on 2005-10-12
I also tried to install this progam a couple of weekends ago.

I had the same errors on the repository [which is archive.ubuntu.com], so I just now went to browse the location in Firefox and there is nothing in the folders except for the Release and Package.gz/bz2 files.

---


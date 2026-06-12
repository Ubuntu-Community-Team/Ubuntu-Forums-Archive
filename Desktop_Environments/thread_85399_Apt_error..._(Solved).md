---
title: "Apt error... (Solved)"
date: 2005-11-02
forum: Desktop Environments
---

### Post by michaelharg on 2005-11-02
Hey, im trying to access the multiverse with apt and synaptic but i get this error message ever time i try to edit the repositories i get this message..

[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.151 80]
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.151 80]
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.151 80]
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.151 80]
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz:) 404 Not Found [IP: 82.211.81.151 80]
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz:) 404 Not Found [IP: 82.211.81.151 80]
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz:) 404 Not Found [IP: 82.211.81.151 80]
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz:) 404 Not Found [IP: 82.211.81.151 80]

So i figure i dont have access to them ;), but i dont know why, i havent changed any of the adresses, are there any repository mirrors i could use?

Thanks

Michael Hargreaves

---

### Post by Iandefor on 2005-11-02
How did you add them? by editing /etc/apt/sources.list or by using Synaptic?
Either way, try [this guide]("https://wiki.ubuntu.com/AddingRepositoriesHowto"), it should work. Before you try that guide, I'd advise you to remove those repositories that aren't working.

---

### Post by michaelharg on 2005-11-02
I have tried editing them in the Terminal and in Synaptic, they are the only repositories listed that are in the "Multiverse", i think i must be  missing the adresses of the  multiverse repositories as these were all back-ports. What is the adress of the multiverse repositories?

Thanks

Michael Hargreaves

---

### Post by Ampersand on 2005-11-02
Your /etc/apt/sources.list should be something like this:
```


## Uncomment the following two lines to fetch updated software from the network
 deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

---

### Post by Iandefor on 2005-11-02
just to be absolutely clear, what are the contents of your /etc/apt/souces.list file?

---

### Post by michaelharg on 2005-11-02
i have pasted that into my sources.list, uncommented the repositories for the multiverse, ran sudo apt-get update. Nothing came up about the Multiverse repositories in the terminal so i ran Synaptic and got the errors again so i removed the repositories giving me the 404s. Now i dont get any error messages but i still cant access the Multiverse... Any more suggestions? 

my source.list file:

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb http://gb.archive.ubuntu.com/ubuntu breezy main restricted
 deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted
 deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://gb.archive.ubuntu.com/ubuntu breezy universe
 deb-src http://gb.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

 deb http://security.ubuntu.com/ubuntu breezy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

Thanks

Michael Hargreaves

---

### Post by Ampersand on 2005-11-02
What happens if you add multiverse to the end of each line starting with deb?

---

### Post by mips on 2005-11-02
Try adding this as the last line
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

---

### Post by michaelharg on 2005-11-02
[QUOTE=Ampersand]What happens if you add multiverse to the end of each line starting with deb?[/QUOTE]
 I added the following to my sources.list file,

```
deb http://gb.archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu breezy multiverse
```

and it worked, problem solved thanks very much!

---


---
title: "looking for &quot;make&quot; command."
date: 2006-06-20
forum: Desktop Environments
---

### Post by m.h.shams on 2006-06-20
dear friends, 

im new in linux and  specially ubuntu.

i want to install some software on my ubuntu 6.06, 
but during installation i need to **make** some packages.
and i can't find make command, it seems that i don't have any compiler,

how can i install and use make command. ? 
do i need connect internet for this installation ? (i can't connect internet yet)

help me please.
regards.
shams

---

### Post by taurus on 2006-06-20
Install build-essential and you should be all set...
```

sudo apt-get install build-essential

```

---

### Post by m.h.shams on 2006-06-20
[QUOTE=taurus]Install build-essential and you should be all set...
```

sudo apt-get install build-essential

```[/QUOTE]

apt-get command needs to connect to internet, but i said that i can't connect internet yet. :(

---

### Post by taurus on 2006-06-20
I believe build-essential is on the CD!  So, make sure you have an entry for the CD (first line) in /etc/apt/sources.list and apt-get it...

---

### Post by m.h.shams on 2006-06-20
[QUOTE=taurus]I believe build-essential is on the CD!  So, make sure you have an entry for the CD (first line) in /etc/apt/sources.list and apt-get it...[/QUOTE]


sorry! i don't get your mind.  you say i most change sources.list and add somethig on it ? (sorry : but don't know how and what)

---

### Post by taurus on 2006-06-20
Post the content of your /etc/apt/sources.list here then...
```

more /etc/apt/sources.list <-- to view it!!!

```

---

### Post by m.h.shams on 2006-06-20
here is my sources.list file : 


```

deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://au.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by Ramses de Norre on 2006-06-20
```
sudo apt-cdrom add
``` and it'll ask you to insert your install disc to add it to your sources, when that's finished you can pull packages from the cd.
Run ```
sudo aptitude update && sudo aptitude install build-essential
```.

---

### Post by m.h.shams on 2006-06-20
thanks,

and a question : how can i find the list of packages that available in ubuntu cd ?

thanks again, for your kindly helps

---


---
title: "Cant apt-get alien"
date: 2006-01-06
forum: Desktop Environments
---

### Post by shade11 on 2006-01-06
I've been trying to install alien via apt-get. But as it turns out it is not working. It isn't even in synaptic. I had typed this in at the terminal:

```
sudo apt-get install alien
```

I also went to the alien homepgae. As it turns out the file is an RPM file, but I need alien to convert RPM files.

If someone can please tell me what's wrong. or if they can tell me how to install an RPM file.

---

### Post by Leif on 2006-01-06
have you enabled universe/multiverse in /etc/apt/sources.list ?

---

### Post by shade11 on 2006-01-06
Umm if it isnt soething that isn't set automatically then no. But I will go and check.

EDIT: No it is not enabled. So I will and install it. Where I am I cant download the repositories or download alien so i will tell you later.

---

### Post by Leif on 2006-01-06
you can use this site to give you a good set of repos - I'd use the standard ones, plus backports and plf. then overwrite what's in your /etc/apt/sources.list with this. do a "sudo apt-get update" and then try installing again

---

### Post by opiston on 2006-01-21
Hi all,
I just installed ubuntu 2 days ago, and I have not used linux except at school, so I don't really know much about ubuntu.

I am trying to enable alien also.
I went into /etc/apt/sources.list and I uncommented the universe/multiverse.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse

Then I did sudo apt-get update.
The update was successful, but alien was still unavailable.

Here is my sources.list:
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe




Can anyone help me to solve this problem?
Thanks

Best Regards
opiston

---

### Post by dueY on 2006-01-21
[QUOTE=opiston]
words
[/QUOTE]
Here you go:
```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
```

---

### Post by opiston on 2006-01-21
Hi dueY,
Thank you for your help. I got alien to work now.
I think the main reason that it wasn't working was that I didn't type in

sudo apt-get install alien

I forgot to type it in ...:eek: 

Regards
opiston

---


---
title: "Automatix issues"
date: 2006-01-08
forum: Desktop Environments
---

### Post by neolithic on 2006-01-08
I installed Automatix as directed from the Automatix thread.  However when I try to run it, it tells me that it does not run on Hoary.  I am using 5.1.0 Breezy.  How can I fix this?

---

### Post by neolithic on 2006-01-08
anybody know?

---

### Post by stalefries on 2006-01-08
Can you show us the contents of your /etc/apt/sources.list file? I had this same problem, and it was because I had the hoary repos enabled, and not the breezy ones.

---

### Post by neolithic on 2006-01-08
yeah, where is it located?

---

### Post by lamego on 2006-01-08
On a terminal window:
cat /etc/apt/sources.list

---

### Post by neolithic on 2006-01-08
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by lamego on 2006-01-08
From  a terminal run:
sudo gedit /etc/apt/sources.list
(enter your default user password)

On the text editor: Search -> Replace
hoary 
with 
breezy
Replace all

It should work now...

---

### Post by neolithic on 2006-01-08
Thanks.  It worked exactly as you described

---


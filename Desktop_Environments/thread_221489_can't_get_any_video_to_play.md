---
title: "can't get any video to play"
date: 2006-07-23
forum: Desktop Environments
---

### Post by tonym2 on 2006-07-23
I updated the linux kernel the other night thru the update manager. Now, I can't get any video to play. Mpeg, mpg, wmv, nothing. Not video files on my hard drive or embeded in a browser windo.

Trying to ap-get install w32codecs, totem-xine and mozilla-mplayer all say the latest version is installed.

Anyone know why it won't work all of a sudden? Is it the new kernel I installed?

---

### Post by madmetal on 2006-07-23
which kernel?
try to find restricted-modules for your new kernel from synaptic.

---

### Post by tonym2 on 2006-07-23
I'm using 2.6.1526-386. 

I'm a n00b so please explain how I find the modules through synaptic? How are they listed?

Is there an easier way through apt-get?

Thanks!

---

### Post by tonym2 on 2006-07-23
OK, In synaptic I was able to find all:

w32codecs
totem-xine
mozilla-mplayer

I was able to reinstall all of tehm, still nop joy. Video in firefox browser just flashes a blue screen then back to black. no video or sound gets played.

This worked before I installed the kernel update via the automatic update manager (when I logged in to Ubuntu Friday night, there they were ready to be  installed)

Anything else you could tell me would be appreciated.

Thanks!

Tony

---

### Post by madmetal on 2006-07-23
video mp3 and sound in general is ok now?
if the problem is only in firefox look for plug-ins and settings for multimedia support.

---

### Post by tonym2 on 2006-07-23
nope, nothing is working. I guess what I did had no effect.

do I need to add different repositories? Here's my list:

## Uncomment the following two lines to fetch updated software from the network
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

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free 

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free 


Am I missing an important one?

---

### Post by tonym2 on 2006-07-23
Bump, 

Can anyone help me on this? I am basically looking fro exactly what to do and how to do it. Please forgive. Trying to dump Windows all together and finding the transition a little complicated.

Thanks for any and all help...

Tony

---


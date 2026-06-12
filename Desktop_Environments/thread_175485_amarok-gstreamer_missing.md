---
title: "amarok-gstreamer missing"
date: 2006-05-13
forum: Desktop Environments
---

### Post by Fedcer on 2006-05-13
Hi, I'm trying to set up the gstreamer engine for amarok but I cannot find the package "amarok-gstreamer".

This is my sources.list

> 
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


Is something missing in the reposteries?

Thanks,

Fedcer

---

### Post by richbarna on 2006-05-13
Open your Konsole and type :-
> sudo apt-get install amarok-gstreamer

Edit: Yeah sorry, seeing lots of posts about Dapper not using gstreamer.
       I will check this out.

---

### Post by Fedcer on 2006-05-13
I've already tried. I get:

> 
Package amarok-gstreamer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package amarok-gstreamer has no installation candidate


---

### Post by richbarna on 2006-05-13
Yeah you're right, I had a look in the repository list :-
[http://packages.ubuntu.com/dapper/sound/]("http://packages.ubuntu.com/dapper/sound/")

I was thinking of upgrading to Dapper, but now that I am seeing so many problems, I think I'll leave it for a while ;)

---

### Post by niviche on 2006-06-18
It's quite a big problem for people working with sound that amarok-gstreamer got removed from the repositories. Amarok works now only with the xine engine, which is quite buggy, to say the least.

I have the exact same problem as this [Suse 10.1 user](http://forums.suselinuxsupport.de/index.php?showtopic=38234), and just can not use Amarok very much. Makes me want to downgrade to Breezy. :(

---

### Post by jalonsom on 2006-06-22
Please give us amaroK-gstreamer for Dapper!!!

I personally want replaygain support...

---


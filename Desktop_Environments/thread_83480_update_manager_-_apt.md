---
title: "update manager - apt"
date: 2005-10-28
forum: Desktop Environments
---

### Post by tieflingrogue on 2005-10-28
while trying to install w32codecs, i found a reference to a .deb script in ubuntu forums that supposedly would download and install everything for you.  When the script is executed........it trys to connect to the mplayer website to download the w32codec files.  However, it can't connect to the site and retries connecting 20 times.  Heres the problem:

Now every time I do an update, this script runs and trys to download the w32codec files 20 times...........so it takes forever for an update to finish.  How can I "flush" this process so that I doesn't continue to run everytime I do an update.   

Thanks

---

### Post by stuporglue on 2005-10-28
Check your /etc/apt/sources.list file for a line that doesn't seem to match the others. You can probably do this in the Synaptic GUI too and look for a repository that doesn't seem to fit in.

---

### Post by tieflingrogue on 2005-10-28
Here's my sources.list----I think the problem is that this .deb file keeps running when i do an update.........just need to stop it from running.
---------------------------------------------------------------------------------------------
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.


# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

#backup Mirror - FAST
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted universe

## mirror provided thanks to OVH [http://ovh.com](http://ovh.com)
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

---


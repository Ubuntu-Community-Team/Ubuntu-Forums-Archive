---
title: "Error when installing 0ad"
date: 2015-11-08
forum: Gaming &amp; Leisure
---

### Post by thewonderland on 2015-11-08
I used to have 0ad installed, and i used to play it. Some weeks ago i wanted to play again after a pause and i type 0ad in the terminal and it says 0ad is not installed, so i tried installing it, this is what i get 

```
no@alpha01:~$ sudo apt-get install 0AD
[sudo] password for no:
Reading package lists ... Done
Building dependency tree
Reading state information ... Done
Some packages could not be installed. It may mean that you have requested
an impossible situation or if you are using the unstable distribution
that some required packages have not yet been created or been moved
from "Incoming".
The following information may help to resolve the situation:


The following packages have dependencies that can not be satisfied:
  0AD: Depends: libboost-filesystem1.46.1 (> = 1.46.1-1) but it can not be installed
          Depends: libicu48 (> = 4.8-1) but it can not be installed
E: Unable to correct problems, you have held broken packages.
```
I used google translate to translate, i am swedish.

And this is what i get when i try to install from software-center (Also translated)

```
The following packages have unmet dependencies:


0AD: PreDepends: dpkg (> = 1.15.6 ~) but 1.17.5ubuntu5.4 will be installed
     Depends: 0AD data (<= 0.0.18-0ubuntu1 ~ 4.12 ~ wfg2) but 0.0.18-0ubuntu1 ~ 4.12 ~ wfg1 will be installed
     Depends: 0AD data-common (<= 0.0.18-0ubuntu1 ~ 4.12 ~ wfg2) but 0.0.18-0ubuntu1 ~ 4.12 ~ wfg1 will be installed
     Depends: libboost-filesystem1.46.1 (> = 1.46.1-1) but will not be installed
     Depends: libc6 (> = 2.15) but 2.19-0ubuntu6.6 will be installed
     Depends: libcurl3-gnutls (> = 7.16.2-1) but will be installed 7.35.0-1ubuntu2.5
     Depends: libgcc1 (> = 1: 4.1.1) but 1: 4.9.1-0ubuntu1 will be installed
     Depends: libicu48 (> = 4.8-1) but will not be installed
     Depends: libjpeg8 (> = 8c) but 8c 2ubuntu8 will be installed
     Depends: libminiupnpc8 (> = 1.6) but will be installed 1.6-3ubuntu2.14.04.2
     Depends: libopenal1 (> = 1: 1.13) but 1: 1.14-4ubuntu1 will be installed
     Depends: libpng12-0 (> = 1.2.13-4) but will be installed 1.2.50-1ubuntu2
     Depends: libsdl1.2debian (> = 1.2.10-1) but will be installed 1.2.15-8ubuntu1.1
     Depends: libstdc ++ 6 (> = 4.6) but 4.8.4-2ubuntu1 ~ 14:04 will be installed
     Depends: libvorbisfile3 (> = 1.1.2), but will be installed 1.3.2-1.3ubuntu1
     Depends: libwxbase2.8-0 (> = 2.8.12.1) but 2.8.12.1 + dfsg-2ubuntu2 will be installed
     Depends: libwxgtk2.8-0 (> = 2.8.12.1) but 2.8.12.1 + dfsg-2ubuntu2 will be installed
     Depends: libxcursor1 (> 1.1.2), but 1: 1.1.14-1 will be installed
     Depends: libxml2 (> = 2.7.4) 2.9.1 + dfsg1-3ubuntu4.4 but will be installed
     Depends: zlib1g (> = 1: 1.2.0) but 1: 1.2.8.dfsg-1ubuntu1 will be installed
```

---

### Post by oldrocker99 on 2015-11-10
I was having similar problems, to the point that I couldn't install wine (?!). I fixed it by switching to a different repository. Tripadvisor.com's repo has eliminated those problems.

---

### Post by oldrocker99 on 2015-11-10
I was having similar problems, to the point that I couldn't install wine (?!). I fixed it by switching to a different repository. Tripadvisor.com's repo has eliminated those problems.

---


---
title: "[SOLVED] Installing Alien Arena 2007"
date: 2007-12-05
forum: Gaming &amp; Leisure
---

### Post by lucast on 2007-12-05
Hi,

I am running Ubuntu 7.10.  Could you tell me if the version of Alien Arena in the repositories is the Alien Arena 2007 version?

If not I have been trying to follow the instructions in this post:

([http://ubuntuforums.org/showthread.php?t=476478&highlight=iNSTALL+aLIEN+aRENA+2007](http://ubuntuforums.org/showthread.php?t=476478&highlight=iNSTALL+aLIEN+aRENA+2007)) 

wget -c [http://icculus.org/alienarena/files/alien-arena_6.05-0ubuntu1~feisty1_i386.deb](http://icculus.org/alienarena/files/alien-arena_6.05-0ubuntu1~feisty1_i386.deb)

wget -c [http://icculus.org/alienarena/files/alien-arena-data_6.05-0ubuntu1_all.deb](http://icculus.org/alienarena/files/alien-arena-data_6.05-0ubuntu1_all.deb) 

sudo dpkg -i alien-arena*


and the refrences to the .deb show that the file does not exist.

If its not the one in the repoositories could someone help me with how to install it please.

Thank you for any assistance! :-)

---

### Post by Zylar on 2007-12-05
Go to [http://red.planetarena.org]("http://red.planetarena.org") and hit their download section, download the linux version from a mirror.  It's a zip, so just unzip it anywhere.  Open a terminal, browse to the location you unzipped it to, and run "./crx".

Mine needed some other dependencies, like libcurl3, etc. 

Good luck,

---


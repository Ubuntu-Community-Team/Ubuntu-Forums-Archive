---
title: "Ubuntu 11.10 and snackr"
date: 2011-11-17
forum: Desktop Environments
---

### Post by jdgr on 2011-11-17
Hi,

I'm trying to install the RSS ticker program Snackr on ubuntu 11.10 x64. The problem I am running into is that when installing the snackr.air file, it gives the error message:

> Sorry, an error has occurred.

The application could not be installed. Try installing it again. If the problem persists, contact the application author.

Error# 1I have install adobe air manually from the following site: [http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/) and through looking at other issues, I think I have traced the issue to being with dpkg and now forcing proper version numbers. Is there anyone that has installed this program on 11.10 or knows how to ignore the version check when it is an adobe.air file running dpkg?

Thanks,
Jeremy

---

### Post by jerkfaceirl on 2012-02-02
Follow the comment here:

[http://askubuntu.com/questions/71760...art-with-digit](http://askubuntu.com/questions/71760...art-with-digit)

worked for me.

---

### Post by jdgr on 2012-02-02
Thanks for the reply, let me look into and give it a try.

---

### Post by jdgr on 2012-02-02
It doesn't work. I had to play around with it since I am running 64-bit, so I found the 1.15.8.4ubuntu3_amd64.deb package and tried running the same command, but it won't downgrade. It gives the following messages:

> dpkg: error: You have more than one architecture instance for some
installed 'Multi-Arch: same' packages, to be able to downgrade dpkg
you will need to have only one instance installed per package.and

> dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
dpkg: error processing dpkg_1.15.8.4ubuntu3_amd64.deb (--install):
 there is no script in the new version of the package - giving up
Errors were encountered while processing:
 dpkg_1.15.8.4ubuntu3_amd64.debI've tried finding other ways to downgrade. The only alternate I found is to straight remove dpkg and install this one, but if I did so, it would have to uninstall half the programs on my system (like wget, wine, and a whole lot of other programs that I don't know their purpose). I really don't dare attempt that for fear of crippling my system and not getting it back properly (manually reinstalling programs that I don't even know I lost is not something I want to run into).

Any ideas?

---


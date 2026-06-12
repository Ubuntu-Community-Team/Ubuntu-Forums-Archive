---
title: "Compiz on draper"
date: 2006-10-20
forum: Desktop Environments
---

### Post by BdON003 on 2006-10-20
Hello all.  I'm pretty new to linux and I have just been jumping in in order to get the feeling of it.  I'm trying to install Compiz on my system using this guide : [http://www.tectonic.co.za/view.php?id=1153]("http://www.tectonic.co.za/view.php?id=1153")
when I get to step 2: sudo apt-get install xserver-xgl compiz compiz-plugins compiz-core compiz-manager csm cgwd cgwd-themes

it returns that it cannot find the compiz-manager package.  My sources.list looks like this: 

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sarge main
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) dapper main main-all
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://gandalfn.club.fr/ubuntu/](http://gandalfn.club.fr/ubuntu/) dapper .

Can anyone help?

---

### Post by davec64 on 2006-10-20
Hi,

The Compiz repositories have been updated, i think you'll find that the cgwd/quinn side of things has broken away and is now called BERYL (I know, what a name!)

Have a search on the forum for Beryl.

I've installed it and it is really good!

All the best.

---

### Post by BdON003 on 2006-10-20
Thanks for your reply, I ran across the name Beryl a lot when searching before I actually posted, but I'm a little unclear.  Do Beryl and Compiz run side-by-side?  What was the cgwd/quinn "side"?

---

### Post by ayoli on 2006-10-20
cgwd was the compiz-quinn window decorator. compiz quinn was a community hacked version of compiz vanilla, but it's now forked into a new project name beryl. compiz and beryl can't work together.
there is many how to's on this forum to install beryl and also here:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu](http://wiki.beryl-project.org/index.php/Install/Ubuntu)

---


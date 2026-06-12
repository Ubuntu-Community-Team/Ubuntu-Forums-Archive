---
title: "GRASS GIS repositories and packages"
date: 2007-09-08
forum: Education &amp; Science
---

### Post by Tachyon1000 on 2007-09-08
I have noted that the GRASS GIS packages are a bit dated.  Current version is 6.2.2 whereas the only packages available for Ubuntu are 6.0.2.  There have been substantial GUI and performance improvements in the current version.  I also note that the packages for the current version are available in Debian sid and lenny repositories.  This leads me to the question as to why these more current packages are not available in Ubuntu.  I realize most people are apt to build from sources to get the current versions but I had thought that part of the goal of Ubuntu was offering easy and stable solutions to Linux users, as opposed to struggling with building from sources.  Is there some way that the current version of GRASS GIS can make its way into the repositories available to Feisty?

---

### Post by Tachyon1000 on 2007-09-08
GRASS GIS 6.0.2, the package currently available with Ubuntu, was released in February **2006**.  Since that's nearly 2 years now, it might be great to get an update.

[http://grass.itc.it/grass60/](http://grass.itc.it/grass60/)

GRASS GIS 6.2.2 was released July 17, 2007

---

### Post by LaserJock on 2007-09-08
The version of GRASS in gutsy (7.10) is 6.2.2 as we sync our packages from Debian unstable. We don't put new upstream versions (6.0.2 -> 6.2.2) in our stable releases (-security or -updates repositories). What you **can** do is request a backport to the feisty-backports repo. Check out [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports) for more info, specifically the "How to request new packages" section.

Keep in mind, we do try to keep up with new releases as well as we can while trying to the releases stable. However, sometimes with our limited resources sometimes things can slip through the cracks so there's no harm in asking.

Overview of GRASS versions in Ubuntu:
   [https://launchpad.net/ubuntu/+source/grass](https://launchpad.net/ubuntu/+source/grass)

Overview of GRASS versions in Debian:
  [http://packages.qa.debian.org/g/grass.html](http://packages.qa.debian.org/g/grass.html)

Hope that helps.
-LaserJock

---

### Post by timmie on 2007-09-10
Please find more up to date packages here:

[http://les-ejk.cz/ubuntu/](http://les-ejk.cz/ubuntu/)

the gpg key do not really verify...

But packages work well.

---

### Post by Nikos.Alexandris on 2007-10-21
Has anybody got grassaddons and other modules isntalled?

I am stuck with getting various modules compiled and installed for GRASS under feisty.

As far as I understand I need the source code of GRASS in order to compile extre modules.

The GRASS installation under ubuntu using "apt-get" does not place the source code somewhere in the system. So it is required to get source GRASS code, compile and install it. Afterwards it is possible to compile GEM ( [http://grass.itc.it/grass62/manuals/html62_user/gem/index.html](http://grass.itc.it/grass62/manuals/html62_user/gem/index.html) ) and use it in order to integrate easily other modules.

It's a bit complicated for me... 

Is there an ubuntu-specific compilation manual (for GRASS) or another way to get external modules to work?

Thanks in advance!

---

### Post by shawana on 2009-07-17
hELLO
hOW R U ALL?
CAN ANY ONE GUIDE ME ABOUT THE SUBMITION OF A THIRD PARTY TOOL FOR GRASS TO PERFORM DENSITY SLICING
WHERE SUOUD I SUBMIT TAHT?
 
WITH bEST REGARDS
sHAWANA

---


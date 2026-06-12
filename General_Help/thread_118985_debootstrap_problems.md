---
title: "debootstrap problems"
date: 2006-01-18
forum: General Help
---

### Post by jpaechnatz on 2006-01-18
hi there!

I'm trying the following:

debootstrap --verbose --arch i386 breezy /space/vservers/test1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

or

debootstrap --verbose --arch i386 sarge /space/vservers/test2 [http://ftp2.de.debian.org/debian](http://ftp2.de.debian.org/debian)

I tried the ubuntu version of debootstrap 0.3.1.2 (I think) and version 0.3.3 of debian.

in both cases:
debootstrap.log shows some /dev/null permission denied entries.

breezy:
W: Failure while configuring base packages.  This will be attempted 5 times.
at least  "I:Base system installed successfully." but it does NOT work. 

sarge:
Errors were encountered while processing:
var/cache/apt/archives/bash_2.05b-26_i386.deb
var/cache/apt/archives/e2fsprogs_1.37-2sarge1_i386.deb
and exits with 
W: Failure while unpacking required packages.  This will be attempted up to five times.

could somebody help me or give me some advise, please?
the whole thing is thought as preparation for a vserver test, but if debootstrap is not working properly, it seems senseless for me to continue.

thanks!

cu joh.

---


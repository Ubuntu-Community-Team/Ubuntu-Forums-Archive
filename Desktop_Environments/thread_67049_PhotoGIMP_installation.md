---
title: "PhotoGIMP installation"
date: 2005-09-19
forum: Desktop Environments
---

### Post by dbee on 2005-09-19
Anyone having trouble installing photoGIMP ???

I can't do it unfortunately.

Is there a .deb somewhere out there ??

Thanks

---

### Post by rejser on 2005-09-19
I made a deb with checkinstall when i tried gimpshop.
More trouble then it was worth, couldn't see any difference, so similar to start with.
But if you still want to try

sudo apt-get install checkinstall

download gimppshop source
tar xfz (if tar.gz) tar xfj (if tar.bz2) gimp***** (what the name of the file you downloaded is)

cd gimp**** (whatever folder that's created)
./configure (check if any error-mess)
make 
checkinstall (which creates a deb-file, maybe it is make checkinstall, don't remember, just try, if checkinstall doe nothing, try make checkinstall)
dpkg -i filnameof created file.deb

---

### Post by dbee on 2005-09-19
Hi rejser,

ya, i have downloaded it and everything, and I was going to do a checkinstall but unfortunately I keep getting non-descript ./configure errors of different types ...
 
It's really annoying ... you don't still have the .deb file available do you ??

---

### Post by Blue1k on 2005-09-20
List the errors..I'm finally getting it to install so I can be of some help.

also see my other post asking how to do this:

[http://ubuntuforums.org/showthread.php?p=361398#post361398](http://ubuntuforums.org/showthread.php?p=361398#post361398)

I also made a deb package for Hoary if you would like to try it. :)

---


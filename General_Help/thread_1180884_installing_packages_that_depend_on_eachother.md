---
title: "installing packages that depend on eachother"
date: 2009-06-07
forum: General Help
---

### Post by Zacksd on 2009-06-07
I'm following a guide on how to set up my wireless drivers and get hooked up to the internet [http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526) and i'm trying to install all the packages i need to install the build essentials, well once i got into after about an hour of moving back and forth with my thumb drive i ran into 2 packages i need to install to continue, but they both depend on each other

 g++-4.4_4.4.0-5ubuntu1_amd64.deb
 and 
libstdc++6-4.4-dev_4.4.0-5ubuntu1_amd64.deb

so if anybody could please let me know what it is i may be doing wrong ( and i have both of them in the same directory) or if it is bugged, or if there is an easier way of setting up my wireless then plz help me, i'll be on the forums all day trying to figure this stuff out thx

---

### Post by kostkon on 2009-06-07
You could try using [*Keryx*]("http://keryxproject.org/") to transfer the packages to the PC that you want to fix, instead of trying to do it manually.

---

### Post by ChaiTan on 2009-06-07
You could use offapt to download all the deps automatically on windows
Homepage: [http://code.google.com/p/offapt/](http://code.google.com/p/offapt/)
Windows binary: [http://offapt.googlecode.com/files/offapt-0.1.1.zip](http://offapt.googlecode.com/files/offapt-0.1.1.zip)
How to: [http://code.google.com/p/offapt/wiki/offaptUsage](http://code.google.com/p/offapt/wiki/offaptUsage)

---


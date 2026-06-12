---
title: "Dell Studio 15"
date: 2008-10-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ukera on 2008-10-26
Hello all of my fellow ubuntu lovers.  I recently purchased a dell studio 15 for my birthday.  It's pretty sweet overall, except for the fact that it's running vista.  So anyways, I tried to boot up ubuntu with my cd, while booting up.. the loading stage went through, but the part were it goes to the light brownish screen didn't work.  I got whats known as the WSoD(white screen of death).  For those of you who don't know what that looks like their are plenty of pics on google images.  It's not the cd because I tried SLAX.  Also got the WSoD, then I loaded "VESA KDE" and it didn't give me the WSoD.  So I was wondering if there was a way to use VESA KDE on ubuntu..

-ukera

---

### Post by suncoolsu on 2008-10-27
I had a similar problem on my brand new Dell Studio 1535 - This is what I did as suggested by forum members.

-boot in recovery mode (it comes as an option when you select the operating system i.e. grub)
-edit the xorg.conf file in /etc/X11/ 
-under the devices section - change the driver to "vesa"
-type telinit 2

this should solve the problem (it did for me) 
follow this thread for minor details ..

[http://ubuntuforums.org/showthread.php?t=955550&highlight=suncoolsu](http://ubuntuforums.org/showthread.php?t=955550&highlight=suncoolsu)

Although I am still not able to run my ubuntu with "more aesthetically pleasing set of effects mode" (in Visual Effects). If you figure out a way please post the solution

Hope this helps
B.

---


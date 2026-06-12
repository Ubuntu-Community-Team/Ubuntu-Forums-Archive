---
title: "newbie: how to (really) force version in synaptic package manager?"
date: 2009-04-05
forum: General Help
---

### Post by sirpelidor on 2009-04-05
hi, i've downloaded re-compiled a package from source because the default apt-get install didn't come with the options i needed.

now that i got my package installed, Synaptic Package Manager kept telling me I have 1 update available - foo.   If i try to "update" it, it'll automatically override what I've done.

when google on how to stop package manager from updating that particular software, it said i can use "force version" (ctrl E) to keep it from updating.  I thought I did that, but that little "update available" icon still shows up on the screen.  I must have missed a step or 2...

would anyone please help me verify what I did wrong?

1) fire up package manager
2) search for the package that was installed
3) highlight it then hit Ctrl E
4) 2 options in drop down list:
   -version.x.foo(now)
   -version.x.foo(hardy)
5) pick "now"  since that should be the one i compiled...
6) click force version
7) quit package manager...but then it said if i quit, nothing will be save?  (how to  "save")???

---

### Post by spiderbatdad on 2009-04-05
if you select a package and then go to the package menu at the top of the window you should see an option to "lock version."

---

### Post by sirpelidor on 2009-04-07
spiderbatdad, thank you for your respond.  i tried your suggestion and that "update available" star still shows on the upper right hand corner :(


this is what i noticed:
-if i install the suggested update, that "update available" icon will goes away, but then the application won't contains the additional option i wanted.

-if i then install my version of the software, as soon as I run "dpjg -i foo" that "update available" icon pops up again.

-i tried to remove it with purge option, then reinstall again, still doesn't work (guess it has nothing to do with the configuration file?)

to recap my problem again:

->i have the exact same version of software by downloading from dpkg source.  All i did was add additional option via configure file.  How can I keep Update manager from telling me "new update is available" after i got it installed?

thank you :)





p.s:  been googling around and found this...looks like it is a bug:
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/313614](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/313614)

---


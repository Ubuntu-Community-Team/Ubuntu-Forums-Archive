---
title: "Kubuntu-Desktop not installing"
date: 2006-10-01
forum: Desktop Environments
---

### Post by ljamie82 on 2006-10-01
So I've installed ubuntu 6.06 finally... did a clean install... now i'm trying to apt-get install kubuntu-desktop and i'm getting dependency problems... it first tells me it cant install language-selector-qt... if i try to install that manually it tells me it depends/can not install language-selector-common.... i've looked and can find no reference to this... any help?

like i said I have 6.06, runnin on a g3 ppc (didn't post in the mac forumn because I do not believe this to have anything to do with running on a ppc)... anyway I appreciate the help.

---

### Post by aysiu on 2006-10-01
Dependency problems usually come from conflicting repositories.

Get a fresh sources.list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then try again: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by ljamie82 on 2006-10-01
ok so i did that... now i've got the same problem, but with a different dependency...
it now tells me that amarok is a dependency but is not going to be installed...when i try to install amarok it tells me libifp4 is not installable...as well as amarok-zine or something along those lines

---

### Post by ljamie82 on 2006-10-01
isn't there a way to force install something if i knwo all of the dependencies SHOULD be there?  what would be the problem with doing that if i feel confident it should all d/l and install regarless of it saying it is failed?

---

### Post by ljamie82 on 2006-10-02
is it just me or does dapper seem really buggy?   Maybe it is just the ppc version?  I've never used it before.  But I have had more problems since I installed this than I have EVER had before.

---


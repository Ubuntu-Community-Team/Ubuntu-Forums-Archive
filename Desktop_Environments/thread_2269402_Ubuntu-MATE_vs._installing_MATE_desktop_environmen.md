---
title: "Ubuntu-MATE vs. installing MATE desktop environment"
date: 2015-03-15
forum: Desktop Environments
---

### Post by cogset on 2015-03-15
I don't know if it is OK to ask here, but what would be the difference(s) in choosing to install Ubuntu-MATE as opposed to installing the MATE desktop on top of  a standard Ubuntu version?
I've done that before in a VM, apparently everything worked OK (as far as I can tell), now I'm wondering if there may be other advantages in installing an Ubuntu-MATE iso, apart from the fact that everything is already there.

Maybe there is also a better integration of the MATE components with the core OS? Or maybe unnecessary parts of the standard Unity desktop are not present in Ubuntu-MATE?

---

### Post by v3.xx on 2015-03-15
One difference is Mate from the site is version 1.8 and on top of ubuntu currently is v1.6.

I don't know if ubuntu 14.10 is any different.

I run Mate 14.04 from the site and have not spent any time on Ubuntu-mate.

---

### Post by Frogs Hair on 2015-03-15
The first Ubuntu Mate official 15.04 release currently in development won't include long term support AFIK. If you install the Mate DE on 14.04 the under lying Ubuntu LTS will be supported for five years . There is always some clutter and application duplication after installing more than one desktop environment.

---

### Post by nargaroth_reg on 2015-03-21
They've made an image for the lts version, you can download it from [https://ubuntu-mate.org/trusty/](https://ubuntu-mate.org/trusty/) . I installed that one and haven't had any problems (like missing components). Basically I prefer that method because, as Frogs Hair mentioned, you get less duplicated applications and unnecessary packages installed.

---

### Post by v3.xx on 2015-03-21
I do not run Mate on top of Ubuntu, but looking through the packages I think this may be the route to go.

**mate-desktop-environment-core**:
This package depends on a very basic set of programs that are necessary to
start a MATE desktop environment session. The set of programs includes the
MATE window manager (Marco), the MATE file manager (Caja), the MATE
control center and a limited set of other obligatory MATE desktop components.

---

### Post by cogset on 2015-03-22
Well... installing only** mate-desktop-environment-core** will give me a basic MATE environment whilst still keeping all the packages from the current desktop: I would not want that ;) 

 I would rather install the iso suggested here [https://ubuntu-mate.org/trusty/](https://ubuntu-mate.org/trusty/) (which as a matter of fact I had already downloaded), I just wanted to understand  if I should still expect to find remnants of the Unity environment there (or any other desktop) or if that iso has been precisely tailored to only use the MATE desktop, cutting off all unneeded dependencies, libraries and so on.

---

### Post by v3.xx on 2015-03-22
> that iso has been precisely tailored to only use the MATE desktop

Yes, you get just the Mate desktop installed by default and nothing else, but you will find libunity packages installed.  No way around that as far as I know.

---

### Post by v3.xx on 2015-03-22
Just thought of something
```
dpkg --get-selections > installed_apps
```
Run that in a live session (try mate ubuntu session) and you will have a *alphabetize list* of all installed packages placed in your home folder.

---

### Post by bookrt on 2015-03-24
> **v3.xx said:**
> Yes, you get just the Mate desktop installed by default and nothing else

Yes, I have not done it myself but I expect it would be the same as KUbuntu, XUbuntu, etc. This would be the most elegant way of doing it so that you don't get duplicate file managers, etc.

---

### Post by ubunt72 on 2015-03-28
Can Cinnamon and MATE co-exist?   That is, if you use the Ubuntu MATE 15.04 (right now at beta 2) .iso for the install and then after, install Cinnamon?   I am just curious.   I tried Ubuntu MATE 15.04 (LIVE media) and really liked it.   Perhaps, I wouldn't need Cinnamon but I am just wondering what the experience would be if you installed the Cinnamon desktop afterwards.

---

### Post by cogset on 2015-04-03
As far as I know, you can basically install how many desktop  environments as you want, as long as they are available for your  distribution -in fact, many distros come with more than one desktop  environment by default (you usually can choose which one to use at the  login screen), and you can always remove the one you don't want and/or  add another one.

But then, removing a desktop environment almost  always results in leaving behind stuff that can't be eliminated because  it will break something, and adding another one on top of the default will  likely result in this > There is always some clutter and  application duplication after installing more than one desktop  environment as Frogs Hair pointed above.

So yes, I'd say  you can probably install Cinnamon on Ubuntu-Mate (Mint had both MATE and  Cinnamon installed a while ago), as long as you add the right Cinnamon  repo for Ubuntu.

I originally asked if Ubuntu-Mate would be  cleaner than a standard Ubuntu installation on which I add MATE, looks  like it will probably be but I reckon  I'll have to try a live session to see how different it is.

---


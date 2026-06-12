---
title: "uninstall memtest86+"
date: 2010-01-20
forum: Desktop Environments
---

### Post by DougZ on 2010-01-20
I'd like to uninstall memtest86++.  The odds are 99.999% in favor I will never ever EVER use it, and if I do I'll boot off a live cd.

when I issue the command

sudo apt-get remove memtest86+

it tells me it is going to uninstall memtest86+ and ubuntu-standard.  Not exactly what I want.  Is there a way to force it to uninstall memtest86+ without uninstalling the dependent package ubuntu-standard.

These package dependencies just kill me...

---

### Post by x33a on 2010-01-20
if you are mainly annoyed by the grub entry, just remove it from you grub configuration file. i don't know of the deps, but the package shouldn't be taking too much of your hard drive space.

---

### Post by DougZ on 2010-01-20
Yes I could do that, but I am a firm believer in removing things that are not going to be used.  Truly removed.

I have seen countless machines run out of disk space because of all those "little" installations that are being not used.

So, again: Is it possible to uninstall this without uninstalling ubuntu-standard?

---

### Post by x33a on 2010-01-20
I am not using ubuntu, so i can't comment on the dependencies. but, if apt is telling you that ubuntu-standard would be removed, then i don't think there is any other way of uninstalling memtest.

---

### Post by mcduck on 2010-01-21
> **DougZ said:**
> Yes I could do that, but I am a firm believer in removing things that are not going to be used.  Truly removed.

I have seen countless machines run out of disk space because of all those "little" installations that are being not used.

So, again: Is it possible to uninstall this without uninstalling ubuntu-standard?

you cant uninstall  some package's dependency without either uninstalling the dependent package or breaking it. However that's meaningless in this situation, it's absolutely safe to uninstall the ubuntu-standard -package.

Ubuntu-standard, like ubuntu-desktop and many others, is just a empty metapackage that contains nothing. It has all the packages of standard CLI Ubuntu system as it's dependencies, but no package depends on it. So installing ubuntu-standard will bring all the packages in standard system with it, uninstalling it will only uninstall the metapackage itself. You'll want to have this kind of packages installed during release upgrades, to mae sure all new stuff gets installed, but otherwise uninstalling them is absolutely safe thing to do.

---

### Post by DougZ on 2010-01-21
In other words it cannot be done without breaking something.

Seems odd that there is an option to install ignoring dependencies, but not one to uninstall ignoring dependencies.

Moot point anyway.  Just hit a "show stopper" trying to convert over from XP:  digital camera downloads do not work seamlessly, and is just plain broken if you have 2 users.

Gonna file it as a bug and go back to using XP.  Someday... (of course been saying that since Breezy)

---

### Post by 2hot6ft2 on 2010-01-21
You mean in Grub2 like this?
Applications > Accessories > Terminal
```
sudo chmod -x /etc/grub.d/20_memtest86+
```
then
```
sudo update-grub
```
From this guide on Grub2 section 7 here:
[URL="http://ubuntuforums.org/showthread.php?t=1195275"]The Grub 2 Guide
(formerly Grub 2 Basics)[/URL]
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by DougZ on 2010-01-21
That worked, as would manually editing the grub entries.

It still does not physically *remove* memtest86++.  Minor irritant anyway.  Was just curious if it can be done.  The answer seems to be no.

---

### Post by mcduck on 2010-01-22
> **DougZ said:**
> In other words it cannot be done without breaking something.

Seems odd that there is an option to install ignoring dependencies, but not one to uninstall ignoring dependencies.

Moot point anyway.  Just hit a "show stopper" trying to convert over from XP:  digital camera downloads do not work seamlessly, and is just plain broken if you have 2 users.

Gonna file it as a bug and go back to using XP.  Someday... (of course been saying that since Breezy)

No, what I said was that removing ubuntu-standard -package *doesn't* break anything. 

"..it's absolutely safe to uninstall the ubuntu-standard -package."

(And both installing or uninstalling ignoring dependencies is pointless, both will only result in broken stuff. Uninstalling would be even worse, as that wouldn't broke the package you are messing with, but instead potentially every other package in your system.. Try installing any program in Windows after removing some stuff from the install package, you'll never get a functional program. Same with Linux, programs need all the code they need to run, remove some part and the rest will break.)

---

### Post by DougZ on 2010-01-25
> **mcduck said:**
> Try installing any program in Windows after removing some stuff from the install package, you'll never get a functional program. Same with Linux, programs need all the code they need to run, remove some part and the rest will break.)

While that is true in **general** are exceptions.  Many programs (in windows) install "bloatware" that the installer absolutely insists is "essential" to the program.  Uninstalling breaks nothing, except perhaps some ads.

From what I understand memtest is another example of this category: It allows you to run a test of your memory at computer startup.  Essential to the proper functioning of Ubuntu? I beg to differ.

Regardless, this thread has sidetracked waaaaaay off course.  Thanks for the replies.  Can someone close this off before it degenerates even further off course?


EDIT: As usual, solved my own problem, with no thanks to the "experts".

dpkg --ignore-depends=memtest86+ -P memtest86+

---

### Post by mattlach on 2010-12-04
> **DougZ said:**
> That worked, as would manually editing the grub entries.

It still does not physically *remove* memtest86++.  Minor irritant anyway.  Was just curious if it can be done.  The answer seems to be no.

Manually editing grub is no longer a solution, as it is automatically regenerated by the "update-grub" script.

It is possible to manually update it, but your changes don't stick.   The memtest entry would come back every single time you update the kernel, or grub, or anything esle related as they all execute the "update-grub" script.

---


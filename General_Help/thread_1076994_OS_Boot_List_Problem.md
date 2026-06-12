---
title: "OS Boot List Problem"
date: 2009-02-21
forum: General Help
---

### Post by MC707 on 2009-02-21
OK so here is the deal. I switched to ubuntu when the release of Intrepid, but I didn't take Linux or Ubuntu too seriously, so I installed it in 1/4 partition of 1 hard drive, with the other partition containing a messed up windows vista installation, full of junk everywhere. So I started using Ubuntu a lot, adding lots of stuff and testing to make sure I wanted a complete switch. Unfortunately, the Ubuntu partition contained only 1/4 of a 465 GB hard drive, so I decided to buy a new 465 GB hard drive to install Ubuntu on and reinstall Vista in the older hard drive. So I backed up information from both OSs, and installed Ubuntu in my new HD, then installed vista in the older HD. The problem is, I did format the old HD, but when I turn my box on and the OS list appears, the old Ubuntu entry appears too. This is the layout, as I can't take snapshots while I am in the OS List:
```
Ubuntu 8.10, kernel 2.6.27-11-generic
Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-7-generic
Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
Ubuntu 8.10, memtest 86+

**Other Operating Systems**
Windows Vista Longhorn (loader)
Ubuntu 8.10, kernel 2.6.27-11-generic
Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-9-generic
Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-7-generic
Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
Ubuntu 8.10, memtest 86+
```

So the upper Ubuntus are my current OS, the lower are my vista install and the old useless ubuntu loaders. When I press one of those, I just see some "couldnt find OS" or something like that. I hope someone can help me delete the lower ones and maybe sometime the Ubuntu community will fix that spammy list :D Thanks in advance :D:D

PS. BTW I use my vista mostly for applications that function **only** in vista (not even with wine under linux) that my College teachers usually ask us to have, or games that only work in windows (ie. GTA San Andreas multi player). Tried Ubuntu and I'm lovin' it! Finally made my switch :D

---

### Post by mcduck on 2009-02-22
press Alt-F2 and run "gksudo gedit /boot/grub/menu.lst". Browse to the end of the file and remove the extra entries related to the old Ubuntu install.

If you need help with which lines to remove then paste the full menu.lst here so we can have a look at it.

What do you mean with "spammy" list? If you made the new Ubuntu install before formatting the old drive, then it's normal behavior that the installer detected the old Ubuntu install and added it into your menu as well. Also having entries for each installed kernel is a designed feature so that's not going to be "fixed" either. Just uninstall the old kernels and their entries will be automatically removed.

(It's also possible to configure Grub to only list certain amount of kernels, but if you do that the actual kernel files are still wasting your disk space while also being completely useless since you can't even boot them any more. So I wouldn't recommend doing that.)

---

### Post by MC707 on 2009-02-22
> **mcduck said:**
> press Alt-F2 and run "gksudo gedit /boot/grub/menu.lst". Browse to the end of the file and remove the extra entries related to the old Ubuntu install.

If you need help with which lines to remove then paste the full menu.lst here so we can have a look at it.

What do you mean with "spammy" list? If you made the new Ubuntu install before formatting the old drive, then it's normal behavior that the installer detected the old Ubuntu install and added it into your menu as well. Also having entries for each installed kernel is a designed feature so that's not going to be "fixed" either. Just uninstall the old kernels and their entries will be automatically removed.

(It's also possible to configure Grub to only list certain amount of kernels, but if you do that the actual kernel files are still wasting your disk space while also being completely useless since you can't even boot them any more. So I wouldn't recommend doing that.)

Thanks dude, it worked.

What do I mean by "spammy"??? I didn't mean spammy because of the old entries, but because of the **new** entries. Have you seen how many entries windows has? do you think a new-user friendly OS has a list like that? I would thank you if you explained me why are old kernels there, too. And *how* to uninstall them, if they are not useful.

Don't get me wrong, neither. I love Ubuntu.:D

---

### Post by mcduck on 2009-02-22
Windows doesn't have entries for many kernels because updating the Windows kernel is harder than in Linux, and only happens very rarely. When it happens, it either works or you won't be able to boot the machine any more. :D

In Linux the kernel is about as easy to update as any other part of the system, so kernel updates can be provided as often as there is need for them. The old kernel isn't removed during the update so you can make sure the new version works correctly for you, and if it doesn't, just select the old one from the boot menu and still have a working computer.

After you are sure the new kernel is working fine on your machine you can then uninstall the old one. Usually people prefer having one older kernel version available in case something goes wrong. Personally, I just run the latest version for a day or two and then uninstall the old one.

Anyway, to uninstall the old kernel versions I suggest using Synaptic Package Manager. Just use the search tool to search for "linux" in "package name". Then find old versions of "linux-image", "linux-headers" and "linux-restricted-modules", select them, right-click and select "mark for complete removal" and finally click "Apply".

edit: Of course it would be nice if there was a way to handle this in a way that doesn't confuse new users, but I also think that being able to update the kernel when needed and still have a working computer if the update doesn't work for some reason is also a great feature. And, of course, most basic users don't usually dual boot their machines so they won't even see the Grub menu at all..

As far as I've understood Ubuntu's developers have been thinking for ways to make uninstalling of old kernel versions easier (or automatic), so we'll probably see that in some future Ubuntu version.

---

### Post by whoop on 2009-02-22
As a rule of thumb I always keep my latest kernel and the last working kernel after that and remove the rest.
Do with this information what you want :p

---

### Post by MC707 on 2009-02-23
> **mcduck said:**
> Windows doesn't have entries for many kernels because updating the Windows kernel is harder than in Linux, and only happens very rarely. When it happens, it either works or you won't be able to boot the machine any more. :D hahahaha :-D=D>

> **mcduck said:**
> In Linux the kernel is about as easy to update as any other part of the system, so kernel updates can be provided as often as there is need for them. The old kernel isn't removed during the update so you can make sure the new version works correctly for you, and if it doesn't, just select the old one from the boot menu and still have a working computer.

After you are sure the new kernel is working fine on your machine you can then uninstall the old one. Usually people prefer having one older kernel version available in case something goes wrong. Personally, I just run the latest version for a day or two and then uninstall the old one.

Anyway, to uninstall the old kernel versions I suggest using Synaptic Package Manager. Just use the search tool to search for "linux" in "package name". Then find old versions of "linux-image", "linux-headers" and "linux-restricted-modules", select them, right-click and select "mark for complete removal" and finally click "Apply".

edit: Of course it would be nice if there was a way to handle this in a way that doesn't confuse new users, but I also think that being able to update the kernel when needed and still have a working computer if the update doesn't work for some reason is also a great feature. And, of course, most basic users don't usually dual boot their machines so they won't even see the Grub menu at all..

As far as I've understood Ubuntu's developers have been thinking for ways to make uninstalling of old kernel versions easier (or automatic), so we'll probably see that in some future Ubuntu version.
Thanks!!! Very useful info!!:mrgreen: Maybe your method of uninstalling kernels should be somewhere accessible to newbs ;)
I assume that method of system restore is more useful and safer than M$' windows restore?

> **whoop said:**
> As a rule of thumb I always keep my latest kernel and the last working kernel after that and remove the rest.
Do with this information what you want :p
Thanks for the info :)

---


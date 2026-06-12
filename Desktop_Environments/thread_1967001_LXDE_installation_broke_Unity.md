---
title: "LXDE installation broke Unity"
date: 2012-04-27
forum: Desktop Environments
---

### Post by parminides on 2012-04-27
I installed Ubuntu 12.04 beta 2 a few days back and upgraded when the official installation came out. Today I wanted to test drive the LXDE desktop, and I installed it by

```

sudo apt-get install lxde-core

```

Subsequently I had several bootup options: Gnome Openbox, Openbox, LXDE, Ubuntu, and Ubuntu 2D. LXDE worked fine. Unfortunately, it broke the default Unity desktop. Unity now has no dash or panel. The screen is nothing but background!

It's not a total loss. Ubuntu 2D works, but it isn't satisfactory. For example, the window placements I set in ccsm don't work.

I tried to uninstall by,

```

sudo apt-get remove lxde-core

```

The messages implied that it removed lxde-core. However, if I boot up, the LXDE option is still there...and it still works! And Unity is still broken.

I tried to remove lxde-core again, and it says package lxde-core isn't installed.

I would like to restore the computer to it's state right before I added LXDE desktop. Maybe I don't know what to search for, but I haven't seen this kind of problem.

---

### Post by Dennis N on 2012-04-27
lxde-core is a meta package, so removing it does not remove the dependencies or recommended packages it brought in. 

Also, I may be wrong, but shouldn't you be installing lubuntu-desktop?

---

### Post by parminides on 2012-04-27
> **Dennis N said:**
> 
Also, I may be wrong, but shouldn't you be installing lubuntu-desktop?

Maybe so. I don't know. I just read somewhere to install lxde-core to run LXDE in Unity. Maybe that's the problem. At this point is there a fix?

---

### Post by Dennis N on 2012-04-27
Here is community documentation on how to install LXDE desktop to a version of Ubuntu:

[https://help.ubuntu.com/community/Lubuntu/Documentation/UpgradeToLubuntu](https://help.ubuntu.com/community/Lubuntu/Documentation/UpgradeToLubuntu)

That indicates you should be installing lubuntu-desktop

Doing that could fix things up and give you the Lubuntu desktop (LXDE) option. That's what I would try, but it's your decision. No guarantees.

---

### Post by parminides on 2012-04-28
I installed lubuntu-desktop and it didn't fix my problem.

For instance, lubuntu-desktop is over 300 MB and includes all the streamlined programs (Abiword + gnumeric instead of LibreOffice, etc.) that Lubuntu uses to speed things up. However, when I removed it with apt-get, it claimed that only 30 something kB were being removed! Moreover, after the alleged removal I can still log in to Lubuntu desktop.

There are other problems with my almost brand-new installation, but I'll spare you the details. I am ready to reinstall from scratch.

By the way, the suggestion to install lxde-core (only 19.7 MB) was from [http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-lxde-core-desktop](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-lxde-core-desktop). "The core files give you the basic LXDE desktop environment."

---

### Post by Dennis N on 2012-04-28
> **parminides said:**
> I installed lubuntu-desktop and it didn't fix my problem.

lubuntu-desktop is over 300 MB and includes all the streamlined programs (Abiword + gnumeric instead of LibreOffice, etc.) that Lubuntu uses to speed things up. However, when I removed it with apt-get, it claimed that only 30 something kB were being removed! Moreover, after the alleged removal I can still log in to Lubuntu desktop.

There are other problems with my almost brand-new installation, but I'll spare you the details. I am ready to reinstall from scratch.

By the way, the suggestion to install lxde-core (only 19.7 MB) was from [http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-lxde-core-desktop](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-lxde-core-desktop). "The core files give you the basic LXDE desktop environment."

Thanks for the link to the article.

So reading that article, I see that lubuntu-desktop gives you the Lubuntu applications as well. Quoting from your link:

> For a complete “Ubuntu” experience using the LXDE desktop consider installing the Lubuntu Desktop. This is the core Ubuntu system configured to use LXDE as its desktop. On the negative side, it also installs many applications that perform the same or similar functions as applications already installed with Ubuntu 12.04.

Sounds like both methods should work (but somehow didn't for you).

lubuntu-desktop is another meta package - basically just a list of things that it will cause to be installed. After all the packages it lists are installed, removing lubuntu-desktop does not remove any of those packages. So thats why Lubuntu still works. the 30k is basically just the size of the list. You would have to use apt-get remove or apt-get purge to remove something. 

If you really want to try Lubuntu with no unneeded Ubuntu packages, go for the Lubuntu Live CD. 

I used that CD to install (but not this newest version), then later added additional Ubuntu packages that I preferred over the Lubuntu defaults.

Good Luck.

---

### Post by parminides on 2012-04-29
This is news to me that an "apt-get remove <package>" doesn't remove everything that was installed with "apt-get install <package>". For future reference, what is the precise command to remove everything (nothing more, nothing less) that was installed with the "apt-get install lubuntu-desktop" command?

---

### Post by tartalo on 2012-04-29
It might help:

[http://askubuntu.com/questions/37451/find-out-what-packages-were-installed-with-a-particular-package](http://askubuntu.com/questions/37451/find-out-what-packages-were-installed-with-a-particular-package)

---

### Post by Dennis N on 2012-04-29
> **parminides said:**
> This is news to me that an "apt-get remove <package>" doesn't remove everything that was installed with "apt-get install <package>". For future reference, what is the precise command to remove everything (nothing more, nothing less) that was installed with the "apt-get install lubuntu-desktop" command?

Again, lubuntu-desktop is a meta package. Please study the following to learn the differences between a package and a meta package:

[http://askubuntu.com/questions/66257/what-is-the-difference-between-a-meta-package-and-a-package](http://askubuntu.com/questions/66257/what-is-the-difference-between-a-meta-package-and-a-package)

Quote from the top answer:

> It is important to note that removing a meta package does NOT remove the packages it installed:

    when a metapackage is automatically removed by the removal or purging of any one, or more, of its underlying dependencies, all of the other packages that were in the metapackage's depends list are still installed on the system.

---

### Post by Complete Concrete Concise on 2012-04-29
> **parminides said:**
> This is news to me that an "apt-get remove <package>" doesn't remove everything that was installed with "apt-get install <package>". For future reference, what is the precise command to remove everything (nothing more, nothing less) that was installed with the "apt-get install lubuntu-desktop" command?
 
I'm sorry that installing LXDE-Core didn't work out for you.
 
When I tested the install, I did it on a fresh upgrade of 11.10 to 12.04 to avoid any potential software / package conflicts.
 
[Sometimes things break in Ubuntu (and, I presume other Linux distros) and fixing them isn't always obvious. I had an 11.10 that was broken in a certain way. I hoped that upgrading to 12.04 would fix it. Nope. Still broken the same way in 12.04 - despite a bazillion packages being replaced / updated. One day, I hope to figure out what is wrong with it.]
 
As for removing completing uninstalling something ... well, this is a problem. You have to know exactly which packages were installed in order to be able to uninstall them.
 
The best way to uninstall everything that was installed is to check the apt-get log and see which packages were installed.
 
I wrote [this tutorial]("http://complete-concrete-concise.com/ubuntu-2/ubuntu-11-10-how-to-completely-remove-a-package/3") for 11.10, but it is the same for 12.04.
 
Since I wrote that tutorial, I have learned the following: if you have installed software or updates after the software you wish to uninstall, there is a chance that you will bugger up those latest changes when you follow the procedure I describe. And here's the reason:
 
(1) assume you installed lxde-core
(2) you then install gsimplecal
 
lxde-core depends on openbox, so it will be installed as part of the lxde-core installation.
 
When you install gsimplecal, it also depends on openbox. However, since openbox is already installed, it doesn't need to install it, it just makes use of the openbox installed by lxde-core.
 
When you choose to uninstall lxde-core using sudo apt-get remove lxde-core, it will leave behind openbox and most everything else it installed.
 
When you use the method I describe, you explicitly uninstall everything that was installed - including openbox.
 
Unfortunately, gsimplecal depends on openbox, consequently gsimplecal will be uninstalled as well.
 
Managing packages and avoiding orphaned packages, bloat, package hell is a serious problem with Linux. I am not sure how to resolve this. Perhaps, someone, somewhere has written a nice app that scans all the packages on your system and resolves all the dependencies and can clean your hard disk of all uninsed packages - but I haven't seen it.

---


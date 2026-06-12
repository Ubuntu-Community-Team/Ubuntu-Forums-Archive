---
title: "reinstall everthing in cache"
date: 2008-12-17
forum: General Help
---

### Post by g0rd99 on 2008-12-17
I experiment a lot. I'm often re-installing Ubuntu.
How do I do a fresh install and retain all my apts?

---

### Post by ibuclaw on 2008-12-17
I use a separate partition for my /home directory.

Then I make a copy of all customisations I make into my home folder.
So whenever I install, I just copy them from, for example, **/home/iain/.backup/sources.list** to **/etc/apt/sources.list**


Also, you may be interested in remastersys.
It acts as a full-system backup utility.
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

So what you can do is set up for computer, then do a full backup onto CD, annihilate it, then restore it by re-installing the backup CD with all your settings on.

Regards
Iain

---

### Post by cdtech on 2008-12-17
```
$ dpkg --get-selections | grep -v deinstall > packagelist
```

The --get-selections flag gives you a list of packages installed and writes them to the file packagelist.

Pipe the output to grep, using the -v flag to select non-matching lines for dpkg's deinstall flag so the packages selected for deinstallation will not be included with your --get-selections call.

Now you have a compact list of installed packages on your current system in a file called "packagelist". Save the file to another device (USB or drive).

To reinstall the Packages just do the following:
Restore the package selection states:
```
$ sudo apt-get update
$ sudo apt-get dist-upgrade
$ sudo dpkg --set-selections < **/dev/sd?/**packagelist
```

Now install it all:
```
$ sudo apt-get -u dselect-upgrade
```

> dselect-upgrade follows the changes made by dselect(8) to the status field of available packages, and performs the actions necessary to realize that state.(for instance, the removal of old and the installation of new
packages).

---

### Post by g0rd99 on 2008-12-18
How do you make a copy of all custimizations? and does a restore restore from the cache? I want to save the time of an internet download.

---

### Post by g0rd99 on 2008-12-18
> **tinivole said:**
> I use a separate partition for my /home directory.

Then I make a copy of all customisations I make into my home folder.
So whenever I install, I just copy them from, for example, **/home/iain/.backup/sources.list** to **/etc/apt/sources.list**


Also, you may be interested in remastersys.
It acts as a full-system backup utility.
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

So what you can do is set up for computer, then do a full backup onto CD, annihilate it, then restore it by re-installing the backup CD with all your settings on.

Regards
Iain

How do you make a copy of all custimizations? and does a restore restore from the cache? I want to save the time of an internet download. Also, many updates have broken other apts, and caused a lot of grief, so I just want to put back all the original apts from the cache. I tried aptoncd, but it downloads a lot of files. I might just re-install everything, and use disk dump to make a complete backup. I have Ubuntu on a small 11G partion

Thanks, Gord

---

### Post by Elfy on 2008-12-18
If I'm reinstalling the same version then I just backup my apt cache and then copy it back once I've reinstalled.

/var/cache/apt

Once everything is back in the cache and sources.list is updated a sudo apt-get update should do the trick.

---


---
title: "Installing OpenOffice on Hardy"
date: 2009-02-21
forum: General Help
---

### Post by iflanery on 2009-02-21
So, I want to install the latest version of OpenOffice.org. Install goes fine until it's time to enter the final command. When entered, I'm told that the package openoffice.org-core conflicts with openoffice.org-unbundled, which is provided when one installs the Debian menu entries for version 3.0.1.

I've got two questions:

1) Is it necessary to remove OpenOffice 2.4 before installing 3.0?

2) Is it even possible to install OpenOffice 3.0 on Hardy Heron?

Thanks in advance.

---

### Post by chmbrs on 2009-02-21
i think you have to remove old one first.

---

### Post by ddarsow on 2009-02-21
> **iflanery said:**
> So, I want to install the latest version of OpenOffice.org. Install goes fine until it's time to enter the final command. When entered, I'm told that the package openoffice.org-core conflicts with openoffice.org-unbundled, which is provided when one installs the Debian menu entries for version 3.0.1.

I've got two questions:

1) Is it necessary to remove OpenOffice 2.4 before installing 3.0?

2) Is it even possible to install OpenOffice 3.0 on Hardy Heron?

Thanks in advance.

1. yes
2. yes

---

### Post by sandyd on 2009-02-21
direct steps... does everything for you....

```

sudo apt-get remove openoffice.org*
sudo dpkg -i *

```
assuming you cd ed to the directory where your debs were

---

### Post by dorkdork777 on 2009-02-21
Alternatively, add these sources. Then the update manager will take care of the rest :)

```
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu hardy main
```

[From this PPA.]("https://launchpad.net/~openoffice-pkgs/+archive/ppa")

---

### Post by sandyd on 2009-02-21
> **dorkdork777 said:**
> Alternatively, add these sources. Then the update manager will take care of the rest :)

```
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu hardy main
```[From this PPA.]("https://launchpad.net/%7Eopenoffice-pkgs/+archive/ppa")

thats actually the best idea. this will make sure you won't get into other conficts in the future when some app needs openoffice.org installed

---

### Post by ErnieDV on 2009-02-22
I'm running KUbuntu 8.04 with KDE 4.1.4.  I followed the above steps to edit the sources, then told Adept to upgrade.  All looked fine and the messages indicated that OpenOffice 3.01 had successfully installed, but it is not located on the Office Menu and the file associations appear to have been lost.  Any ideas on how to fix it?

Ernie

---

### Post by RenderRob on 2009-10-20
> **carlee said:**
> 

                     Originally Posted by **dorkdork777**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=6776466#post6776466")                 
                 [I]Alternatively, add these sources. Then the update manager will take care of the rest :smile:

     Code:
     deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) hardy main 
[From this PPA.]("https://launchpad.net/%7Eopenoffice-pkgs/+archive/ppa")



[/I]
                                 thats actually the best idea. this will make sure you won't get into other conficts in the future when some app needs openoffice.org installed

It might be the best idea, if it actually did that. After adding these sources in the "Software Sources" app, "Update Manager" detects NO changes on my system. I'm using Ubuntu 8.04 from LinuxCNC.org.

---

### Post by Hagar Delest on 2009-10-20
Personally, I prefer the official (Sun) version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

You may have to reset your profile if there have some troubles afterwards: [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

---


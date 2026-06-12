---
title: "gnome-desktop-environment depends on gnome-keyring-manager which doesn't exist"
date: 2008-04-27
forum: Desktop Environments
---

### Post by mor22 on 2008-04-27
Hi,

I've just upgraded to (Kubuntu) hardy and wanted to try gnome.  I can't install it because there is a dependancy issue with gnome-desktop-environment which depends on gnome-keyring-manager and that package isn't available.  gnome-keyring is available and installed.  Is there an error in the package management here?

any help appreciated.

---

### Post by Hendronicus on 2008-05-12
I and many others have the exact same problem. The gnome-keyring-manager version that the gnome-desktop-environment package depends on is older than the current one. I hope they fix this soon because one of the first things I always do with ubuntu is install the full gnome suite.:(

---

### Post by MonkeeSage on 2008-05-12
> **Hendronicus said:**
> I and many others have the exact same problem. The gnome-keyring-manager version that the gnome-desktop-environment package depends on is older than the current one. I hope they fix this soon because one of the first things I always do with ubuntu is install the full gnome suite.:(

It's not that it's older; gnome-keyring-manager isn't in the Hardy tree at all. It has been replaced with a different package (seahorse).[[post=4895598]1[/post]]

---

### Post by Hendronicus on 2008-05-12
It's in universe, but it's broken. They've got it listed as "triaged" in the bug reports as of Apr. 28, 2008. No telling when it will be fixed.

---

### Post by MonkeeSage on 2008-05-14
Hopefully soon. Other than just dependencies worries, it was a general PITA to figure out where it went (I was going from memory, trying to test a specific keyring setup). I was looking for it for like 30 minutes before I hit on the thread I linked to above. Seahorse solved my specific problem, but that still leaves the unresolved dependencies issue.

---

### Post by Hendronicus on 2008-05-14
Yeah, It was quite a surprise to me, as well. I like the way Ubuntu does GNOME, and I don't like the default apps in Ubuntu, so I usually put in the GNOME desktop and let Synaptic uninstall the default one. To each, his own. I'm not saying there's anything wrong with the defaults; I just don't like them. I've done the same thing on every version since 5.04 so it really was a shock when it didn't install.

---

### Post by Awalton on 2008-05-15
From my understanding, this is just a problem with the metapackage. gnome-keyring-manager was removed from the desktop set in favor of seahorse, and apparently the metapackage is still listing gnome-keyring-manager as a necessary package:

$ apt-cache depends gnome-desktop-environment | grep keyring-manager
  Depends: gnome-keyring-manager

You should file a bug on Launchpad against the gnome-desktop-environment metapackage.

---

### Post by Hendronicus on 2008-05-15
Yes and no. It's not that simple. They may have replaced the keyring manager with Seahorse but unless the two are "X messaging" (my term) compatible, then you would still need the keyring manager for some GNOME apps. Obviously, the metapackage is messed-up as well since the gnome-desktop-environment package wants an older version than the current keyring manager. The current one, I believe, is 2.22.2, and the one it wants is 2.22.0. I've checked, and both bugs have already been reported. I'm kind of fussy about GNOME. (It's not my favorite desktop, but Ubuntu usually does it well.) Plus, it's a pretty bad bug. The Ubuntu Devs are going to have to regenerate quite a few of these kinds of packages because of the Debian ssl/ssh debacle anyway, so I'm sure it will be fixed fairly soon.

---

### Post by Awalton on 2008-05-15
> **Hendronicus said:**
> They may have replaced the keyring manager with Seahorse but unless the two are "X messaging" (my term) compatible, then you would still need the keyring manager for some GNOME apps.

Seahorse does everything gnome-keyring-manager does, only better, and it does more on top of that (provides encryption/decryption inside of Nautilus through a plugin, as a limited example). This is the entire reason gnome-keyring-manager was removed from the desktop set. (See meeting rationale: [http://www.mail-archive.com/ubuntu-desktop@lists.ubuntu.com/msg01354.html](http://www.mail-archive.com/ubuntu-desktop@lists.ubuntu.com/msg01354.html))

---

### Post by Hendronicus on 2008-05-15
> **Awalton said:**
> Seahorse does everything gnome-keyring-manager does, only better, and it does more on top of that (provides encryption/decryption inside of Nautilus through a plugin, as a limited example). This is the entire reason gnome-keyring-manager was removed from the desktop set. (See meeting rationale: [http://www.mail-archive.com/ubuntu-desktop@lists.ubuntu.com/msg01354.html](http://www.mail-archive.com/ubuntu-desktop@lists.ubuntu.com/msg01354.html))

Ok, I like that feature. I don't like to leave the file manager, whatever OS or desktop I'm on, for anything, if I can help it.

---

### Post by Hendronicus on 2008-08-14
Well, it's been months and it's not going to get fixed. What bothers me is the fact that so many other packages depend on this. They really dropped the ball on this one. I'm very disappointed. :(

---

### Post by jwiede on 2008-08-20
Yep, rather shoddy planning on their part.  They shouldn't have allowed gnome-keyring-manager to be removed Hardy before having a plan in place to compensate for all the problems caused by doing so.

Telling users "install everything manually one by one if your metapackages are broken" isn't a user-acceptable solution, nor is saying "install ubuntu-desktop instead".  

Most of the larger gnome metapackages depend on gnome-desktop-environment and it in turn depends on gnome-keyring-manager.  By removing gnome-keyring-manager they broke ALL the metapackages which depend on it.  Installing ubuntu-desktop simply does not install all the packages installed by those metapackages.

I think the real answer is that users who care about convenient gnome installs should use distros other than Ubuntu as TPTB have made it quite clear such users aren't important to Ubuntu.

---

### Post by Will Shackleton on 2008-10-05
Someone could create a metapackage that just depends on gnome-keyring and seahorse, and the other necessary packages?

---

### Post by Will Shackleton on 2008-10-05
Or install ubuntu-desktop, i think that is the main package

---


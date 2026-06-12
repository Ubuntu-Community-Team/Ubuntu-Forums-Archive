---
title: "Update manager and Repositories"
date: 2006-01-07
forum: Desktop Environments
---

### Post by nitrolinux on 2006-01-07
Hello guys,

I keep getting these cryptic errors in the update manager when trying to check for updates or going into the preferneces of the update manager:


******************************************
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[in box]

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com)
breezy/universe Packages
(/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages)
- stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com)
breezy/universe Packages
(/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages)
- stat (2 No such file or directory)This program is not currently
installable. It should be available in the "universe" section of the
repository. Enable that section in the Repositories dialog in the
Settings menu to install.....
********************************************
Do any of you guys have any ideal what this is all about? I'm using Ubuntu Breezy 5.10. Using it now to make this post. My Internet is working so I know it's not a connection problem. Any help would be appreciated.

-NitroLinux

---

### Post by schilcha on 2006-01-07
Try the primary ubuntu repositories (not the mirror)... replace "us.archive.ubuntu.com" with "archive.ubuntu.com" in the file /etc/apt/sources.list

---

### Post by Omnios on 2006-01-07
I have noticed similar things with my repsoitorries and it was just that that web section was down at the time. Try again and see if it works

---

### Post by nitrolinux on 2006-01-09
Hello guys,

I just wanted to give thanks for the suggestion of editing my /etc/apt/sources.list to just include: archive.ubuntu.com . Thanks schilcha. Everything is working nice now!

-NitroLinux

---

### Post by Norwal on 2006-01-11
schilcha

> Try the primary ubuntu repositories (not the mirror)... replace "us.archive.ubuntu.com" with "archive.ubuntu.com" in the file /etc/apt/sources.list

Thanks. This fixed the problem for me.:p

---


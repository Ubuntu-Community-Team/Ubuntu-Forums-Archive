---
title: "BIG Problems with ADD APPLICATIONS"
date: 2005-11-24
forum: Desktop Environments
---

### Post by Georgie-o on 2005-11-24
I'm not sure what happended but some how I managed to mess up the ADD APPLICATIONS program on my brand new install.  Can anyone help?  Anyway to reload this application to start fresh?  Without doing a new install?


When I try to do anything an error screen pops up and says:

"The following problems were found on your system:"

"W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)"

THANKS
****

---

### Post by mgmiller on 2005-11-24
I think the us archives are down at the moment.  I could not refresh my repository list for the same reason.  Just gilve it a while and try again or you could edit your repository list and remove the us from the beginning of the url.  This happens every now and again if they are down or swamped by users.

---

### Post by linbetwin on 2005-11-24
Don't reinstall Ubuntu. The problem is not on your computer. There seems to be a problem today with the US mirror. I use the Romanian mirror (because I live in Romania), but many users posted about this problem today. Wait until tomorrow and maybe it will be solved.

---


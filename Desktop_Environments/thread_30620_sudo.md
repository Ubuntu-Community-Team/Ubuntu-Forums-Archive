---
title: "sudo"
date: 2005-04-29
forum: Desktop Environments
---

### Post by oldguy2 on 2005-04-29
I'm a linux newbie and have just installed hoary 5.04 for about the 5th time. I can't do anything as sudo -- it won't accept my password, either user or root. This is in terminal or any of the system apps that require a password. I had the xserver problem on installation that several people seem to have. It selected my on board graphics instead of my Nvidia PCI add on so x wouldn't start. I logged on as root and ran the dpkg to reconfigure the xserver and that worked ok but I'm wondering if that caused the sudo problem. Any help would be appreciated.

---

### Post by Joeb on 2005-04-29
Are you able to "su" in a terminal and enter the root password?  If so, it sounds like you might have messed up the sudoers list that says who can sudo or not.  If that is the case, you could "su" and then recreate it.

---

### Post by oldguy2 on 2005-04-29
Yes I can "su" in terminal and the sudoers list does sound like the problem because I did have an error msg at one time about the list. Thanks, I'll try to check it out this afternoon -- have to run for now.

---

### Post by Joeb on 2005-04-29
[QUOTE=oldguy2]Yes I can "su" in terminal and the sudoers list does sound like the problem because I did have an error msg at one time about the list. Thanks, I'll try to check it out this afternoon -- have to run for now.[/QUOTE]

Some of the various threads on the forums talk about removing the sudoers list after enabling the root password.  The problem is that sudo doesn't work after that.  Instead of deleting the file, it should be edited and only include the users that you trust to use sudo.

Joeb

---


---
title: "OpenOffice Issue"
date: 2009-01-16
forum: General Help
---

### Post by m00blar on 2009-01-16
Hi, I have a little problem with OpenOffice :) First off i upgraded from openoffice 2.3(or 4) to version 3, then it started acting up weird, it crashed every time i opened it. So I uninstalled all that had anything to do with openoffice (apt-get remove openoffice*.* --purge) and added these two repo's (deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main) 

And yay it worked, but now my menu text is bold and it looks like im running it as root, even though im not!

Could anyone help me getting rid of the bold text, I want my old smooth text back ;p 

Here is a screenshot so you can see what im talking about :D

Thanks to all :>

Edit: I'm running kubuntu 8.04
$> uname -r 
2.6.24-23-generic

---

### Post by Hagar Delest on 2009-01-17
You can try to install the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68) It may be a good idea to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) and avoid transferring the personal data during the welcome process, it can wreck the new profile.

---

### Post by m00blar on 2009-01-18
Thank you that worked great!

---


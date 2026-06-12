---
title: "help! can splashy be supported by Kubuntu??"
date: 2005-11-08
forum: Desktop Environments
---

### Post by mjxian on 2005-11-08
how can i keep splashy installed and can run apt-get normally in Kubuntu, please?

when i installed the splashy deb package, apt-get system noticed that i must remove usplashy first, and i tried "dpkg -i --auto-deconfigure splashy_0.1.5.svn4_i386.deb ", at last i cannot run apt-get any more and it says:

root@mjxian ~
# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kubuntu-desktop: Depends: usplash but it is not installed
E: Unmet dependencies. Try using -f.


root@mjxian ~
# apt-get check
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kubuntu-desktop: Depends: usplash but it is not installed
E: Unmet dependencies. Try using -f.

root@mjxian ~
# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  usplash
The following packages will be REMOVED:
  splashy
The following NEW packages will be installed:
  usplash
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/32.8kB of archives.
After unpacking 401kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

---


---
title: "KDE 4.5 Upgrade"
date: 2010-08-13
forum: Desktop Environments
---

### Post by dillzz on 2010-08-13
Has anyone else received this error?  I upgraded to KDE 4.5 and freespacenotifier was removed.  When I try to install after the removal, I receive the following:


sudo aptitude install freespacenotifier 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  kdebase-workspace-bin kdebase-workspace-data 
The following NEW packages will be installed:
  freespacenotifier 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/17.9kB of archives. After unpacking 119kB will be used.
The following packages have unmet dependencies:
  kdebase-workspace-bin: Conflicts: freespacenotifier but 0.0svn1061317-0ubuntu1 is to be installed.
  kdebase-workspace-data: Conflicts: freespacenotifier but 0.0svn1061317-0ubuntu1 is to be installed.
The following actions will resolve these dependencies:

Remove the following packages:
kdebase-workspace
kdebase-workspace-bin
kubuntu-desktop

Downgrade the following packages:
kdebase-workspace-data [4:4.5.0b-0ubuntu1~lucid1~ppa2 (lucid, now) -> 4:4.4.2-0ubuntu14 (lucid)]

Leave the following dependencies unresolved:
plasma-desktop recommends kdebase-workspace
Score is -333

Accept this solution? [Y/n/q/?]

---


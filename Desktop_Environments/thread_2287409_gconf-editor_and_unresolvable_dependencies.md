---
title: "gconf-editor and unresolvable dependencies"
date: 2015-07-19
forum: Desktop Environments
---

### Post by mrcpuhead on 2015-07-19
I'm trying to install gconf-editor on Ubuntu 14.04 LTS (which appears to now be 15.04 due to upgrades).  Here's a snapshot of the results:

joe@joe-Satellite-P755:~$ sudo apt-get install gconf-editor
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gconf-editor : Depends: gconf-defaults-service (>= 2.28) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
joe@joe-Satellite-P755:~$ sudo apt-get install gconf-defaults-service
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gconf-defaults-service : Depends: gconf2-common (= 3.2.6-0ubuntu2) but 3.2.6-3ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.
joe@joe-Satellite-P755:~$ sudo apt-get install gconf2-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gconf2-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joe@joe-Satellite-P755:~$

I tried removing gconf2-common 3.2.6-3ubuntu1 and installing version 3.2.6-0ubuntu2.  That process removed several apps that I wanted and in the process of reinstalling those apps, the gconf2-common got upgraded to the version apparently incompatible with gconf-defaults-service.

Any ideas?

---

### Post by v3.xx on 2015-07-19
Sources list ok?
```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
```

---

### Post by mc4man on 2015-07-19
As mentioned your sources list may be wrong.
You are trying to install gconf-defaults-service from 14.04 but already have gconf2-common either installed or available from 15.04.
gconf-defaults-service  is in universe repo, gconf2-common is in main repo

---

### Post by mrcpuhead on 2015-07-19
v3.xx and mc4man - it appears somehow my sources.list is mismatched with the version of Ubuntu, which is now 15.04. 

The first line in the response says:
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

I updated this first line to match the right data for 15.04, and successfully installed gconf-editor.

Thanks a TON for your help!

---


---
title: "XFCE Active Directory Skel issue"
date: 2016-11-19
forum: Desktop Environments
---

### Post by thevoices on 2016-11-19
Hello, really scratching my head on this one, I have a Xubuntu 16.04 Using SSSD to auth to Active Directory this is works fantastically except it seems to be hickup. My issue is this i am attempting to use pam_oddjob_mkhomedir.so and the oddjob_mkhomedir application to create a home dir using the contents of skel. The odd thing I am able to ssh as user or even sudo it pulls everythiing from Skel. However trying to auth via lightdm it generates the xdg default directories. this is where i have added and the contents; I also tried pam_oddjob_mkhomedir.so.

common-session:session required      pam_mkhomedir.so skel=/etc/skel umask=0022
common-session-noninteractive:session required      pam_mkhomedir.so skel=/etc/skel umask=0022
password-auth-ac:session     required      pam_mkhomedir.so skel=/etc/skel umask=0022
system-auth-ac:session     required      pam_mkhomedir.so skel=/etc/skel umask=0022


no matter what i try, I can not generate debug details on those... closest error I have gotten is when i didnt have oddjob or mkhomedir installed I got an error on logout from common-session stating the so didnt exist.  Thanks in advance



This issue is noted here as well... though no go for me;

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1318778](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1318778)

---

### Post by thevoices on 2016-12-01
No one has any idea?

---


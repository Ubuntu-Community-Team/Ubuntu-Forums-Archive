---
title: "Cannot go past login screen"
date: 2009-10-29
forum: Desktop Environments
---

### Post by vra5107 on 2009-10-29
Hi

    Something's seriously wrong with my kubuntu. The computer boots up and shows the login screen. From there I enter a username and password and then I see a progress bar that hangs up at about 70%. 

    I can log into the console though. From there when I type 

sudo dpkg-reconfigure kdm 

I get

/usr/sbin/dpkg-reconfigure: kdm is broken or not fully configured

sudo apt-get install --reinstall kdm 

throws

dpkg: error processing kdm (--configure):
subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of kubuntu-desktop:
kubuntu-desktop depends on kdm; howerver:
Package kdm is not configured yet.
dpkg: error processing kubuntu-desktop (--configure):
dependency problems - leaving unconfigured


From the above I could understand that there are some dependecy problems between kdm and kubuntu-desktop. But I don't have a clue how to resolve these dependency conflicts.

Thanks in advance
venkat

---


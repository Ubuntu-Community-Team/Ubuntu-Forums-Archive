---
title: "compiz-fusion not working"
date: 2009-03-19
forum: Desktop Environments
---

### Post by sameerkgm on 2009-03-19
i`ve acer aspire desktop pc with ATI radeonxpress200. i installed ubuntu 8.10 .when i try to install compiz fusion ,i face some error message as shown as below

user@ubuntu:~$ sudo apt-get -y upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
user@ubuntu:~$ sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compizconfig-backend-gconf: Conflicts: libcompizconfig-backend-gconf but 0.6.0~git20071003+3v1ubuntu0 is to be installed
E: Broken packages
user@ubuntu:~$ 

pls help me

---

### Post by Scubdup on 2009-03-20
I'm sure someone else with more expertise could offer more comprehensive help, but in the meantime, I might be able to offer some ideas.

[From [the FAQ]("http://ubuntuforums.org/showthread.php?t=809695")] Open System > Preferences > Appearance. Click on the Visual Effects tab. If Compiz and desktop effects are enabled, Normal, Extra, or Custom will be selected. If Compiz is disabled, None will be selected. To switch modes, simply click on another selection.

Any good?

Otherwise have you tried installing them from the repositories?

---


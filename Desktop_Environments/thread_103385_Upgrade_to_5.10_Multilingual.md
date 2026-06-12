---
title: "Upgrade to 5.10 Multilingual"
date: 2005-12-14
forum: Desktop Environments
---

### Post by Ray Fried on 2005-12-14
I am running 5.04 Kubuntu and would like to move to 5.10 and at the same time allow both English and Chinese. I prefer to install from a CD (ISO). The machine is a triple boot setup. 

What steps must I do to not trash the other OS (Win and DOS) on this machine and what must I do to allow multi-language? 

Any comments would be greatly appreciated,
Ray

---

### Post by afhp on 2005-12-14
[QUOTE=Ray Fried]I am running 5.04 Kubuntu and would like to move to 5.10 and at the same time allow both English and Chinese. I prefer to install from a CD (ISO). The machine is a triple boot setup. 

What steps must I do to not trash the other OS (Win and DOS) on this machine and what must I do to allow multi-language? 
Ray[/QUOTE]

Since you have Hoary already installed, the upgrade to Breezy is pretty straightforward :

* edit /etc/apt/sources.list and replace every instance of "hoary" by "breezy"
* you might want to add the following line to get KDE 3.5:
   ```
deb http://kubuntu.org/packages/kde35 breezy main
```
* sudo apt-get update
* sudo apt-get dist-upgrade
(I'd recommend exiting KDE and doing dist-upgrade from a console, but that's not absolutely necessary.)

Regarding chinese support, sudo apt-get install kde-i18n-zhcn

This would all be for an on-line upgrade. Not sure about a CD-based upgrade, but I suspect the following would work (someone correct me if I'm wrong) :
* download the Kubuntu Breezy install CD. Do not boot from it.
* edit /etc/apt/sources.list on your existing Hoary setup and replace the first line (deb cdrom:...) with the appropriate breezy entry (look for sources.list on the CD-ROM, it should be its first line as well)
* sudo apt-get update, sudo apt-get dist-upgrade

Anything you do from within the existing Hoary install (update / dist-upgrade) will only affect your Ubuntu setup and shouldn't touch your Windows partition in any way.

---

### Post by Ray Fried on 2005-12-15
Thanks - sounds pretty straightforward.

Ray

---


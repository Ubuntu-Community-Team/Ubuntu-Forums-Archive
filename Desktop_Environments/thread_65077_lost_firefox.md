---
title: "lost firefox"
date: 2005-09-12
forum: Desktop Environments
---

### Post by kevin_hill54 on 2005-09-12
Hi all

I have recently installed a new 5.04 Ubuntu in place of my Fc3.

I have run a script I found on this forum  to update all the programs and  it worked perfectly.

Since then I have tried to run Synaptics to upgrade Firefox but I get the following message and it does not upgrade.

Now I can't access Firefox at all and have no other option for internet connection.

Can someone please suggest a fix.

This is the error I get.

E: /var/cache/apt/archives/firefox_1.0.6-1ubuntu1~5.04ubp1_i386.deb:
subprocess dpkg-deb --fsys-tarfile returned error exit status 2
E: /var/cache/apt/archives/x-dev_6.8.2-10_all.deb:  cannot access
archive: No such file or directory
E: /var/cache/apt/archives/libxext-dev_6.8.2-10_i386.deb:  cannot access
archive: No such file or directory E:
/var/cache/apt/archives/libxi-dev_6.8.2-10_i386.deb:  cannot access
archive: No such file or directory E:
/var/cache/apt/archives/libxkbfile-dev_6.8.2-10_i386.deb:  cannot access
archive: No such file or directory E:
/var/cache/apt/archives/libx11-dev_6.8.2-10_i386.deb:  cannot access
archive: No such file or directory E:
/var/cache/apt/archives/libice-dev_6.8.2-10_i386.deb:  cannot access
archive: No such file or directory E:
/var/cache/apt/archives/libsm-dev_6.8.2-10_i386.deb:  cannot access
archive: No such file or directory E:
/var/cache/apt/archives/libxt-dev_6.8.2-10_i386.deb:  cannot access
archive: No such file or directory E:
/var/cache/apt/archives/mozilla-firefox-dev_1.0.6-1ubuntu1~5.04ubp1_all.de
b:  cannot access archive: No such file or directory E:
/var/cache/apt/archives/firefox-dev_1.0.6-1ubuntu1~5.04ubp1_i386.deb:
cannot access archive: No such file or directory E:
/var/cache/apt/archives/mozilla-firefox-dom-inspector_1.0.6-1ubuntu1~5.04u
bp1_all.deb:  cannot access archive: No such file or directory E:
/var/cache/apt/archives/firefox-dom-inspector_1.0.6-1ubuntu1~5.04ubp1_i386
.deb:  cannot access archive: No such file or directory E:
/var/cache/apt/archives/firefox-gnome-support_1.0.6-1ubuntu1~5.04ubp1_i386
.deb:  cannot access archive: No such file or directory

Any ideas??

Thanks again for your help.

Kevin

---

### Post by graigsmith on 2005-09-12
it might help if you told us what script you ran.

also,  open up a terminal, and type

firefox 

and then hit enter,  what happens? do you get the same message?

---

### Post by kevin_hill54 on 2005-09-12
The lines I entered were

Open a terminal session and enter:
wget [http://download.ubuntuforums.org/ubuntusetup/ubuntusetup.sh](http://download.ubuntuforums.org/ubuntusetup/ubuntusetup.sh)
sudo sh ubuntusetup.sh

It worked fine but then Firefox was missing. I will try the command line when I get back to the computer.

---

### Post by graigsmith on 2005-09-12
[QUOTE=kevin_hill54]The lines I entered were

Open a terminal session and enter:
wget [http://download.ubuntuforums.org/ubuntusetup/ubuntusetup.sh](http://download.ubuntuforums.org/ubuntusetup/ubuntusetup.sh)
sudo sh ubuntusetup.sh

It worked fine but then Firefox was missing. I will try the command line when I get back to the computer.[/QUOTE]
 it looks like that script tries to install firefox forms.  it may have installed an older version or something that messed up firefox..

If typing firefox in the terminal doesn't start it, then its probably a corrupt firefox.  you will have to reinstall firefox, i would recommend deleting the firefox folder and installing it again.

type this in a terminal, these commands change to the directory where the firefox directory is located, remove the directory. and reinstall it.

cd /usr/lib
sudo rm -r mozilla-firefox
sudo apt-get update
sudo apt-get install mozilla-firefox

then you should have a fresh installation of firefox.

---


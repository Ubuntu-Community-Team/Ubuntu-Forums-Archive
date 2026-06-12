---
title: "can't install KDE"
date: 2010-04-08
forum: Desktop Environments
---

### Post by cold0zero on 2010-04-08
i tried to install KDE on ubuntu 9.10 but i get that 

ubuntu-desktop:
 Depends: kdebase-workspace-bin but it is not going to be installed
 Depends: language-selector-qt but it is not going to be installed
 Depends: plasma-desktop  but it is not installable
 Depends: software-properties-kde but it is not going to be installed
 Recommends: apport-kde but it is not going to be installed
 Recommends: apturl-kde but it is not going to be installed
 Recommends: install-package but it is not going to be installed
 Recommends: jockey-kde but it is not going to be installed
 Recommends: k3b but it is not going to be installed
 Recommends: kdebluetooth but it is not going to be installed
 Recommends: kipi-plugins but it is not going to be installed
 Recommends: kpackagekit but it is not going to be installed
 Recommends: kubuntu-firefox-installer but it is not going to be installed
 Recommends: plasma-widget-facebook but it is not going to be installed
 Recommends: plasma-widget-googlecalendar but it is not going to be installed
 Recommends: plasma-widget-kubuntu-qa-feedback but it is not going to be installed
 Recommends: plasma-widget-networkmanagement but it is not going to be installed
 Recommends: printer-applet but it is not going to be installed
 Recommends: system-config-printer-kde but it is not going to be installed
 Recommends: update-notifier-kde but it is not going to be installed
 Recommends: usb-creator-kde but it is not going to be installed
 Recommends: userconfig but it is not going to be installed

---

### Post by cold0zero on 2010-04-08
cold0zero@ubuntu:~$ sudo apt-get install kdebase-workspace-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdebase-workspace-bin: Depends: kdebase-workspace-data (= 4:4.3.2-0ubuntu7.1) but it is not going to be installed
E: Broken packages
cold0zero@ubuntu:~$ sudo apt-get install kdebase-workspace-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdebase-workspace-data: Depends: python-kde4 (>= 4:4.2.0) but it is not going to be installed
E: Broken packages
cold0zero@ubuntu:~$ sudo apt-get install python-kde4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python-kde4: Depends: python-qt4 (>= 4.3-2ubuntu7.1) but it is not going to be installed
E: Broken packages
cold0zero@ubuntu:~$ sudo apt-get install python-qt4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python-qt4: Depends: python-sip4 (< 4.10) but 4.10.0-0ubuntu1~karmic1~ppa1 is to be installed
E: Broken packages
cold0zero@ubuntu:~$ sudo apt-get install python-sip4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-sip4 is already the newest version.
The following packages were automatically installed and are no longer required:
  pidgin-data linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.

---

### Post by micio on 2010-04-08
try in this way:

```
sudo apt-get install kubuntu-desktop
```

or better

```
sudo aptitude install kubuntu-desktop
```

---

### Post by shaka_zulu on 2010-04-08
How did you try to install it?

---

### Post by cold0zero on 2010-04-09
thanks it's work 

sudo aptitude install kubuntu-desktop

---

### Post by shaka_zulu on 2010-04-09
put [SOLVED] in theme title.

---

### Post by ebrahim-3enab on 2010-04-09
same wrong with me

---

### Post by codemaniac on 2010-04-10
follow as micio has said above it works 100%
or you can install it through synaptic..

---

### Post by zvacet on 2010-04-15
```
sudo tasksel install kubuntu-desktop
```

---


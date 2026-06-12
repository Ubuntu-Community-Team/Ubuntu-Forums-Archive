---
title: "Help with KDE 4.2 Beta 2 and Koffice"
date: 2009-01-06
forum: Desktop Environments
---

### Post by MisterFlibble84 on 2009-01-06
When I got to install koffice with apt, I get this:

```
$ sudo apt-get install koffice
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  koffice: Depends: kformula (>= 1:1.6.3-6ubuntu3) but it is not going to be installed
E: Broken packages

```

So if I try to install kformula, I get:

```
$ sudo apt-get install kformula
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  amarok-mysql-data xscreensaver-gl libnet-daemon-perl libmeanwhile1 mysql-server libjpeg-progs libsmokeqt1 libdbi-perl
  libqt0-ruby1.8 xscreensaver-data xscreensaver-gl-extra akonadi-server xscreensaver-data-extra libgle3 libdbd-mysql-perl netpbm
  libplrpc-perl libnetpbm10 xscreensaver libloudmouth1-0 mysql-server-5.0 libmsn0.1 mysql-client-5.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  koffice-data koffice-libs latex-xft-fonts
Suggested packages:
  wordnet tetex-extra
The following packages will be REMOVED:
  adept akonadi-kde akregator amarok-kde4 ark dolphin dragonplayer gdebi-kde guidance-power-manager gwenview install-package
  jockey-kde kaddressbook kamera kate kde-printer-applet kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma
  kdebase-runtime kdebase-runtime-bin-kde4 kdebase-workspace-bin kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins
  kdelibs-bin kdelibs5 kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs5
  kdeplasma-addons kdesudo kdm kfind kgrubeditor khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror
  konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete korganizer krdc krfb kscreensaver kscreensaver-xsavers
  kscreensaver-xsavers-extra ksnapshot ksysguard ksystemlog ktimetracker ktorrent kubuntu-desktop kubuntu-docs
  kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libkcddb4 libkdecorations4 libkdepim4 libkexiv2-7
  libkholidays4 libkipi6 libkleo4 libkonq5 libkpgp4 libksieve4 libkwineffects1 libmaildir4 libmimelib4 libokularcore1 libplasma3
  okular okular-extra-backends plasmoid-quickaccess python-kde4 software-properties-kde system-config-printer-kde systemsettings
  update-manager-kde update-notifier-kde xorg
The following NEW packages will be installed:
  kformula koffice-data koffice-libs latex-xft-fonts
0 upgraded, 4 newly installed, 96 to remove and 0 not upgraded.
Need to get 1022kB/4574kB of archives.
After this operation, 251MB disk space will be freed.
Do you want to continue [Y/n]?

```

Is this going to be fixed with the RC1? Or is it maybe something I did?

---

### Post by binbash on 2009-01-07
i guess you are trying to install wrong package : 

install this one koffice-kde4

---


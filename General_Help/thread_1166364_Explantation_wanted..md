---
title: "Explantation wanted."
date: 2009-05-21
forum: General Help
---

### Post by jonathonblake on 2009-05-21
All:
OS: Ubuntu 8.20 with a partial upgrade to Ubuntu 9.04.
64 bit version.

I'm trying to update Koffice.
To install KFormula, roughly 200 things will be removed.

Amongst the listed items are:
* Akregator
* Amarok
* Dolphin
* Edubuntu Desktop KDE
* Gdeb KDE
* GTK-QT-Engine
* gtk-qt-engine-kde4
* gwenview
* Ichthux-default-settings
* Ichthus-desktop
* Ichthux-docs
* Install Packages
* kappfinder
* kate
* kcron
* kde-icons-kneu
* kde-printer-applet
* kde-style-qtcurve
* kde-window-manager
* kde-zeroconf
* kdeadmin
* kdebase;
* kdebase-bin
* kdebase-data
* kdebase-plasma
* kdebase-runtime
* kdebase-runtime-bin-kde4
* kdebase-workspace
* kdebase-workspace-bin
* kdebase-workspace-libs4+5
* kdebluetooth
* kdegames
* kdegraphics-strigi-plugins
* kdelibs-bin
* kdelibs5
* kdemultimedia
* kdemultimedia-kio-plugins
* kdenetwork-filesharing
* kdepasswd
* kdepim
* kdepim-kresources
* kepim-strigi-plugins
* kedepim-wizards
* kdepimlib5
* kdeplasma-addons
* kfind
* kfourinline
* kgrubeditor
* khelpcenter
* khelpcenter4
* kmix
* kmousetool
* kmplayer
* kmplayer-base
* kmplayer-konq-plugins
* kmplot
* knetwalk
* knetworkconf
* koulorpaint4
* konq-plugins
* konqueror
* konqueror-nplugins
* konqueror-plugin-adblock
* konqueror-plugin-akregator
* konqueror-plugins-autorefresh
* knoquest
* konsole
* konsolekalendar
* kontact
* kopete
* korganizer
* kpackagekit
* kpat
* kpercentage
* kppp
* krdc
* kreversi
* krfb
* kruler
* kscd
* kscreensaver
* kscreensaver-xsavers
* kshisen
* ksirk
* ksnapshot
* ktimetracker
* ktorrent
* ktouch
* kubuntu-desktop
* kubuntu-konqueror-shortcuts
* kuser
* kwalletmanager
* kwrite
* languge-selector
* okular
* okular-extra-backends
* systemsettings
* python-kde4
* ubuntu-edu-primary
* ubuntu-edu-secondary
* ubuntu-edu-tertiary
* update-manager-kde
* update-notifier-kde

One or two programs being removed, whilst bad, might be understandable.
But the wholesale removal of programs, and metapackages that this requires is utterly unacceptable. 

Especially when the programs being removed include components of the office suite that KFormula is a part of.

Inasmuch as if I compiled everything from source, updating KFormula wouldn't take out everything, is their a sound rational reason why using synaptic takes out so much?

jonathon

---

### Post by Irony on 2009-05-21
Try *aptitude keep-all* to zero everything then run your command.

---

### Post by wirelessmonkey on 2009-05-21
What do you mean by a 'partial upgrade'? What has been upgraded?

---

### Post by albinootje on 2009-05-21
> **jonathonblake said:**
> Ubuntu 8.20 with a partial upgrade to Ubuntu 9.04. 64 bit version.

Unless you're properly using apt-pinning... you should first do a complete upgrade, and only then continue installing.

---

### Post by todak on 2009-05-21
You want to ```
sudo apt-get install koffice-kde4
```and remove koffice.

---

### Post by jonathonblake on 2009-05-21
> **wirelessmonkey said:**
> What do you mean by a 'partial upgrade'? What has been upgraded?

For starters, either KFormula, or everything it uninstalled wasn't upgraded.

Several other programs either uninstalled other programs, as part of the upgrade, or reverted them to an earlier version.  (And the only program I wanted to keep at a specific version got updated to the most recent, so I have to uninstall that one, and reinstall the correct, earlier version.)

jonathon

---


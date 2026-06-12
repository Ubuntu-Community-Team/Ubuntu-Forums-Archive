---
title: "Cannot Shutdown/Logout/Reset through Graphic Interface"
date: 2011-05-09
forum: Desktop Environments
---

### Post by Nathan_U on 2011-05-09
Hello,

Here's the problem - working on KDE, I cannot shutdown, reset, logout or switch users through graphical interface (you know, bit blue button, 'leave' tab and all these buttons).

I've googled the problem, and here's what I have found:
[https://bbs.archlinux.org/viewtopic.php?id=106612&p=2](https://bbs.archlinux.org/viewtopic.php?id=106612&p=2)

Guys on the Arch forum related the problem to the OGG files and phonon-xine - indeed, I cannot play OGG files anymore.

I tried to install phonon-vlc, but the package is not in any of my repositories. I tried to remove libqt4-phonon, but it would also remove half of the system, which isn't the best idea. 

Someone else suggested to install speex, but it's already installed on my Kubuntu.

I'm out of ideas, and I'm not really sure how to reinstall xine and phonon without deleting half of the system like this:

```
The following packages will be REMOVED:
  akregator amarok apport-kde apport-qt apturl-kde ark calibre digikam dolphin dragonplayer gdebi-kde gwenview install-package jockey-kde k3b kaddressbook kaffeine
  kaffeine-gstreamer kamera kate kcm-gtk kde-printer-applet kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4
  kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs5
  kdemultimedia-kio-plugins kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-runtime-libs4 kdepim-strigi-plugins kdepim-wizards kdepimlibs5 kdeplasma-addons
  kdesudo kdm kfind khelpcenter4 kipi-plugins klipper kmag kmail kmix kmousetool knotes konq-plugins konqueror konqueror-nsplugins konqueror-plugin-searchbar konqueror-plugins
  konsole kontact kopete korganizer kpackagekit kppp krdc krfb ksnapshot ksudoku ksysguard ksystemlog ktimetracker ktorrent kubuntu-desktop kubuntu-firefox-installer
  kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager kwin-style-qtcurve language-selector-qt libk3b6 libk3b6-extracodecs libkabcommon4 libkcddb4 libkdcraw7 libkdecorations4
  libkdegames5 libkdepim4 libkexiv2-7 libkipi6 libkleo4 libknotificationitem1 libkonq5 libkonqsidebarplugin4 libkontactinterfaces4 libkopete4 libkorundum4-ruby1.8 libkpgp4
  libksane0 libksieve4 libkwineffects1 liblancelot0 libmarble4 libmimelib4 libokularcore1 libphonon4 libplasma3 libqedje0 libqt4-phonon libqt4-ruby libqt4-ruby1.8 libqt4-webkit
  libqzion0 libsmokekde4-2 libsmokeqt4-2 okular okular-extra-backends openoffice.org-kde phonon phonon-backend-gstreamer phonon-backend-xine plasma-dataengines-addons
  plasma-dataengines-workspace plasma-runners-addons plasma-scriptengine-python plasma-wallpapers-addons plasma-widget-facebook plasma-widget-folderview
  plasma-widget-googlecalendar plasma-widget-indicatordisplay plasma-widget-kimpanel plasma-widget-kubuntu-qa-feedback plasma-widget-lancelot plasma-widget-network-manager
  plasma-widget-networkmanagement plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace printer-applet python-kde4 python-plasma python-qt4 quassel
  software-properties-kde system-config-printer-kde systemsettings update-manager-kde update-notifier-kde usb-creator-kde userconfig webkam xorg
```

Any suggestions?

---

### Post by narf41 on 2011-06-05
i think, it´s called phonon-backend-vlc in kubuntu.

---


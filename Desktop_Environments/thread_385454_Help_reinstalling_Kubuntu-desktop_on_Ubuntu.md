---
title: "Help reinstalling Kubuntu-desktop on Ubuntu"
date: 2007-03-15
forum: Desktop Environments
---

### Post by dg10050 on 2007-03-15
I need some help. A little while back I installed the kubuntu-desktop on Ubuntu so I could use Kubuntu. However, apt-get has been telling me that there are some files that should be removed, like 50 of them. I was a little hesitant, but I let it remove them. I figured that they were just left over from something. I also asked on IRC and they said the same thing. Well this screwed up my Kubuntu install. It worked, but a lot of the main programs were gone. So I tried reinstalling the kubuntu-desktop package, which worked, but now all of my settings are messed up. Now I just want to uninstall kubuntu-desktop completely and reinstall it. However, I can't find how to completely uninstall kubuntu-desktop and KDE. Can anyone help me? From what I can tell, the kubuntu-package was somehow automatically removed and apt-get assumed that these packages were no longer needed because nothing was dependent on them. The following packages were the ones uninstalled by apt-get:
 ```
The following packages were automatically installed and are no longer required:
  kpdf ksystemlog krdc krfb kppp krita-data kubuntu-default-settings
  python2.4-dev adept-manager knode kmplayer-konq-plugins ksvg kio-locate
  libpythonize0 ksnapshot liblockdev1 kdebluetooth openoffice.org-kde
  adept-installer libsmokeqt1 libtdb1 adept-updater libqt4-qt3support
  latex-xft-fonts hwdb-client-kde krita qca-tls libmimelib1c2a
  kubuntu-artwork-usplash libqt4-core adept-batch koffice-data kde-icons-mono
  libqt-perl pykdeextensions adept kubuntu-konqueror-shortcuts procmail skim
  korganizer kdenetwork-kfile-plugins kbstate kio-apt kwin-style-crystal
  python-qt4 libjasper-runtime adept-common libqt4-gui speedcrunch
  libkpimidentities1 libskim0 kpf bogofilter-bdb kdnssd katapult
  kdenetwork-filesharing kubuntu-docs knotes bogofilter kde-guidance
  libqt4-sql debtags libgsl0 apt-index-watcher libkpimexchange1 rdiff-backup
  language-selector-qt qobex ktorrent scim-qtimm kwalletmanager kopete
  python-elementtree karm keep koffice-libs adept-notifier bogofilter-common
  kde-guidance-powermanager kde-systemsettings librsync1 kmousetool
  kitchensync kmag kdepim-kresources kdepim-wizards kmilo kmplayer-base
  python-kde3 qt4-qtconfig
Use 'apt-get autoremove' to remove them.
```

---

### Post by Dr. Nick on 2007-03-15
Try this to get "pure gnome" For the resinstall of KDE use aptitude as menined on the site

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by dg10050 on 2007-03-15
Thanks. I've actually found that not as many setting were messed up as I had thought and I was able to fix most of them by now. That site may still be usefull though.

---


---
title: "Minimal KDE installation"
date: 2010-12-22
forum: Desktop Environments
---

### Post by DirtyJohnson on 2010-12-22
How do I do a minimal install of KDE? This is on a virtual server so I don't need all the bells and whistles. I am just trying to run kcachegrind.

---

### Post by Lone_Joker on 2010-12-23
I think that all you would need would be the kdebase* packages.

I'd try running sudo apt-get install kdebase*

If that does not work you could try
```
 sudo apt-get install kdebase-apps kdebase-bin kdebase-data kdebase-runtime kdebase-runtime-data kdebase-workspace kdebase-workspace-bin kde-workspace-data kdebase-workspace-wallpapers
```

I'm not sure if you need to install both kdebase-workspace and kdebase-workspace-bin (I don't think so). Other than that, I'm pretty sure that those are the packages you'd need. I would wait for somebody else to confirm this though.

Oh, by the way, you could install the server version of ubuntu to have a barebones installation then run those commands. Or you might decide on using a different Linux distro, one that is more minimal.

---

### Post by cascade9 on 2010-12-23
> **DirtyJohnson said:**
> How do I do a minimal install of KDE? This is on a virtual server so I don't need all the bells and whistles. I am just trying to run kcachegrind.

If you're just trying to install kcachegrind, why dont you just 'apt-get install' it? 

This is what it should install- 

[http://packages.ubuntu.com/maverick/kcachegrind](http://packages.ubuntu.com/maverick/kcachegrind)

@ Lone_Joker- that will install a lot more than just the dependancies for  kcachegrind.

---

### Post by DirtyJohnson on 2010-12-23
Thanks I will look into the kdebase packages.
 
I did install kcachegrind but this is on a server install so I don't have a graphical env. yet to use it. That is why I am trying to install the barebones kde.

---

### Post by DirtyJohnson on 2010-12-23
Can you update your 10.10 KDE guide? I tried it but there are no core or base packages. I am looking for a minimal install guide. Can I do a Kubuntu then go backwards?

---

### Post by cascade9 on 2010-12-24
Minimal KDE doesnt really exist in the newer *buntus. :(

---

### Post by weekend warrior on 2010-12-24
kde-plasma-desktop is the package for a minimal desktop setup

---

### Post by inobe on 2010-12-24
> **cascade9 said:**
> Minimal KDE doesnt really exist in the newer *buntus. :(

it may be libkdecore, it's supposedly bare minimum and the packages includes kdebase, kdelibs, arts, fontconfig.


that's by memory, confirmation needed !

edit; scratch that, seems that things have changed

---

### Post by aysiu on 2010-12-24
> **DirtyJohnson said:**
> Can you update your 10.10 KDE guide? I tried it but there are no core or base packages. I am looking for a minimal install guide. Can I do a Kubuntu then go backwards?
I don't have any plans to maintain that particular guide, but the package you're looking for is *kde-plasma-desktop*.

If you're using Kubuntu 10.10 (Maverick Meerkat), you can get to it by pasting this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get remove akregator amarok amarok-common amarok-utils apport apport-kde apturl-kde ark bluedevil bluez brltty cdparanoia cdrdao dragonplayer dvd+rw-tools gdebi-core gdebi-kde genisoimage gnupg-agent gnupg2 gtk2-engines-qtcurve gwenview hal hal-info ibus-qt4 jockey-common jockey-kde k3b k3b-data kaddressbook kamera kate kcalc kde-config-gtk kde-config-touchpad kde-zeroconf kdegraphics-libs-data kdegraphics-strigi-plugins kdelibs5 kdemultimedia-kio-plugins kdepim-groupware kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdesudo kdm khelpcenter4 kinfocenter kmag kmail kmix kmousetool knm-runtime knotes kontact kopete kopete-message-indicator korganizer kpackagekit kppp krdc krfb krosspython ksnapshot ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kubuntu-netbook-default-settings kubuntu-notification-helper kvkbd kwalletmanager language-selector-qt libakonadi-contact4 libbluedevil1 libdebconf-kde0 libepub0 libflac++6 libgpgme++2 libhal-storage1 libibus-qt1 libindicate-qt0 libk3b6 libkblog4 libkcddb4 libkdcraw8 libkdepim4 libkexiv2-8 libkimproxy4 libkipi7 libkleo4 libknewstuff2-4 libkontactinterface4 libkopete4 libkpgp4 libkpimidentities4 libkpimtextedit4 libksba8 libksieve4 libktnef4 libktorrent-l10n libktorrent2 libkxmlrpcclient4 liblastfm0 libloudmouth1-0 libmessagecore4 libmessagelist4 libmimelib4 libmsn0.3 libokularcore1 libotr2 libpackagekit-glib2-14 libpackagekit-qt-14 libpoppler-qt4-3 libqapt-runtime libqapt1 libqca2-plugin-ossl libqgpgme1 libqjson0 libqt4-help libqt4-sql-sqlite libqt4-test libtag-extras1 libtelepathy-qt4-0 libzip1 network-manager-pptp network-manager-pptp-kde okular okular-extra-backends openoffice.org-kde openoffice.org-style-oxygen oxygen-icon-theme-complete packagekit packagekit-backend-aptcc pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-netbook plasma-scriptengine-python plasma-widget-facebook plasma-widget-kimpanel plasma-widget-kimpanel-backend-ibus plasma-widget-kubuntu-feedback plasma-widget-menubar plasma-widget-message-indicator plasma-widget-networkmanagement plasma-widget-quickaccess plasma-widgets-addons plymouth-theme-kubuntu-logo plymouth-theme-kubuntu-text polkit-kde-1 printer-applet python-apport python-kde4 python-packagekit python-qt4 python-qt4-dbus python-sip qapt-batch quassel quassel-data rdesktop rekonq samba-common samba-common-bin smartdimmer smbclient software-properties-kde system-config-printer-kde update-manager-kde usb-creator-common usb-creator-kde userconfig wodim && sudo apt-get install kde-plasma-desktop --no-install-recommends
```

---

### Post by DirtyJohnson on 2010-12-24
Thanks aysiu,
Is that command to remove everything as if I had kubuntu installed then add the plasma? Also, I noticed that in 10.04 lts there is still the kde-minimal packages. Would I have been better off using that version or just stick with your recommendation above. It doesn't really matter since this isn't a production setup, just a local virtual server on my laptop. I don't have lots of hd space and am trying to keep the performance up, hence install as little as possible.

---

### Post by aysiu on 2010-12-24
> **DirtyJohnson said:**
> Thanks aysiu,
Is that command to remove everything as if I had kubuntu installed then add the plasma? Also, I noticed that in 10.04 lts there is still the kde-minimal packages. Would I have been better off using that version or just stick with your recommendation above. It doesn't really matter since this isn't a production setup, just a local virtual server on my laptop. I don't have lots of hd space and am trying to keep the performance up, hence install as little as possible.
The command above assumes you already have *kubuntu-desktop* installed and then it strips away all the added Kubuntu stuff and keeps only the basic minimal KDE.

I saw a bunch of kde-minimal packages but they didn't really seem to be metapackages for a KDE desktop experience--more like just a handful of components.

If you don't already have Kubuntu installed, just install *kde-plasma-desktop*

---

### Post by cascade9 on 2010-12-24
Before everybody goes all crazy about KDE4.X and plasma- 

> ** Requirements**

 
[LIST]
[*]Callgrind: Valgrind (i.e. Linux on X86)
[*]KCachegrind:
[LIST]
[*]Libraries for KDE 3.[01234].x. Note that KDE is not bound to Linux, but runs on most Unixes, on Windows (KDE on CygWin), and even MacOS X (Fink project)
[*]Commands 'dot' (GraphViz) for call graph, and 'objdump' (BinUtils) for assembler view (these are runtime requirements, not needed for compilation)
[/LIST]
 
[/LIST]


[http://kcachegrind.sourceforge.net/html/Home.html](http://kcachegrind.sourceforge.net/html/Home.html)

Its a KDE3.X app.

---

### Post by DirtyJohnson on 2010-12-24
Is KDE4.x not backwarks compatible? I already installed kcahcegrind. Would those lib be different in KDE4 that it would break it? I guess it will be an experiment!

---

### Post by DirtyJohnson on 2010-12-25
Ok well I installed the kde-plasma-desktop and it works so far. The kcachegrind I had already installed was in the development tools and worked as well. It only added 124mb to install so that was good. 
 
Thanks for the help

---

### Post by aliancemd on 2012-05-27
Another way is to download a minimal install: [URL="https://help.ubuntu.com/community/Installation/MinimalCD"]https://help.ubuntu.com/community/Installation/MinimalCD
[/URL] 
When you are asked for packages to get installed you select none and just press enter. There might be a problem, you need internet for it and if you need to connect for that to a wireless network you might need some skills to do that too. An Ethernet connection will work great.

After the minimal system is installed, when the system booted, you just type ```
sudo apt-get install kde-plasma-desktop
``` without --no-install-recommendations
because you might have an unusable system.

And if you want a low-memory system you can also install after that ```
sudo apt-get install kubuntu-low-fat-settings
```.

---


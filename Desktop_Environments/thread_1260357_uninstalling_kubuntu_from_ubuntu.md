---
title: "uninstalling kubuntu from ubuntu"
date: 2009-09-07
forum: Desktop Environments
---

### Post by oospill on 2009-09-07
I installed the kubuntu desktop on top of my ubuntu system just to check it out.  not much of a fan of kde, I'd like to uninstall it, even just to see the ubuntu bootup and shutdown splash screens.  anyone know how to go about this?

thanks, oospill

---

### Post by Brandon Williams on 2009-09-07
Provided that you still have ubuntu-desktop installed, then you should be able to simply remove kubuntu-desktop. That will work as long as all of the kde specific stuff is still marked for automatic removal when everything that depends on it has been removed. If that's not the case, you might have to mark all of the kde stuff for removal manually, which might be a bit of a pain.

As for the bootup splash and login screens, if it doesn't automatically revert to using the ubuntu splash screen and gdm, you may need to reconfigure gdm and/or usplash-theme-ubuntu.

The commands in question are:

```
sudo aptitude remove kubuntu-desktop
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure usplash-theme-ubuntu
```

You may want to try the two dpkg-reconfigure calls first, before removing kubuntu-desktop, just to make sure that they do the trick for you before removing kubuntu-desktop, rust to be certain that you don't end up with a system that you can't log in to.

---

### Post by oospill on 2009-09-09
FYI:  I tried the above methods, and my splash screen is still blue instead of orange.. and I still have to uninstall all of the KDE apps myself.  Luckily I'm due for a reinstall!!

oospill

---

### Post by Cortux on 2009-09-09
Here you go. 
 
Note that this applies to Jaunty only. Also when I used this it removed skype and google earth apps but not the installation (data) files so I just reinstalled it via synaptic and no large downloads were required again.
 
Paste in Terminal:
 
sudo apt-get remove akregator amarok amarok-common apport-qt ark cdrdao dolphin dontzap dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ijsgutenprint install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdesudo kdm kfind khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete korganizer kpackagekit krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libao2 libaudio2 libavahi-qt3-1 libboost-program-options1.35.0 libclucene0ldbl libdbus-qt-1-1c2 libeet1 libexiv2-5 libflac++6 libgeoip1 libk3b3 libk3b3-extracodecs libkcddb4 libkdecorations4 libkdepim4 libkexiv2-7 libkholidays4 libkipi6 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 libloudmouth1-0 liblua50 liblualib50 libmad0 libmimelib4 libmodplug0c2 libmpcdec3 libmsn0.1 libmysqlclient15off libokularcore1 libpackagekit-glib11 libpackagekit-qt11 libphonon4 libplasma3 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl libqedje0 libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqzion0 libraptor1 librasqal1 librdf0 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-common okular okular-extra-backends openoffice.org-kde openoffice.org-style-crystal oxygen-cursor-theme packagekit packagekit-backend-apt phonon phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-widget-network-manager plasma-widget-quickaccess python-dev python-kde4 python-packagekit python-plasma python-qt4 python-qt4-common python-qt4-dbus python-sip4 python2.6-dev qt4-qtconfig quassel quassel-data raptor-utils redland-utils software-properties-kde soprano-daemon speedcrunch strigi-client strigi-daemon system-config-printer-kde systemsettings ttf-dejavu ttf-dejavu-extra update-manager-kde update-notifier-kde && sudo apt-get install ubuntu-desktop

---

### Post by oospill on 2009-09-09
that's the scariest post I've seen yet.  I'm gonna try it.

peace!!

---

### Post by oospill on 2009-09-09
hmph.  now I've got BOTH splash screens!!  hah.  please tell me you didn't type all of that out, and then please tell me where you got that list!!

the only thing I noticed missing what gnomebaker, which I prefer.

rock on.

---

### Post by Cortux on 2009-09-09
> **oospill said:**
> hmph. now I've got BOTH splash screens!! hah. please tell me you didn't type all of that out, and then please tell me where you got that list!!
 
the only thing I noticed missing what gnomebaker, which I prefer.
 
rock on.
 
 
 
Dude, 
If I were to type that out, you probably wouldnt have a PC left :lolflag:
And I would never do that to a fellow Linux linux user.
 
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
 
I did use it myself and was all good on my side. Maybe depends on the config.

---

### Post by Brandon Williams on 2009-09-09
> **oospill said:**
> FYI:  I tried the above methods, and my splash screen is still blue instead of orange.. and I still have to uninstall all of the KDE apps myself.  Luckily I'm due for a reinstall!!

oospill

I don't have any alternatives for either the usplash or the display manager installed, so I thought that dpkg-reconfigure would do the right things. Look like I was wrong ... sorry about that.

Do this instead:
```
sudo update-usplash-theme ubuntu
echo /usr/sbin/gdm | sudo tee /etc/X11/default-display-manager
```

This will have you switched over to the orange usplash theme and gdm, after which you can remove all of the kde stuff without risking your ability to boot and login to the system.

---

### Post by dru3692 on 2009-09-10
I installed KDE on top of Gnome. Went into KDE, started changing display settings, now all I can see is solid black or solid white. Kubuntu is still functioning properly, I just can't see much of it. I can make out vague window borders but that is about it. 

Looking to reset KDE to default display values or uninstall and reinstall KDE. I have tried several suggestions but always get some erroneous error or another. Advice?

---


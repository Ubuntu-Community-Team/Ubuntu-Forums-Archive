---
title: "I need to remove KDE"
date: 2010-09-21
forum: Desktop Environments
---

### Post by THM2 on 2010-09-21
I need to remove KDE

:confused::confused::confused::confused::confused::confused::confused::confused:

And I Dont Know How

---

### Post by Elfy on 2010-09-21
You'll need to give people a bit more fo an idea what it is you want to achieve here.

You want to remove kde and leave nothing on the hdd?

You want to remove kde and had something else before?

---

### Post by sikander3786 on 2010-09-21
Ubuntu Lucid is mentioned in your details in the left column so I assume that you have installed KDE on Ubuntu Lucid. So to uninstall it, here is the command.

```

sudo apt-get remove akonadi-server akregator amarok amarok-common amarok-utils apport-kde apturl-kde ark cdrdao dolphin dragonplayer exiv2 foomatic-db-gutenprint freespacenotifier gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ibus-qt4 icoutils ijsgutenprint install-package jockey-kde k3b k3b-data kaddressbook kamera kate kbluetooth kcalc kcm-gtk kcm-touchpad kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-data kdebase-workspace kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdesudo kdm kfind khelpcenter4 klipper kmag kmail kmix kmousetool knm-runtime knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete kopete-message-indicator korganizer kpackagekit kppp krdc krfb krosspython ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-debug-installer kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kubuntu-notification-helper kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libao2 libattica0 libaudio2 libboost-program-options1.40.0 libclucene0ldbl libdbusmenu-qt2 libepub0 libexiv2-6 libflac++6 libibus-qt1 libindicate-qt0 libiodbc2 libk3b6 libkcddb4 libkdcraw8 libkdecorations4 libkdepim4 libkephal4 libkexiv2-8 libkfontinst4 libkipi7 libkleo4 libkonq5 libkonq5-templates libkonqsidebarplugin4 libkopete4 libkpgp4 libkscreensaver5 libksgrd4 libksieve4 libksignalplotter4 libkwineffects1 libkworkspace4 liblastfm0 libmimelib4 libmng1 libmodplug0c2 libmpcdec3 libmsn0.3 libmysqlclient16 libokularcore1 libotr2 libpackagekit-glib2-12 libpackagekit-qt-12 libphonon4 libplasma-applet-system-monitor4 libplasma-geolocation-interface4 libplasma3 libplasmaclock4 libplasmagenericshell4 libpolkit-qt-1-0 libpoppler-qt4-3 libprocesscore4 libprocessui4 libqca2 libqca2-plugin-ossl libqimageblitz4 libqt4-assistant libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libsolidcontrol4 libsolidcontrolifaces4 libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libtag-extras1 libtaskmanager4 libvncserver0 libweather-ion4 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-client-core-5.1 mysql-common mysql-server-core-5.1 network-manager-kde okular okular-extra-backends openoffice.org-kde openoffice.org-style-oxygen oxygen-cursor-theme oxygen-icon-theme oxygen-icon-theme-complete packagekit packagekit-backend-apt phonon phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop plasma-scriptengine-javascript plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-kimpanel plasma-widget-kimpanel-backend-ibus plasma-widget-kubuntu-feedback plasma-widget-message-indicator plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace plymouth-theme-kubuntu-logo polkit-kde-1 printer-applet python-kde4 python-packagekit python-qt4 python-qt4-dbus python-sip quassel quassel-data shared-desktop-ontologies software-properties-kde soprano-daemon system-config-printer-kde systemsettings ttf-dejavu ttf-dejavu-extra update-manager-kde usb-creator-kde userconfig virtuoso-nepomuk
```

---

### Post by 3Miro on 2010-09-21
If you actually installed Kubuntu and you remove KDE you will be left with a bare system. Make sure you have either Ubuntu-desktop, Xubuntu-desktop or Lubuntu-desktop (I think that is the name) installed first.

---

### Post by Elfy on 2010-09-21
If you in fact did have another desktop installed and then installed kubuntu following post #3 will remove all kde apps. 

> It's possible that the commands might remove some other packages you have since added to the default and want to keep. If that's the case, keep track of which packages those are and reinstall them. 

---

### Post by THM2 on 2010-09-21
Didn't Uninstall  :(

---

### Post by LinuxPhreak on 2010-09-23
> **THM2 said:**
> Didn't Uninstall  :(

Please try to give more info. 

Did you download the KUbuntu ISO image then burned it to disk and installed it onto your computer? 

Try to press ctrl + alt + F1 then you will get command command line asking for you to log in. Log in the type the following. 

```
sudo apt-get remove --purge kubuntu-desktop
```

Next type the following. 

```
sudo reboot
```

The above will remove all Desktop Envirnments leaving you with cammand line system. 

Did you install Ubuntu then added kubuntu-desktop?

Make sure you log out of KUbuntu and choose to log into GNOME. Then open up the terminal and type the following.

```
sudo apt-get remove --purge kubuntu-desktop
```

Did you install just the bare minimum of KDE?

```
sudo apt-get remove --purge kde-minimal
```

Did you install the Alternate CD as CLI and installed bare minimum IDE's?

```
sudo apt-get remove --purge kde-minimal
```

Are you trying to remove KDE from inside of KDE such as GUI Package Manager? 

If so this could cause some complications. Try using a terminal to remove it or another desktop environment.

---

### Post by Onael on 2010-11-15
> **LinuxPhreak said:**
> Please try to give more info. 

Did you download the KUbuntu ISO image then burned it to disk and installed it onto your computer? 

Try to press ctrl + alt + F1 then you will get command command line asking for you to log in. Log in the type the following. 

```
sudo apt-get remove --purge kubuntu-desktop
```

Next type the following. 

```
sudo reboot
```

The above will remove all Desktop Envirnments leaving you with cammand line system. 

Did you install Ubuntu then added kubuntu-desktop?

Make sure you log out of KUbuntu and choose to log into GNOME. Then open up the terminal and type the following.

```
sudo apt-get remove --purge kubuntu-desktop
```

Did you install just the bare minimum of KDE?

```
sudo apt-get remove --purge kde-minimal
```

Did you install the Alternate CD as CLI and installed bare minimum IDE's?

```
sudo apt-get remove --purge kde-minimal
```

Are you trying to remove KDE from inside of KDE such as GUI Package Manager? 

If so this could cause some complications. Try using a terminal to remove it or another desktop environment.

So was he successful?

I'm in the same boat, I think. I installed Ubuntu10.10 and tried KDE desktop environment. I'm not liking it and would like to revert back to Gnome.

Thanks.

Onael

---

### Post by Verbeck on 2010-11-15
> **Onael said:**
> So was he successful?

I'm in the same boat, I think. I installed Ubuntu10.10 and tried KDE desktop environment. I'm not liking it and would like to revert back to Gnome.

Thanks.

Onaeltry [http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

---

### Post by Onael on 2010-11-15
Thank you. Do I have to be in Gnome or can I just run that from KDE?

---

### Post by Verbeck on 2010-11-15
from kde i think, as all kde stuff is removed

---

### Post by Onael on 2010-11-15
Okay. Thank you. That is a very long command, btw lol

---

### Post by Onael on 2010-11-15
Well that long command didn't do anything for me. This is what I got. But I did manage to get back to my gnome environment using the 'purge' command above.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kmail is not installed, so not removed
Package kopete is not installed, so not removed
Package kopete-message-indicator is not installed, so not removed
Package libkopete4 is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libaccess-bridge-java : Depends: default-jre but it is not going to be installed or
                                  openjdk-6-jre but it is not going to be installed or
                                  sun-java6-jre but it is not installable
E: Broken packages
akinci1g@akinci1g:~$
```
Thank you.

Onael

---

### Post by sikander3786 on 2010-11-15
> **Onael said:**
> Well that long command didn't do anything for me. This is what I got. But I did manage to get back to my gnome environment using the 'purge' command above.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kmail is not installed, so not removed
Package kopete is not installed, so not removed
Package kopete-message-indicator is not installed, so not removed
Package libkopete4 is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libaccess-bridge-java : Depends: default-jre but it is not going to be installed or
                                  openjdk-6-jre but it is not going to be installed or
                                  sun-java6-jre but it is not installable
E: Broken packages
akinci1g@akinci1g:~$
```
Thank you.

Onael
You need to fix the broken packages first.

Go to Software Center > Edit > Software Sources > Other Software Tab and make sure the Canonical Partners Repositories are enabled. (2 of them)

Now from terminal,

```
sudo apt-get update
```

```
sudo apt-get install -f
```

And then try to remove the KDE stuff by the same previously used command.

---

### Post by koolcracker on 2010-11-25
I found that the package 'libgif4' was the one causing problems, so I removed that from the long command and everything seemed to uninstall just fine.

The new command turned out to be:
```
sudo apt-get remove akonadi-server akregator amarok amarok-common amarok-utils apport-kde apturl-kde ark bluedevil cdparanoia cdrdao docbook-xsl docbook-xsl-doc-html dolphin dragonplayer gdebi-core gdebi-kde gnupg-agent gnupg2 gtk2-engines-qtcurve gwenview hal hal-info ibus-qt4 icoutils jockey-kde k3b k3b-data kaddressbook kamera kate kcalc kde-config-gtk kde-config-touchpad kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-runtime kdebase-runtime-data kdebase-workspace kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdegraphics-libs-data kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdelibs5-data kdelibs5-plugins kdemultimedia-kio-plugins kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-strigi-plugins kdepim-wizards kdepimlibs-kio-plugins kdesudo kdm kdoctools kfind khelpcenter4 kinfocenter klipper kmag kmail kmix kmousetool knm-runtime knotes konsole kontact kopete kopete-message-indicator korganizer kpackagekit kppp krdc krfb krosspython ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-debug-installer kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kubuntu-netbook-default-settings kubuntu-notification-helper kvkbd kwalletmanager language-selector-qt libakonadi-contact4 libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4 libakonadiprivate1 libao-common libao4 libattica0 libaudio2 libbluedevil1 libboost-program-options1.42.0 libcln6 libclucene0ldbl libdbusmenu-qt2 libdebconf-kde0 libdirectfb-1.2-9 libepub0 libflac++6 libgpgme++2 libgps19 libhal-storage1 libhal1 libibus-qt1 libilmbase6 libindicate-qt0 libiodbc2 libk3b6 libkabc4 libkatepartinterfaces4 libkblog4 libkcal4 libkcddb4 libkdcraw8 libkde3support4 libkdecorations4 libkdecore5 libkdepim4 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkephal4 libkexiv2-8 libkfile4 libkholidays4 libkhtml5 libkimap4 libkimproxy4 libkio5 libkipi7 libkjsapi4 libkjsembed4 libkldap4 libkleo4 libkmediaplayer4 libkmime4 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkonq5 libkonq5-templates libkontactinterface4 libkopete4 libkparts4 libkpgp4 libkpimidentities4 libkpimtextedit4 libkpimutils4 libkpty4 libkresources4 libkrosscore4 libkrossui4 libksba8 libkscreensaver5 libksgrd4 libksieve4 libksignalplotter4 libktexteditor4 libktnef4 libktorrent-l10n libktorrent2 libkunitconversion4 libkutils4 libkwineffects1a libkworkspace4 libkxmlrpcclient4 liblastfm0 libloudmouth1-0 libmailtransport4 libmessagecore4 libmessagelist4 libmicroblog4 libmimelib4 libmng1 libmodplug1 libmpcdec6 libmsn0.3 libmysqlclient16 libnepomuk4 libnepomukquery4a libokularcore1 libopenexr6 libotr2 libpackagekit-glib2-14 libpackagekit-qt-14 libphonon4 libplasma-geolocation-interface4 libplasma3 libplasmaclock4b libplasmagenericshell4 libpolkit-qt-1-0 libpoppler-qt4-3 libprocesscore4a libprocessui4a libqalculate5 libqapt-runtime libqapt1 libqca2 libqca2-plugin-ossl libqgpgme1 libqimageblitz4 libqjson0 libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libqtwebkit4 libreadline5 libsolid4 libsolidcontrol4a libsolidcontrolifaces4 libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libsyndication4 libtag-extras1 libtaskmanager4a libtelepathy-qt4-0 libthreadweaver4 libts-0.0-0 libvirtodbc0 libvncserver0 libweather-ion4a libxcb-shape0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-client-core-5.1 mysql-common mysql-server-core-5.1 network-manager-pptp-kde odbcinst odbcinst1debian2 okular okular-extra-backends openoffice.org-kde openoffice.org-style-oxygen oxygen-cursor-theme oxygen-icon-theme oxygen-icon-theme-complete packagekit packagekit-backend-aptcc phonon phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop plasma-netbook plasma-scriptengine-javascript plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-kimpanel plasma-widget-kimpanel-backend-ibus plasma-widget-kubuntu-feedback plasma-widget-menubar plasma-widget-message-indicator plasma-widget-networkmanagement plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace plymouth-theme-kubuntu-logo plymouth-theme-kubuntu-text polkit-kde-1 printer-applet python-kde4 python-packagekit python-qt4 python-qt4-dbus python-sip qapt-batch quassel quassel-data rekonq shared-desktop-ontologies smartdimmer software-properties-kde soprano-daemon system-config-printer-kde systemsettings tsconf ttf-dejavu ttf-dejavu-extra update-manager-kde usb-creator-kde userconfig virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common && sudo apt-get install ubuntu-desktop
```

---

### Post by AHoneybun on 2011-03-22
I used the command to install kubuntu-desktop but it just shows "KDE" at the login, but I install xubuntu-desktop and it install both xubuntu and xfce. And I wish to remove all of it.

---

### Post by TheWSD on 2011-04-08
I'm a noob to this and have learnt the hard way that I should have backed up my X Config file but didn't.  I installed Ubuntu 11.04, then installed KDE 4.6 using the command line, I was trying to set up my 2nd display using the nvidia settings, selected "twin view" and xinemera, rebooted and now when I boot into KDE there is just a blank desktop image, if I were to do as the below, would this remove my KDE only leaving ubuntu, where I could  then reinstall KDE? After the mess that I caused last time, I would like some advice before  proceeding, thanks in advance.

   > **LinuxPhreak said:**
> 

Try to press ctrl + alt + F1 then you will get command command line asking for you to log in. Log in the type the following. 

```
sudo apt-get remove --purge kubuntu-desktop
```Next type the following. 

```
sudo reboot
```The above will remove all Desktop Envirnments leaving you with cammand line system. 

Did you install Ubuntu then added kubuntu-desktop?



Edit:

I have since used the nvidia settings in ubuntu to disable both twin view and xinemera but it hasn't fixed the problem, looks like I broke KDE?

Tried and it was 3rd time lucky, can boot into kubuntu and it works :)

---

### Post by s41ted on 2011-06-19
> **koolcracker said:**
> I found that the package 'libgif4' was the one causing problems, so I removed that from the long command and everything seemed to uninstall just fine.

Sorry to dig up an old thread, but how the hell did you work out that it was the libgif4 package?

---

### Post by tobcro on 2011-12-02
> **s41ted said:**
> Sorry to dig up an old thread, but how the hell did you work out that it was the libgif4 package?

Haha, I second that :)

Just wanted to say thank you, got the same error when I tried to remove Ubuntu (and keep Xubuntu) in 11.10 following the instructions here: [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

After removing libgif4 from the packages list the uninstall now works.

---


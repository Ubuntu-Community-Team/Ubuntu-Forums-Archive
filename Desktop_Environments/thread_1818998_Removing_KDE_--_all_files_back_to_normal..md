---
title: "Removing KDE -- all files back to normal."
date: 2011-08-05
forum: Desktop Environments
---

### Post by GoffyGoober on 2011-08-05
Quite a bit earlier, I got KDE on my computer seeing what's so great about it. But I found some problems I don't like about it:
[LIST]
[*]It was pretty slow -- even on settings set for lowest CPU.
[*]It was a bit confusing.
[*]Everything can't be where I need it most.
[*]**On start up, it isn't so pretty.**
[/LIST]

I even am planning on making some programs (that might have to be embedded) and contribute to ubuntu but I'd like to make them with (as close as possible) original source files. **And I don't want to reformat my partition!**

Other relevant information: I use gnome (Ubuntu classic), have 11.04, no silly other versions of Ubuntu(like edubuntu, xubuntu, etc.) except for KDE compatibility, and Ubuntu being installed by a Ubuntu disk. My login screen is not KDE. And I forgot which Google result I used.

---

### Post by dniMretsaM on 2011-08-05
```
sudo apt-get remove akonadi-server akregator amarok amarok-common  amarok-utils appmenu-qt apport-kde apturl-kde ark bluedevil cdparanoia   cdrdao docbook-xsl dolphin dragonplayer freespacenotifier gdebi-core  gdebi-kde gnupg-agent gnupg2 gpgsm   gtk2-engines-oxygen gwenview ibus-qt4 icoutils jockey-kde k3b k3b-data  kaddressbook kamera kate kcalc kde-config-gtk   kde-config-touchpad kde-window-manager kde-zeroconf kdebase-bin  kdebase-data kdebase-runtime kdebase-runtime-data   kdebase-workspace kdebase-workspace-bin kdebase-workspace-data  kdebase-workspace-kgreet-plugins kdegames-card-data   kdegraphics-libs-data kdegraphics-strigi-plugins kdelibs-bin  kdelibs5-data kdelibs5-plugins kdemultimedia-kio-plugins   kdenetwork-filesharing kdepasswd kdepim-groupware kdepim-kresources  kdepim-runtime kdepim-strigi-plugins kdepim-wizards   kdepimlibs-kio-plugins kdesudo kdm kdoctools kfind khelpcenter4  kinfocenter klipper kmag kmail kmix kmousetool knm-runtime   knotes konsole kontact kopete kopete-message-indicator korganizer  kpackagekit kpat kppp krdc krfb krosspython ksnapshot   ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data  kubuntu-debug-installer kubuntu-default-settings   kubuntu-desktop kubuntu-docs kubuntu-firefox-installer  kubuntu-konqueror-shortcuts kubuntu-netbook-default-settings   kubuntu-notification-helper kvkbd kwalletmanager language-selector-kde  libakonadi-contact4 libakonadi-kabc4   libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4  libakonadiprotocolinternals1 libao-common libao4 libasyncns0 libattica0   libaudio2 libbluedevil1 libboost-program-options1.42.0 libcln6  libclucene0ldbl libdbusmenu-qt2 libdebconf-kde0 libdiscid0   libdmtx0a libepub0 libflac++6 libgif4 libgpgme++2 libgps19 libibus-qt1  libilmbase6 libindicate-qt1 libiodbc2 libk3b6   libkabc4 libkatepartinterfaces4 libkblog4 libkcal4 libkcalcore4  libkcalutils4 libkcddb4 libkcmutils4 libkdcraw9   libkde3support4 libkdecorations4 libkdecore5 libkdegames5 libkdepim4  libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4   libkemoticons4 libkephal4a libkexiv2-9 libkfile4 libkholidays4  libkhtml5 libkidletime4 libkimap4 libkimproxy4 libkio5   libkipi8 libkjsapi4 libkjsembed4 libkldap4 libkleo4 libkmediaplayer4  libkmime4 libknewstuff2-4 libknewstuff3-4   libknotifyconfig4 libkntlm4 libkonq5-templates libkonq5a  libkontactinterface4 libkopete4 libkparts4 libkpgp4   libkpimidentities4 libkpimtextedit4 libkpimutils4 libkprintutils4  libkpty4 libkresources4 libkrosscore4 libksba8   libkscreensaver5 libksgrd4 libksieve4 libksignalplotter4  libktexteditor4 libktnef4 libktorrent-l10n libktorrent2   libkunitconversion4 libkutils4 libkwineffects1a libkworkspace4  libkxmlrpcclient4 liblastfm0 libloudmouth1-0   libmailtransport4 libmessagecore4 libmessagelist4 libmicroblog4  libmimelib4 libmng1 libmpcdec6 libmsn0.3 libmusicbrainz3-6   libmysqlclient16 libnepomuk4 libnepomukquery4a libnepomukutils4  libntrack-qt4-1 libntrack0 libokularcore1 libopenexr6   libotr2 libpackagekit-glib2-14 libpackagekit-qt14 libphonon4  libplasma-geolocation-interface4 libplasma3 libplasmaclock4b   libplasmagenericshell4 libpolkit-qt-1-1 libpoppler-qt4-3  libpowerdevilcore0 libprocesscore4b libprocessui4a libqalculate5   libqapt-runtime libqapt1 libqca2 libqca2-plugin-ossl libqgpgme1  libqimageblitz4 libqjson0 libqt4-dbus libqt4-declarative   libqt4-designer libqt4-help libqt4-network libqt4-opengl  libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql   libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml  libqt4-xmlpatterns libqtassistantclient4 libqtcore4   libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network  libqtscript4-sql libqtscript4-uitools libqtscript4-xml   libqtwebkit4 libreadline5 libreoffice-kde libreoffice-style-oxygen  libsolid4 libsolidcontrol4a libsolidcontrolifaces4a   libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libsyndication4  libtag-extras1 libtaskmanager4b libthreadweaver4   libvirtodbc0 libvncserver0 libweather-ion6 libzip1  mysql-client-core-5.1 mysql-common mysql-server-core-5.1   nepomukcontroller network-manager-pptp-kde ntrack-module-libnl-0  odbcinst odbcinst1debian2 okular okular-extra-backends   oxygen-cursor-theme oxygen-icon-theme oxygen-icon-theme-complete  packagekit packagekit-backend-aptcc partitionmanager   phonon phonon-backend-gstreamer pinentry-gtk2 pinentry-qt4  plasma-dataengines-addons plasma-dataengines-workspace   plasma-desktop plasma-netbook plasma-scriptengine-declarative  plasma-scriptengine-javascript plasma-scriptengine-python   plasma-widget-facebook plasma-widget-folderview plasma-widget-kimpanel  plasma-widget-kimpanel-backend-ibus   plasma-widget-menubar plasma-widget-message-indicator  plasma-widget-networkmanagement plasma-widget-quickaccess   plasma-widgets-addons plasma-widgets-workspace  plymouth-theme-kubuntu-logo plymouth-theme-kubuntu-text polkit-kde-1   printer-applet python-kde4 python-packagekit python-pyudev python-qt4  python-qt4-dbus python-sip qapt-batch quassel   quassel-data rekonq shared-desktop-ontologies software-properties-kde  soprano-daemon system-config-printer-kde   systemsettings update-manager-kde usb-creator-kde userconfig  virtuoso-minimal virtuoso-opensource-6.1-bin   virtuoso-opensource-6.1-common && sudo apt-get install  ubuntu-desktop
``` Will completely remove KDE and leave GNOME fully functional.

---

### Post by GoffyGoober on 2011-08-05
> **dniMretsaM said:**
> ```
sudo apt-get remove akonadi-server akregator amarok amarok-common  amarok-utils appmenu-qt apport-kde apturl-kde ark bluedevil cdparanoia   cdrdao docbook-xsl dolphin dragonplayer freespacenotifier gdebi-core  gdebi-kde gnupg-agent gnupg2 gpgsm   gtk2-engines-oxygen gwenview ibus-qt4 icoutils jockey-kde k3b k3b-data  kaddressbook kamera kate kcalc kde-config-gtk   kde-config-touchpad kde-window-manager kde-zeroconf kdebase-bin  kdebase-data kdebase-runtime kdebase-runtime-data   kdebase-workspace kdebase-workspace-bin kdebase-workspace-data  kdebase-workspace-kgreet-plugins kdegames-card-data   kdegraphics-libs-data kdegraphics-strigi-plugins kdelibs-bin  kdelibs5-data kdelibs5-plugins kdemultimedia-kio-plugins   kdenetwork-filesharing kdepasswd kdepim-groupware kdepim-kresources  kdepim-runtime kdepim-strigi-plugins kdepim-wizards   kdepimlibs-kio-plugins kdesudo kdm kdoctools kfind khelpcenter4  kinfocenter klipper kmag kmail kmix kmousetool knm-runtime   knotes konsole kontact kopete kopete-message-indicator korganizer  kpackagekit kpat kppp krdc krfb krosspython ksnapshot   ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data  kubuntu-debug-installer kubuntu-default-settings   kubuntu-desktop kubuntu-docs kubuntu-firefox-installer  kubuntu-konqueror-shortcuts kubuntu-netbook-default-settings   kubuntu-notification-helper kvkbd kwalletmanager language-selector-kde  libakonadi-contact4 libakonadi-kabc4   libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4  libakonadiprotocolinternals1 libao-common libao4 libasyncns0 libattica0   libaudio2 libbluedevil1 libboost-program-options1.42.0 libcln6  libclucene0ldbl libdbusmenu-qt2 libdebconf-kde0 libdiscid0   libdmtx0a libepub0 libflac++6 libgif4 libgpgme++2 libgps19 libibus-qt1  libilmbase6 libindicate-qt1 libiodbc2 libk3b6   libkabc4 libkatepartinterfaces4 libkblog4 libkcal4 libkcalcore4  libkcalutils4 libkcddb4 libkcmutils4 libkdcraw9   libkde3support4 libkdecorations4 libkdecore5 libkdegames5 libkdepim4  libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4   libkemoticons4 libkephal4a libkexiv2-9 libkfile4 libkholidays4  libkhtml5 libkidletime4 libkimap4 libkimproxy4 libkio5   libkipi8 libkjsapi4 libkjsembed4 libkldap4 libkleo4 libkmediaplayer4  libkmime4 libknewstuff2-4 libknewstuff3-4   libknotifyconfig4 libkntlm4 libkonq5-templates libkonq5a  libkontactinterface4 libkopete4 libkparts4 libkpgp4   libkpimidentities4 libkpimtextedit4 libkpimutils4 libkprintutils4  libkpty4 libkresources4 libkrosscore4 libksba8   libkscreensaver5 libksgrd4 libksieve4 libksignalplotter4  libktexteditor4 libktnef4 libktorrent-l10n libktorrent2   libkunitconversion4 libkutils4 libkwineffects1a libkworkspace4  libkxmlrpcclient4 liblastfm0 libloudmouth1-0   libmailtransport4 libmessagecore4 libmessagelist4 libmicroblog4  libmimelib4 libmng1 libmpcdec6 libmsn0.3 libmusicbrainz3-6   libmysqlclient16 libnepomuk4 libnepomukquery4a libnepomukutils4  libntrack-qt4-1 libntrack0 libokularcore1 libopenexr6   libotr2 libpackagekit-glib2-14 libpackagekit-qt14 libphonon4  libplasma-geolocation-interface4 libplasma3 libplasmaclock4b   libplasmagenericshell4 libpolkit-qt-1-1 libpoppler-qt4-3  libpowerdevilcore0 libprocesscore4b libprocessui4a libqalculate5   libqapt-runtime libqapt1 libqca2 libqca2-plugin-ossl libqgpgme1  libqimageblitz4 libqjson0 libqt4-dbus libqt4-declarative   libqt4-designer libqt4-help libqt4-network libqt4-opengl  libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql   libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml  libqt4-xmlpatterns libqtassistantclient4 libqtcore4   libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network  libqtscript4-sql libqtscript4-uitools libqtscript4-xml   libqtwebkit4 libreadline5 libreoffice-kde libreoffice-style-oxygen  libsolid4 libsolidcontrol4a libsolidcontrolifaces4a   libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libsyndication4  libtag-extras1 libtaskmanager4b libthreadweaver4   libvirtodbc0 libvncserver0 libweather-ion6 libzip1  mysql-client-core-5.1 mysql-common mysql-server-core-5.1   nepomukcontroller network-manager-pptp-kde ntrack-module-libnl-0  odbcinst odbcinst1debian2 okular okular-extra-backends   oxygen-cursor-theme oxygen-icon-theme oxygen-icon-theme-complete  packagekit packagekit-backend-aptcc partitionmanager   phonon phonon-backend-gstreamer pinentry-gtk2 pinentry-qt4  plasma-dataengines-addons plasma-dataengines-workspace   plasma-desktop plasma-netbook plasma-scriptengine-declarative  plasma-scriptengine-javascript plasma-scriptengine-python   plasma-widget-facebook plasma-widget-folderview plasma-widget-kimpanel  plasma-widget-kimpanel-backend-ibus   plasma-widget-menubar plasma-widget-message-indicator  plasma-widget-networkmanagement plasma-widget-quickaccess   plasma-widgets-addons plasma-widgets-workspace  plymouth-theme-kubuntu-logo plymouth-theme-kubuntu-text polkit-kde-1   printer-applet python-kde4 python-packagekit python-pyudev python-qt4  python-qt4-dbus python-sip qapt-batch quassel   quassel-data rekonq shared-desktop-ontologies software-properties-kde  soprano-daemon system-config-printer-kde   systemsettings update-manager-kde usb-creator-kde userconfig  virtuoso-minimal virtuoso-opensource-6.1-bin   virtuoso-opensource-6.1-common && sudo apt-get install  ubuntu-desktop
``` Will completely remove KDE and leave GNOME fully functional.
Nope, didn't work. Absolutely no change in anyhting. I already Googled this problem and found about the same line of code. KDE is still loadable... GRUB's still teal, along with the:

[CENTER][SIZE="4"][FONT="Courier New"][B][COLOR="MediumTurquoise"]Kubuntu
. . . [/COLOR][COLOR="Teal"].[/COLOR][/B][/SIZE][/FONT][/CENTER]

(Wow that looks exact... just imagine the backing be the color of the text and the text being white except for the animated dark dots.)
I sure hope I don't have to reformat. :(

---

### Post by GoffyGoober on 2011-08-05
How do I completely remove [COLOR="Teal"]KDE[/COLOR] from my system? This includes all files it has edited. For example the *Ubuntu* loading screen that changed into:

[CENTER][FONT="Courier New"][B][SIZE="5"][COLOR="MediumTurquoise"]Kubuntu
. . . [/COLOR][COLOR="Teal"].[/COLOR][/SIZE][/B][/FONT][/CENTER]

I tried [COLOR="Teal"]KDE[/COLOR], but don't like it. I originally installed the normal Ubuntu and put [COLOR="teal"]KDE[/COLOR] off, so I know the files are there somewhere. This means I already have a normal login screen and Unity and Gnome. All past efforts didn't do anything at all. This also means the about-150-words command line. Any and all suggestions would be helpful, thanks!

---

### Post by haqking on 2011-08-05
see here

[]("http://www.psychocats.net/ubuntu/purexfce")_[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)_

remember though that Kubuntu means it is buitl using KDE as preferred, you cna run KDE and Gnome together and choose at login.

---

### Post by GoffyGoober on 2011-08-05
> **haqking said:**
> see here

[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/purexfce")

remember though that Kubuntu means it is buitl using KDE as preferred, you cna run KDE and Gnome together and choose at login.
Well, actually, this is the 150-word command... I already tried it, but it didn't work. But thanks for the reply, though!

---

### Post by haqking on 2011-08-05
> **GoffyGoober said:**
> Well, actually, this is the 150-word command... I already tried it, but it didn't work. But thanks for the reply, though!


well i take it you chose the correct version at the top like 10.04 or 10.10 or 11.04 etc

then the correct command fomr the list ?

What error messages ar you getting then ?

also the link you quoted from my post for some reason goes to wrong page you wanted this one [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

although the link says the same it goes to the xfce page

---

### Post by GoffyGoober on 2011-08-05
> **haqking said:**
> well i take it you chose the correct version at the top like 10.04 or 10.10 or 11.04 etc

then the correct command fomr the list ?

What error messages ar you getting then ?

also the link you quoted from my post for some reason goes to wrong page you wanted this one [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

although the link says the same it goes to the xfce page

Hmm... I don't know what happened to the quote I made... but here is the output:
> [sudo] password for *******: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libaccess-bridge-java : Depends: default-jre but it is not going to be installed or
                                  openjdk-6-jre but it is not going to be installed or
                                  sun-java6-jre but it is not going to be installed
E: Broken packages

But I'm not giving out the ****** at the top, or the input of the **huge** line of code.

---

### Post by haqking on 2011-08-05
> **GoffyGoober said:**
> Hmm... I don't know what happened to the quote I made... but here is the output:

But I'm not giving out the ****** at the top, or the input of the **huge** line of code.

a maybe obvious question.

but have you at login chosen to log back in using Gnome as you said it was origainlly Ubuntu which you added KDE to and not Kubuntu you started with ?

the broken dependencies are java

---

### Post by GoffyGoober on 2011-08-05
> **haqking said:**
> a maybe obvious question.

but have you at login chosen to log back in using Gnome as you said it was origainlly Ubuntu which you added KDE to and not Kubuntu you started with ?

the broken dependencies are java
I know that it's saying something is up with java...
But what I gathered by what you just said, I have my default login to "Ubuntu Classic", because I'm not a real fan of Unity, either.
And according to Update Manager, all my programs are up to date.

---

### Post by GoffyGoober on 2011-08-05
> **GoffyGoober said:**
> I know that it's saying something is up with java...
But what I gathered by what you just said, I have my default login to "Ubuntu Classic", because I'm not a real fan of Unity, either.
And according to Update Manager, all my programs are up to date.
Oh, sorry, it had one thing out of date -- Gnome user's guide...

---

### Post by GoffyGoober on 2011-08-05
> **GoffyGoober said:**
> Oh, sorry, it had one thing out of date -- Gnome user's guide...
NOW it's updated.

---

### Post by haqking on 2011-08-05
> **GoffyGoober said:**
> I know that it's saying something is up with java...
But what I gathered by what you just said, I have my default login to "Ubuntu Classic", because I'm not a real fan of Unity, either.
And according to Update Manager, all my programs are up to date.

OK so you can login to Ubuntu Classic with no problems then ?

you just want to remove the K related stuff left behind is this correct ?

and when you do so you get errors ?

If you can login to classic then in software centre or better synaptic have you tried removing KDE from there which is probably where you installed it from right ?

---

### Post by GoffyGoober on 2011-08-05
> **haqking said:**
> OK so you can login to Ubuntu Classic with no problems then ?

you just want to remove the K related stuff left behind is this correct ?

and when you do so you get errors ?

If you can login to classic then in software centre or better synaptic have you tried removing KDE from there which is probably where you installed it from right ?
If I did it that way, it would be mush easier...
See, I don't remember the method I used. I just googled it.
But I'll look at if there is a KDE package...
I think the line of code was somthing like:
```
sudo something something KDE get
```
I had KDE for a while, but just not getting rid of it, untill now... but the line of code might have been like:
```
sudo apt-get KDE blah blah blah
```
So now I'll open the Software Center...

---

### Post by GoffyGoober on 2011-08-05
This seems like it's working... I'm going to reboot my computer now.

---

### Post by GoffyGoober on 2011-08-05
I can no longer get onto KDE, it seems like it's off... I'll search on my computer "KDE" and see if it brings up anything. But what do we do about grub being teal and the loader saying KDE?

---

### Post by GoffyGoober on 2011-08-05
Um... 1,098 results... I don't know if it got off...

---

### Post by overdrank on 2011-08-05
Hi and welcome, please do not create multiple threads on the same issue. Threads merged.

---


---
title: "Changing from Kubuntu to Ubuntu - KDE implications ?"
date: 2017-05-02
forum: Desktop Environments
---

### Post by oygle on 2017-05-02
Have been running Kubuntu now for several years. Just recently swapped KMail for Claws ( [https://ubuntuforums.org/showthread.php?t=2349281&p=13639550#post13639550](https://ubuntuforums.org/showthread.php?t=2349281&p=13639550#post13639550) ) and I don't use any of the other PIM applications. During the 7 months that KMail gave problems, I noticed on a number of forums that people mentioned that KDE is bloated. Given the fact this desktop is 9 yrs old, I'm now looking at going back to Ubuntu.

What are the KDE implications of doing this ? No doubt it depends on what applications I'm using. One is KMyMoney which uses kde-runtime > 4:4.10

There are 2225 packages installed. is there an easy method to determine if these packages have dependency on KDE please ?

---

### Post by vasa1 on 2017-05-02
Try```
apt-get remove -s kde-runtime | grep Remv | cut -d ' ' -f 2
```Note that "-s" means that only a simulation will be run. Nothing will be removed. And you don't need *sudo*.

I can't verify what will be listed because I don't use KDE. However, I have some packages with qt dependencies:```
apt-get remove -s libqt* | grep Remv | cut -d ' ' -f 2
audacity
code-of-conduct-signing-assistant
python3-pyqt4
qt-at-spi
libqt4-dbus
simplescreenrecorder
unetbootin
libqtgui4
libqt4-declarative
libqt4-designer
libqt4-help
libqtassistantclient4
libqt4-network
libqtwebkit4
libqt4-opengl
libqt4-scripttools
libqt4-script
libqt4-sql-mysql
libqt4-sql
libqt4-svg
libqt4-test
qdbus
libqtdbus4
libqt4-xml
libqt4-xmlpatterns
libsuil-0-0
libqtcore4

```

---

### Post by Erik1984 on 2017-05-02
Is it a big problem if a program has KDE dependencies?

---

### Post by oygle on 2017-05-02
> **vasa1 said:**
> Try```
apt-get remove -s kde-runtime | grep Remv | cut -d ' ' -f 2
```Note that "-s" means that only a simulation will be run. Nothing will be removed. And you don't need *sudo*.

Thanks for that. I had seen various posts regards how to list the applications (apps not packages), but not sure if they were 'safe'. Like some had a recursive **ls** in them, which other posters stated was dangerous. Have used the above command and got ..

```
$ apt-get remove -s kde-runtime | grep Remv | cut -d ' ' -f 2
amarok
amarok-utils
apturl-kde
language-pack-kde-en
k3b-i18n
k3b
kde-baseapps-bin
libreoffice-kde
skanlite
kde-runtime
kdeconnect
kdemultimedia-kio-plugins
plasma-discover
ubuntu-release-upgrader-qt
kdesudo
kfind
kio-audiocd
kmymoney
krdc
ktorrent
okular
python3-pykde4
```

This one is a bit longer ...

```
$ apt-get remove -s libqt* | grep Remv | cut -d ' ' -f 2
amarok
amarok-utils
apport-kde                                                                                                                                                              
apturl-kde                                                                                                                                                              
ark                                                                                                                                                                     
plasma-desktop                                                                                                                                                          
dolphin                                                                                                                                                                 
libkf5baloowidgets-bin                                                                                                                                                  
baloo-kf5                                                                                                                                                               
baloo-utils                                                                                                                                                             
bcompare                                                                                                                                                                
bluedevil                                                                                                                                                               
breeze                                                                                                                                                                  
dragonplayer                                                                                                                                                            
sddm                                                                                                                                                                    
sddm-theme-breeze                                                                                                                                                       
plasma-widgets-addons                                                                                                                                                   
plasma-workspace                                                                                                                                                        
frameworkintegration                                                                                                                                                    
gstreamer-qapt                                                                                                                                                          
gtk3-engines-breeze                                                                                                                                                     
gwenview                                                                                                                                                                
hplip-gui                                                                                                                                                               
ibus-qt4                                                                                                                                                                
language-pack-kde-en                                                                                                                                                    
k3b-i18n                                                                                                                                                                
k3b                                                                                                                                                                     
kde-telepathy                                                                                                                                                                      
kde-telepathy-minimal                                                                                                                                                              
kde-telepathy-auth-handler                                                                                                                                                         
kde-telepathy-text-ui                                                                                                                                                              
libktpcommoninternals9                                                                                                                                                             
kde-config-telepathy-accounts                                                                                                                                                      
kaccounts-integration                                                                                                                                                              
kaccounts-providers                                                                                                                                                                
kactivities                                                                                                                                                                        
kamera
kate
libreoffice-kde
skanlite
kde-runtime
kdelibs5-plugins
katepart
kcalc
kde-baseapps-bin
kscreen
kdeconnect-plasma
kde-cli-tools
kde-config-gtk-style
kde-config-mailtransport
kde-config-screenlocker
kde-config-sddm
kde-config-whoopsie
kde-l10n-engb
kde-spectacle
kde-style-breeze-qt4
kde-style-breeze
kde-style-oxygen-qt5
kde-style-qtcurve-qt4
kde-style-qtcurve-qt5
kde-telepathy-approver
kde-telepathy-contact-list
kde-telepathy-desktop-applets
kde-telepathy-filetransfer-handler
kde-telepathy-integration-module
kde-telepathy-kaccounts
kde-telepathy-kpeople
kde-telepathy-send-file
kdeconnect
kded5
kdelibs-bin
kdemultimedia-kio-plugins
kdenetwork-filesharing
kdepimlibs-kio-plugins
plasma-discover
ubuntu-release-upgrader-qt
kdesudo
kdoctools
khelpcenter
kdoctools5
keepassx
kfind
kgamma5
khotkeys
kimageformat-plugins
kinfocenter
muon-updater
muon-notifier
plasma-discover-updater
plasma-discover-private
libkf5noteshared5
libkf5pimcommon5
libkf5newstuff5
kio
kinit
kio-audiocd
kio-extras
kio-mtp
kmenuedit
kmymoney
kubuntu-notification-helper
konsole
konsole-kpart
konversation
kpackagelauncherqml
kpackagetool5
krdc
plasma-dataengines-addons
kross
ksshaskpass
ksysguard
ksystemlog
ktexteditor-katepart
ktnef
ktorrent
kubuntu-driver-manager
kwalletmanager
kwayland-integration
kwin-addons
kwin
kwin-x11
kwin-common
kwin-style-breeze
kwrited
signon-ui
signon-ui-x11
libkaccounts1
libaccounts-qt5-1
libakonadi-kmime4
libakonadi-kde4
libakonadiprotocolinternals1
libalkimia4
libappstreamqt1
python3-pykde4
plasma-scriptengine-javascript
libplasma3
libkatepartinterfaces4
libknewstuff3-4
okular-extra-backends
libkhtml5
libktexteditor4
libkdeui5
libattica0.4
libbaloofiles4
libbalooxapian4
libbaloocore4
sni-qt
libdbusmenu-qt2
qapt-deb-installer
libdebconf-kde1
libdolphinvcs5
libkf5mailcommon5
libkf5messagecomposer5
libkf5templateparser5
libkf5messageviewer5
libkf5libkdepim5
libkf5tnef5
libkf5calendarutils5
libgrantlee-templates5
libkf5messagelist5
libkf5messagecore5
libkf5libkleo5
libkf5pimtextedit5
libgrantlee-textdocument5
libgwengui-qt4-0
libibus-qt1
libk3b6-extracodecs
libk3b6
libkabc4
okular
libkactivities6
libkcalcore4
libkcddb4
libkcmutils4
libkcompactdisc4
libkde3support4
libkdeclarative5
libkdecorations2-5v5
libkdecorations2private5v5
libkrosscore4
libkdesu5
libkpty4
libkdecore5
libkdewebkit5
libkdnssd4
libkpimutils4
libkemoticons4
libkexiv2-11v5
print-manager
plasma-wallpapers-addons
plasma-framework
qml-module-org-kde-extensionplugin
qml-module-org-kde-activities
libkf5activities5
libkf5activitiesexperimentalstats1
libkf5akonadiagentbase5
libkf5incidenceeditorsng5
libkf5eventviews5
libkf5akonadicalendar5
libkf5calendarsupport5
libkf5kdepimdbusinterfaces5
libkf5akonadicontact5
libkolab1
libkf5mailtransport5
libkf5akonadicore5
libkf5akonadicore-bin
libkf5mailimporter5
libkf5akonadimime5
libkf5akonadinotes5
libkf5akonadiwidgets5
libkf5akonadiprivate5
libkf5akonadisearchdebug5
libkf5akonadisearchpim5
libkf5alarmcalendar5
libkf5plasmaquick5
plasma-runners-addons
libkf5plasma5
libkf5texteditor5
libkf5archive5
libkf5webkit5
libkf5parts-plugins
libkf5parts5
user-manager
libkf5kiofilewidgets5
libkf5xmlgui5
libkf5attica5
systemsettings
powerdevil
libkf5auth5
libkf5baloowidgets5
libkf5baloo5
libkf5balooengine5
qml-module-org-kde-bluezqt
libkf5bluezqt6
libkf5bookmarks5
libkf5gapitasks5
libkf5calendarcore5
libkf5calendarevents5
libkf5syndication5
libkf5codecs5
qml-module-org-kde-kio
plasma-nm
libkf5kiowidgets5
libtaskmanager5
libkf5completion5
libkf5config-bin
software-properties-kde
qapt-batch
partitionmanager
libkf5kiocore5
qml-module-org-kde-telepathy
libkf5configcore5
qml-module-org-kde-kquickcontrols
libpowerdevilcore2
libkf5configgui5
libktpwidgets9
libkf5kcmutils5
libprocessui7
libkf5configwidgets5
libkf5gapicontacts5
libkf5contacts5
libkf5kiontlm5
qml-module-org-kde-kcoreaddons
libkf5coreaddons5
libqapt3-runtime
polkit-kde-agent-1
libkscreenlocker5
libkf5crash5
libkf5dbusaddons-bin
signon-kwallet-extension
libkf5wallet-bin
libkf5dbusaddons5
qml-module-org-kde-kwindowsystem
qml-module-org-kde-kquickcontrolsaddons
libkf5declarative5
libkf5dnssd5
libkf5emoticons-bin
libkf5emoticons5
libkf5filemetadata-bin
libkf5filemetadata3
libkf5followupreminder5
libkf5gapicalendar5
libkf5gapidrive5
libkf5gapicore5
libkf5globalaccel-bin
plasma-pa
libkf5globalaccel5
libkf5globalaccelprivate5
libkf5gravatar5
liboxygenstyle5-5
libkfontinstui5
libkfontinst5
libkf5kdelibs4support5
libkf5guiaddons5
libkf5holidays5
libweather-ion7
libkf5i18n5
libkf5iconthemes-bin
libkwin4-effect-builtins1
libkf5iconthemes5
libkf5ksieveui5
libkf5identitymanagement5
libkf5idletime5
libkf5imap5
libkf5itemmodels5
libkf5peoplewidgets5
libkf5itemviews5
libkf5khtml-bin
libkf5khtml5
libkf5jobwidgets5
libkf5jsembed5
libkf5kdcraw5
libkf5kdelibs4support5-bin
libkf5kdgantt2-5
libkf5kipi30.0.0
libkf5kmanagesieve5
libkf5kontactinterface5
libkf5krossui5
libkf5krosscore5
libkf5ksieve5
libkf5ldap5
libkf5mbox5
libkf5mime5
libkf5modemmanagerqt6
libkf5networkmanagerqt6
libkf5wallet5
libkwalletbackend5-5
libkf5notifications5
libkf5notifyconfig5
libkf5quickaddons5
libkf5package5
libktpmodels9
libkf5people5
libkf5peoplebackend5
libkf5prison1
libkf5su-bin
libkf5su5
libkf5pty5
libkf5qgpgme5
qml-module-org-kde-runnermodel
milou
libkf5runner5
libkf5screen-bin
libkf5screen6
libkf5sendlater5
libktplogger9
libkf5service-bin
libkf5textwidgets5
libkf5service5
qml-module-org-kde-solid
libkf5solid5
sonnet-plugins
libkf5sonnetui5
libkf5sonnetcore5
libkf5style5
libksignalplotter7
libkf5sysguard-bin
libkf5threadweaver5
libkf5unitconversion5
libkf5waylandclient5
libkwineffects7
libkf5waylandserver5
liboxygenstyleconfig5-5
libkf5widgetsaddons5
libkf5windowsystem5
libkf5xmlgui-bin
libkf5xmlrpcclient5
libkonq5abi1
libkfile4
libkfilemetadata4
libkholidays4
libkidletime4
libkprintutils4
libkmediaplayer4
libkparts4
libknotifyconfig4
libkio5
libkjsembed4
libokularcore7
libkjsapi4
libkldap4
libkmime4
libknewstuff2-4
libkntlm4
libkonq-common
libkresources4
libksane0
libksgrd7
libktorrent-l10n
libktorrent5
libktpotr9
libkubuntu1
libkwinglutils7
libkwinxrenderutils7
libkworkspace5-5
libkxmlrpcclient4
liblastfm1
libmygpo-qt1
libntrack-qt4-1
libpackagekitqt5-0
phonon
phonon-backend-gstreamer
libphonon4
phonon4qt5-backend-gstreamer
libphonon4qt5-4
libplasma-geolocation-interface5
libpolkit-qt-1-1
libpolkit-qt5-1-1
libpoppler-qt4-4
libpoppler-qt5-1
libpowerdevilui5
libprocesscore7
libqapt3
libqca-qt5-2-plugins
libqca-qt5-2
libqca2-plugin-ossl
libqca2-plugins
libqca2
qml-module-qtmultimedia
libqt5multimedia5-plugins
libqgsttools-p1
libqimageblitz4
libqjson0
libqmobipocket1
libsolid4
python3-pyqt4
libqt4-dbus
libqtwebkit4
libqtgui4
libqt4-declarative
libqt4-qt3support
libqt4-designer
libqt4-help
libtelepathy-qt4-2
libqtassistantclient4
libqt4-network
libqt4-opengl
libqtscript4-xml
libqt4-script
libqt4-scripttools
libqtscript4-sql
libqt4-sql-mysql
libqt4-sql
libqt4-sql-sqlite
libqt4-svg
libqt4-test
libsyndication4
qdbus
libqt4-xml
libqt4-xmlpatterns
qttools5-dev-tools
python3-pyqt5
libqt5help5
libqt5clucene5
libqt5concurrent5
vlc
libqt5sql5-mysql
qdbus-qt5
libqt5xml5
qml-module-qtwebkit
libqt5webkit5
libqt5printsupport5
libqt5widgets5
libqt5core5a
libqt5multimediawidgets5
libqt5opengl5
libqt5gui5
libtelepathy-logger-qt5
libtelepathy-qt5-0
libqt5network5
qtwayland5
libqt5waylandclient5
libqt5dbus5
libqt5designercomponents5
libqt5designer5
libqt5multimediaquick-p5
libqt5multimedia5
libqt5qml-graphicaleffects
qml-module-qtgraphicaleffects
qml-module-qtquick-controls-styles-breeze
qml-module-qtquick-controls
qml-module-qtquick2
qml-module-org-kde-draganddrop
libqt5quick5
qtdeclarative5-xmllistmodel-plugin
qml-module-qtquick-xmllistmodel
qml-module-qtquick-window2
libqt5qml5
libqt5quickwidgets5
libqt5script5
signon-plugin-password
signond
libqt5sql5-sqlite
libqt5sql5
libqt5svg5
libqt5test5
libqt5x11extras5
libqt5xmlpatterns5
libthreadweaver4
python3-dbus.mainloop.qt
libqtcore4
libqtcurve-utils2
libqtdbus4
libqtscript4-gui
libqtscript4-uitools
libqtscript4-core
libqtscript4-network
libsignon-extension1
signon-plugin-oauth2
libsignon-plugins-common1
libsignon-qt5-1
pinentry-qt4
pinentry-qt
python-qt4-dbus
python3-dbus.mainloop.pyqt5
qml-module-qt-labs-folderlistmodel
qml-module-qt-labs-settings
qml-module-qtquick-dialogs
qml-module-qtquick-layouts
qml-module-qtquick-privatewidgets
qt-at-spi
qt5-image-formats-plugins

```

> **Erik1984 said:**
> Is it a big problem if a program has KDE dependencies?

As my original posts stated - > During the 7 months that KMail gave problems, I noticed on a number of forums that people mentioned that KDE is bloated.

Is it possible to install Ubuntu **without** KDE ? Possibly that is impossible.  :D

I would prefer to think that it is possible to have a bare minimum of any KDE. Have been going through a few apps to find replacements ..

ibreoffice-kde ===> libreoffice
kfind  ===> catfish
kuser ===> gnome-system-tools

I read some comparison report yesterday that compared Ubuntu to Kubuntu and GNOME. In terms of performance and load on CPU/Memory, Ubuntu came out as the 'winner', closely followed by GNOME. In consideration of a computer that is 9 years old, I'll always prefer an OS that is lighter and quicker. The reports and others seem to confirm the statements by others that KDE places a heavy load.

---

### Post by vasa1 on 2017-05-02
> **oygle said:**
> Thanks for that. I had seen various posts regards how to list the applications (apps not packages), but not sure if they were 'safe'. Like some had a recursive **ls** in them, which other posters stated was dangerous. ...

Is it possible to install Ubuntu **without** KDE ? Possibly that is impossible.  :D

I would prefer to think that it is possible to have a bare minimum of any KDE. Have been going through a few apps to find replacements ..

ibreoffice-kde ===> libreoffice
kfind  ===> catfish
kuser ===> gnome-system-tools

I read some comparison report yesterday that compared Ubuntu to Kubuntu and GNOME. In terms of performance and load on CPU/Memory, Ubuntu came out as the 'winner', closely followed by GNOME. In consideration of a computer that is 9 years old, I'll always prefer an OS that is lighter and quicker. The reports and others seem to confirm the statements by others that KDE places a heavy load.
[LIST]
[*]I'm not sure that a recursive **ls**, *per se*, is dangerous.
[*]I don't understand what you mean by "install Ubuntu **without** KDE".
[*]Re. "I read some comparison report yesterday", if that's a public link, please share it here.
[*]As for a 9 years old computer, mine is from 2009, no GPU, and a recent version of KDE Neon was pretty snappy when used from a Live USB.
[*]Why do you not think that Xubuntu or Lubuntu may be even lighter that Ubuntu or "GNOME" or "KDE"? 
[/LIST]

And libreoffice-kde is, I'm nearly certain, something that facilitates the integration of LibreOffice into a KDE environment. It's not a KDE version of LibreOffice.

---

### Post by oygle on 2017-05-02
> **vasa1 said:**
> 
I'm not sure that a recursive **ls**, *per se*, is dangerous.

I'm not sure either. I prefer your method though, to determine what applications are installed.  :)

> **vasa1 said:**
> 
I don't understand what you mean by "install Ubuntu **without** KDE".


Well, one application, KMyMoney needs kde-runtime, so no matter what *buntu I use, I'm stuck with that. Need and want to stay away from as much 'KDE' as possible, if that is possible. 

> **vasa1 said:**
> Re. "I read some comparison report yesterday", if that's a public link, please share it here.

[http://www.hecticgeek.com/2016/05/ubuntu-16-04-flavors-comparison/](http://www.hecticgeek.com/2016/05/ubuntu-16-04-flavors-comparison/)

> **vasa1 said:**
> As for a 9 years old computer, mine is from 2009, no GPU, and a recent version of KDE Neon was pretty snappy when used from a Live USB.

I haven't had any hardware problems at all with this old computer, an Asus. Just need to be mindful of what OS and apps are on it, as the last few weeks, it has been freezing, which is very uncommon.

> **vasa1 said:**
> ]Why do you not think that Xubuntu or Lubuntu may be even lighter that Ubuntu or "GNOME" or "KDE"? 

I haven't discounted those 2 at all. In fact a person in a mailing list has recommended Lubuntu (using the LXDE GOSFUI). That was one of the reasons to try and determine what applications are installed (although I do keep a list, but not 100% certain that is up to date). Once I know for sure what is installed, then I can also look at Xubuntu or Lubuntu.

> **vasa1 said:**
> libreoffice-kde is, I'm nearly certain, something that facilitates the integration of LibreOffice into a KDE environment. It's not a KDE version of LibreOffice.

Okay thanks, so it won't be an issue.

---

### Post by SeijiSensei on 2017-05-03
I suggest you start with an Lubuntu installation and see if you like it.  If so, then install KMyMoney.  It will bring in whatever KDE dependencies it needs.  You'll then have the LXDE desktop and access to the one KDE application you need.

---

### Post by oygle on 2017-05-07
> **SeijiSensei said:**
> I suggest you start with an Lubuntu installation and see if you like it.  If so, then install KMyMoney.  It will bring in whatever KDE dependencies it needs.  You'll then have the LXDE desktop and access to the one KDE application you need.

Thanks :)

---


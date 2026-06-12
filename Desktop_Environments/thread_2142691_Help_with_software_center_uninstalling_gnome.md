---
title: "Help with software center uninstalling gnome"
date: 2013-05-06
forum: Desktop Environments
---

### Post by abdorefky on 2013-05-06
[SIZE=2]i just upgraded to ubuntu 12.04 ... some extensions on gnome wasn't working so i went to unity and  purged the gnome
now before i install  the gnome i have selected all the package's down and pressed apply changes ....
the software center downloaded 327 MB and installed them ,, and when i restarted i have found that i installed KDE and XFCE and WINDOWS MAKER

i went to remove them ,, but guess what ..... the software center doesn't detect that gnome is installed . 
when i unselect packages press apply changes , nothing happend 
i dont know how this stupid software center installed the gnome and can't detect its installed !!!!![/SIZE]

[SIZE=2]**how can i fix this miss ,,, is there a command like uninstalled all packages that installed in the past 3 hours or so ??**[/SIZE]

---

### Post by abdorefky on 2013-05-06
i have no problem to uninstall all installed packages in the last 6 hours .. but how

---

### Post by Slim Odds on 2013-05-06
Look in the install history log in /var/log/apt/

---

### Post by abdorefky on 2013-05-06
[SIZE=1][B][SIZE=3][SIZE=2]cool , now how to uninstall them together from terminal ?[/SIZE][SIZE=3][SIZE=2] is there setting will remain ?[/SIZE] :(

[/SIZE][/SIZE][/B][SIZE=2]```

Start-Date: 2013-05-06  18:03:25
Commandline: aptdaemon role='role-commit-packages' sender=':1.216'
Install: kubuntu-debug-installer:amd64 (11.10ubuntu1, automatic), libkresources4:amd64 (4.8.5-0ubuntu0.1, automatic), 
qapt-batch:amd64 (1.3.1-0ubuntu2, automatic), 
xfce4-settings:amd64 (4.8.3-1ubuntu3, automatic), 
xscreensaver-gl:amd64 (5.15-2ubuntu1, automatic), 
plasma-desktopthemes-artwork:amd64 (4.8.5-0ubuntu0.1, automatic), 
libqrencode3:amd64 (3.1.1-1ubuntu1, automatic), menu-xdg:amd64 (0.5), 
libkprintutils4:amd64 (4.8.5-0ubuntu0.1, automatic), libofx4:amd64 (0.9.4-2, 
automatic), libkldap4:amd64 (4.8.5-0ubuntu0.1, automatic), 
planner:amd64 (0.14.5-1ubuntu3), 
libktnef4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libmono-sqlite4.0-cil:amd64 (2.10.8.1-1ubuntu2.2, automatic), 
virtuoso-minimal:amd64 (6.1.4+dfsg1-0ubuntu1, automatic), 
libnet-ssleay-perl:amd64 (1.42-1build1, automatic), 
libokularcore1abi1:amd64 (4.8.5-0ubuntu0.1, automatic), 
libevolution:amd64 (3.2.3-0ubuntu6, automatic), 
libgsf-1-common:amd64 (1.14.21-2, automatic), 
libkonq5-templates:amd64 (4.8.5-0ubuntu0.1, automatic), 
libqca2:amd64 (2.0.3-2, automatic), 
kopete-message-indicator:amd64 (0.2.1-0ubuntu2, automatic), 
libmono-system-web-services4.0-cil:amd64 (2.10.8.1-1ubuntu2.2, automatic), 
guile-1.8:amd64 (1.8.8+1-6ubuntu2, automatic), 
freespacenotifier:amd64 (4.8.5-0ubuntu0.3, automatic), 
kde-baseapps:amd64 (4.8.5-0ubuntu0.1, automatic), 
gnome-shell:amd64 (3.4.1-0ubuntu2, automatic), 
libkcalcore4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libgnome2-0:amd64 (2.32.1-2ubuntu1.1, automatic), 
plasma-containments-addons:amd64 (4.8.5-0ubuntu0.1, automatic), 
kde-baseapps-bin:amd64 (4.8.5-0ubuntu0.1, automatic), 
libpolkit-qt-1-1:amd64 (0.103.0-1, automatic), 
dia-libs:amd64 (0.97.2-5, automatic), 
libprison0:amd64 (1.0+dfsg-1, automatic), 
gnucash:amd64 (2.4.10-1), 
tumbler:amd64 (0.1.24-0ubuntu1, automatic), 
libkholidays4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libknewstuff2-4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libkeybinder0:amd64 (0.2.2-3build1, automatic), 
libgnomecanvas2-0:amd64 (2.30.3-1ubuntu1.1, automatic), 
libtumbler-1-0:amd64 (0.1.24-0ubuntu1, automatic), 
kde-workspace-data:amd64 (4.8.5-0ubuntu0.3, automatic), l
ibknewstuff3-4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libqapt-runtime:amd64 (1.3.1-0ubuntu2, automatic), 
libvirtodbc0:amd64 (6.1.4+dfsg1-0ubuntu1, automatic), 
libbonobo2-common:amd64 (2.32.1-0ubuntu1.1, automatic), 
libqca2-plugin-ossl:amd64 (2.0.0~beta3-1, automatic), 
libgtkhtml-4.0-common:amd64 (4.2.2-1ubuntu1.2, automatic), 
ksnapshot:amd64 (4.8.2-0ubuntu1, automatic), 
plasma-wallpapers-addons:amd64 (4.8.5-0ubuntu0.1, automatic), 
libkexiv2-data:amd64 (4.8.5-0ubuntu0.1, automatic), 
libxfce4ui-1-0:amd64 (4.8.1-1, automatic), 
libnepomuksync4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libkipi8:amd64 (4.8.5-0ubuntu0.1, automatic), 
libosp5:amd64 (1.5.2-10, automatic), 
libmono-web4.0-cil:amd64 (2.10.8.1-1ubuntu2.2, automatic), 
xfce4-notifyd:amd64 (0.2.2-1, automatic), 
libkipi-data:amd64 (4.8.5-0ubuntu0.1, automatic), 
xfce4-volumed:amd64 (0.1.13-2ubuntu1, automatic), 
libgwengui-gtk2-0:amd64 (4.3.1-1, automatic), 
evolution-plugins:amd64 (3.2.3-0ubuntu6, automatic), 
gdebi:amd64 (0.8.5build1), 
liburi-perl:amd64 (1.59-1, automatic), 
libmagickcore4:amd64 (6.6.9.7-5ubuntu3.2, automatic), 
planner-data:amd64 (0.14.5-1ubuntu3, automatic), 
libotr2:amd64 (3.2.0-4ubuntu0.1, automatic), 
libkdeclarative5:amd64 (4.8.5-0ubuntu0.1, automatic), 
evolution:amd64 (3.2.3-0ubuntu6, automatic), 
libnepomukquery4a:amd64 (4.8.5-0ubuntu0.1, automatic), 
konqueror-nsplugins:amd64 (4.8.5-0ubuntu0.1, automatic), 
libgnomeui-0:amd64 (2.24.5-2ubuntu2, automatic), 
libgnome2-bin:amd64 (2.32.1-2ubuntu1.1, automatic), 
libyaml-syck-perl:amd64 (1.19-1, automatic), 
libhtml-parser-perl:amd64 (3.69-1build1, automatic), 
kde-standard:amd64 (71~pre15ubuntu12.4), 
libplasma-geolocation-interface4:amd64 (4.8.5-0ubuntu0.3, automatic), 
kde-workspace-bin:amd64 (4.8.5-0ubuntu0.3, automatic), 
libkleo4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libmono-system-transactions4.0-cil:amd64 (2.10.8.1-1ubuntu2.2, automatic), 
libaqbanking-data:amd64 (5.0.22-1, automatic), 
libxfconf-0-2:amd64 (4.8.1-1, automatic), 
libhttp-daemon-perl:amd64 (6.00-1, automatic), 
libjpeg-progs:amd64 (8c-2ubuntu7, automatic), 
libpst4:amd64 (0.6.54-0ubuntu1, automatic), 
libcrypt-ssleay-perl:amd64 (0.57-2ubuntu1, automatic), 
libweather-ion6:amd64 (4.8.5-0ubuntu0.3, automatic), 
libkonq-common:amd64 (4.8.5-0ubuntu0.1, automatic), 
bogofilter-bdb:amd64 (1.2.2+dfsg1-1ubuntu0.12.04.1, automatic), 
xfce4-panel:amd64 (4.8.6-2ubuntu2, automatic), 
gwenview:amd64 (4.8.5-0ubuntu0.1, automatic), 
libthreadweaver4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libmarblewidget13:amd64 (4.8.5-0ubuntu0.2, automatic), 
libbonobo2-0:amd64 (2.32.1-0ubuntu1.1, automatic), 
libkdecore5:amd64 (4.8.5-0ubuntu0.1, automatic), 
thunar-volman:amd64 (0.6.1-0ubuntu1, automatic), 
libmagickwand4:amd64 (6.6.9.7-5ubuntu3.2, automatic), 
phonon:amd64 (4.7.0really4.6.0-0ubuntu1, automatic), 
libnepomukutils4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libktexteditor4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libexo-common:amd64 (0.6.2-4, automatic), 
libkmediaplayer4:amd64 (4.8.5-0ubuntu0.1, automatic), 
docbook-xsl:amd64 (1.76.1+dfsg-1ubuntu1, automatic), 
kcalc:amd64 (4.8.3-0ubuntu0.1, automatic), 
libcdt4:amd64 (2.26.3-10ubuntu1, automatic), 
libfont-afm-perl:amd64 (1.20-1, automatic), 
wmaker:amd64 (0.95.0+20111028-4), 
libdate-manip-perl:amd64 (6.25-1, automatic), 
kdeplasma-addons:amd64 (4.8.5-0ubuntu0.1, automatic), 
oxygen-icon-theme:amd64 (4.8.3-0ubuntu0.1, automatic), 
libdbi1:amd64 (0.8.4-5.1, automatic), 
libakonadi-kmime4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libgps20:amd64 (3.4-2, automatic), 
plasma-scriptengine-javascript:amd64 (4.8.5-0ubuntu0.1, automatic), 
libaqofxconnect7:amd64 (5.0.22-1, automatic), 
klipper:amd64 (4.8.5-0ubuntu0.3, automatic), 
libhttp-negotiate-perl:amd64 (6.00-2, automatic), 
libmagickcore4-extra:amd64 (6.6.9.7-5ubuntu3.2, automatic), 
libakonadiprotocolinternals1:amd64 (1.7.2-0ubuntu1, automatic), 
libkrosscore4:amd64 (4.8.5-0ubuntu0.1, automatic), 
xfdesktop4-data:amd64 (4.8.3-2ubuntu7, automatic), 
libfile-listing-perl:amd64 (6.03-1, automatic), 
kaddressbook:amd64 (4.8.5-0ubuntu0.1, automatic), 
libhtml-form-perl:amd64 (6.00-1, automatic), 
libplasmaclock4abi3:amd64 (4.8.5-0ubuntu0.3, automatic), 
xscreensaver-data:amd64 (5.15-2ubuntu1, automatic), 
xfce4:amd64 (4.8.0.3), 
kwalletmanager:amd64 (4.8.4-0ubuntu0.1, automatic), 
gdebi-core:amd64 (0.8.5build1, automatic), 
libgtkhtml-4.0-0:amd64 (4.2.2-1ubuntu1.2, automatic), 
libpoppler-qt4-3:amd64 (0.18.4-1ubuntu3.1, automatic), 
libgoffice-0.8-8-common:amd64 (0.8.17-1, automatic), 
ksysguard:amd64 (4.8.5-0ubuntu0.3, automatic), 
evolution-common:amd64 (3.2.3-0ubuntu6, automatic), 
xfce-keyboard-shortcuts:amd64 (4.8.1-1, automatic), 
orage:amd64 (4.8.3-1, automatic), 
mysql-server-core-5.5:amd64 (5.5.31-0ubuntu0.12.04.1, automatic), 
libcln6:amd64 (1.3.2-1.1, automatic), 
konq-plugins:amd64 (4.8.5-0ubuntu0.1, automatic), 
libkactivities-bin:amd64 (4.8.5-0ubuntu0.1, automatic), 
libmessagecore4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libeventviews4:amd64 (4.8.5-0ubuntu0.1, automatic), 
akonadi-backend-mysql:amd64 (1.7.2-0ubuntu1, automatic), 
libkwineffects1abi3:amd64 (4.8.5-0ubuntu0.3, automatic), 
libkateinterfaces4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libgnome2.24-cil:amd64 (2.24.2-1, automatic), 
evolution-webcal:amd64 (2.32.0-2ubuntu2, automatic), 
libgadu3:amd64 (1.11.1-1, automatic), 
libcalendarsupport4:amd64 (4.8.5-0ubuntu0.1, automatic), 
virtuoso-opensource-6.1-bin:amd64 (6.1.4+dfsg1-0ubuntu1, automatic), 
dolphin:amd64 (4.8.5-0ubuntu0.1, automatic), 
kmenuedit:amd64 (4.8.5-0ubuntu0.3, automatic), 
kwrite:amd64 (4.8.5-0ubuntu0.1, automatic), 
plasma-dataengines-addons:amd64 (4.8.5-0ubuntu0.1, automatic), 
libsyndication4:amd64 (4.8.5-0ubuntu0.1, automatic), 
khelpcenter4:amd64 (4.8.5-0ubuntu0.1, automatic),
 libkmbox4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libsolid4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libdlrestrictions1:amd64 (0.14.2ubuntu5, automatic), 
liblqr-1-0:amd64 (0.4.1-1.1, automatic), 
marble-plugins:amd64 (4.8.5-0ubuntu0.2, automatic), 
blam:amd64 (1.8.9-2ubuntu1), 
libmessagecomposer4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libkontactinterface4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libhtml-tree-perl:amd64 (4.2-1, automatic), 
libnepomuk4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libkmanagesieve4:amd64 (4.8.5-0ubuntu0.1, automatic), 
gnome-session-fallback:amd64 (3.2.1-0ubuntu8, automatic), 
pinentry-gtk2:amd64 (0.8.1-1ubuntu1, automatic), 
browser-plugin-gnash:amd64 (0.8.10-5ubuntu1), 
libencode-locale-perl:amd64 (1.02-2, automatic), 
konsole:amd64 (4.8.5-0ubuntu0.1, automatic), 
gnome-games-extra-data:amd64 (3.2.0-0ubuntu1, automatic), 
libkcalutils4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libgoffice-0.8-8:amd64 (0.8.17-1, automatic), 
korganizer:amd64 (4.8.5-0ubuntu0.1, automatic), 
slib:amd64 (3b1-3.1, automatic), 
libhttp-date-perl:amd64 (6.00-1, automatic), 
libsoprano4:amd64 (2.7.5+dfsg.1-0ubuntu1, automatic), 
libmono-system-data4.0-cil:amd64 (2.10.8.1-1ubuntu2.2, automatic), 
akonadi-server:amd64 (1.7.2-0ubuntu1, automatic), 
libmicroblog4:amd64 (4.8.5-0ubuntu0.1, automatic), 
gnucash-docs:amd64 (2.4.1-2, automatic), 
akregator:amd64 (4.8.5-0ubuntu0.1, automatic), 
libkonqsidebarplugin4a:amd64 (4.8.5-0ubuntu0.1, automatic), 
libmailtools-perl:amd64 (2.08-1, automatic), 
libgtkhtml-editor-4.0-0:amd64 (4.2.2-1ubuntu1.2, automatic), 
libattica0.3:amd64 (0.3.0-0ubuntu2, automatic), 
virtuoso-opensource-6.1-common:amd64 (6.1.4+dfsg1-0ubuntu1, automatic), 
liblwp-protocol-https-perl:amd64 (6.02-1, automatic), 
libkdnssd4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libksgrd4:amd64 (4.8.5-0ubuntu0.3, automatic), 
libkparts4:amd64 (4.8.5-0ubuntu0.1, automatic), 
ark:amd64 (4.8.5-0ubuntu0.1, automatic), 
sweeper:amd64 (4.8.2-0ubuntu2, automatic), 
libkpgp4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libqgpgme1:amd64 (4.8.5-0ubuntu0.1, automatic), 
kde-runtime-data:amd64 (4.8.5-0ubuntu0.1, automatic), 
kde-plasma-desktop:amd64 (71~pre15ubuntu12.4, automatic), 
kde-window-manager:amd64 (4.8.5-0ubuntu0.3, automatic), 
libexo-helpers:amd64 (0.6.2-4, automatic), 
gnash-common:amd64 (0.8.10-5ubuntu1, automatic), 
kde-window-manager-common:amd64 (4.8.5-0ubuntu0.3, automatic), 
libclucene0ldbl:amd64 (0.9.21b-2, automatic), 
libqapt1:amd64 (1.3.1-0ubuntu2, automatic), 
libmono-system-web-applicationservices4.0-cil:amd64 (2.10.8.1-1ubuntu2.2, automatic), 
dia-gnome:amd64 (0.97.2-5), 
libtaskmanager4abi3:amd64 (4.8.5-0ubuntu0.3, automatic), 
imagemagick-common:amd64 (6.6.9.7-5ubuntu3.2, automatic), 
libkabc4:amd64 (4.8.5-0ubuntu0.1, automatic), 
shared-desktop-ontologies:amd64 (0.8.1-1, automatic), 
bogofilter-common:amd64 (1.2.2+dfsg1-1ubuntu0.12.04.1, automatic), 
libmono-system-enterpriseservices4.0-cil:amd64 (2.10.8.1-1ubuntu2.2, automatic), 
libhttp-cookies-perl:amd64 (6.00-2, automatic), 
libkdepim4:amd64 (4.8.5-0ubuntu0.1, automatic), 
kdoctools:amd64 (4.8.5-0ubuntu0.1, automatic), 
libhttp-message-perl:amd64 (6.01-1, automatic), 
tumbler-common:amd64 (0.1.24-0ubuntu1, automatic), 
libkactivities6:amd64 (4.8.5-0ubuntu0.1, automatic), 
libmailcommon4:amd64 (4.8.5-0ubuntu0.1, automatic), 
thunar:amd64 (1.2.3-3ubuntu2, automatic), 
libkdecorations4:amd64 (4.8.5-0ubuntu0.3, automatic), 
libqimageblitz4:amd64 (0.0.6-4, automatic), 
libgnome-vfs2.0-cil:amd64 (2.24.2-1, automatic),
 libincidenceeditorsng4:amd64 (4.8.5-0ubuntu0.1, automatic),
 libksieve4:amd64 (4.8.5-0ubuntu0.1, automatic), 
kfind:amd64 (4.8.5-0ubuntu0.1, automatic), 
libnepomukdatamanagement4:amd64 (4.8.5-0ubuntu0.1, automatic), 
mysql-client-core-5.5:amd64 (5.5.31-0ubuntu0.12.04.1, automatic), 
dragonplayer:amd64 (4.8.5-0ubuntu1, automatic), 
libpathplan4:amd64 (2.26.3-10ubuntu1, automatic), 
kde-baseapps-data:amd64 (4.8.5-0ubuntu0.1, automatic), 
kde-wallpapers:amd64 (4.8.3-0ubuntu0.1, automatic), 
libgarcon-common:amd64 (0.1.11-0ubuntu1, automatic), 
plasma-widget-folderview:amd64 (4.8.5-0ubuntu0.1, automatic),
 kde-workspace:amd64 (4.8.5-0ubuntu0.3, automatic), 
kdm:amd64 (4.8.5-0ubuntu0.3, automatic), 
libksba8:amd64 (1.2.0-2, automatic), 
xfwm4:amd64 (4.8.3-1ubuntu1.1, automatic), 
libkdepimdbusinterfaces4:amd64 (4.8.5-0ubuntu0.1, automatic), 
pinentry-qt4:amd64 (0.8.1-1ubuntu1, automatic), 
libnet-http-perl:amd64 (6.02-1, automatic), 
icoutils:amd64 (0.29.1-2, automatic), 
libkidletime4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libgsf-1-114:amd64 (1.14.21-2, automatic), 
katepart:amd64 (4.8.5-0ubuntu0.1, automatic), 
gnupg-agent:amd64 (2.0.17-2ubuntu2.12.04.2, automatic), 
juk:amd64 (4.8.5-0ubuntu1, automatic), 
libreoffice-evolution:amd64 (3.5.7-0ubuntu4), 
libart2.0-cil:amd64 (2.24.2-1, automatic), 
libkunitconversion4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libwebkit1.1-cil:amd64 (0.3-5, automatic), 
libkcmutils4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libkdgantt2:amd64 (4.8.5-0ubuntu0.1, automatic),
 libkcal4:amd64 (4.8.5-0ubuntu0.1, automatic),
 plasma-widgets-addons:amd64 (4.8.5-0ubuntu0.1, automatic), 
knotes:amd64 (4.8.5-0ubuntu0.1, automatic), 
bogofilter:amd64 (1.2.2+dfsg1-1ubuntu0.12.04.1, automatic), 
libntrack0:amd64 (016-1ubuntu1, automatic), 
desktop-base:amd64 (6.0.7ubuntu1, automatic), 
soprano-daemon:amd64 (2.7.5+dfsg.1-0ubuntu1, automatic),
 libkalarmcal2:amd64 (4.8.5-0ubuntu0.1, automatic),
libakonadi-calendar4:amd64 (4.8.5-0ubuntu0.1, automatic),
 libaqhbci20:amd64 (5.0.22-1, automatic), 
libwutil2:amd64 (0.95.0+20111028-4, automatic), 
libkfile4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libkopete4:amd64 (4.8.5-0ubuntu0.2, automatic), 
language-pack-kde-en:amd64 (12.04+20130128, automatic), 
gnome-shell-common:amd64 (3.4.1-0ubuntu2, automatic), 
libgwenhywfar60:amd64 (4.3.1-1, automatic),
 libxfce4util-common:amd64 (4.8.2-1, automatic), 
kde-workspace-kgreet-plugins:amd64 (4.8.5-0ubuntu0.3, automatic), 
libkpty4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libgwenhywfar-data:amd64 (4.3.1-1, automatic), 
libplasmagenericshell4:amd64 (4.8.5-0ubuntu0.3, automatic), 
libthunarx-2-0:amd64 (1.2.3-3ubuntu2, automatic),
 libhtml-format-perl:amd64 (2.10-1, automatic),
 libkimap4:amd64 (4.8.5-0ubuntu0.1, automatic), 
kde-l10n-engb:amd64 (4.8.5-0ubuntu0.1, automatic),
 konqueror:amd64 (4.8.5-0ubuntu0.1, automatic), 
libphonon4:amd64 (4.7.0really4.6.0-0ubuntu1, automatic), 
libgvc5:amd64 (2.26.3-10ubuntu1, automatic),
 libfinance-quote-perl:amd64 (1.17+git20110918-1, automatic), 
libkexiv2-10:amd64 (4.8.5-0ubuntu0.1, automatic), 
libmono-system-web4.0-cil:amd64 (2.10.8.1-1ubuntu2.2, automatic), 
polkit-kde-1:amd64 (0.99.0-3ubuntu5, automatic), 
thunar-data:amd64 (1.2.3-3ubuntu2, automatic), 
libmailtransport4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libgrantlee-core0:amd64 (0.2.0-0ubuntu1, automatic), 
libksignalplotter4:amd64 (4.8.5-0ubuntu0.3, automatic), 
kscreensaver:amd64 (4.8.5-0ubuntu0.1, automatic), 
libwings2:amd64 (0.95.0+20111028-4, automatic), 
libmessageviewer4:amd64 (4.8.5-0ubuntu0.1, automatic),
 libassuan0:amd64 (2.0.2-1ubuntu1, automatic), 
libkntlm4:amd64 (4.8.5-0ubuntu0.1, automatic), 
xfdesktop4:amd64 (4.8.3-2ubuntu7, automatic), 
kinfocenter:amd64 (4.8.5-0ubuntu0.3, automatic), 
libplasma3:amd64 (4.8.5-0ubuntu0.1, automatic), 
libkworkspace4abi1:amd64 (4.8.5-0ubuntu0.3, automatic), 
plasma-dataengines-workspace:amd64 (4.8.5-0ubuntu0.3, automatic), 
kde-wallpapers-default:amd64 (4.8.3-0ubuntu0.1, automatic), 
plasma-widget-lancelot:amd64 (4.8.5-0ubuntu0.1, automatic), 
ksysguardd:amd64 (4.8.5-0ubuntu0.3, automatic), 
libmessagelist4:amd64 (4.8.5-0ubuntu0.1, automatic), 
phonon-backend-gstreamer:amd64 (4.7.0really4.6.2-0ubuntu0.1, automatic), 
libkemoticons4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libkpimtextedit4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libgarcon-1-0:amd64 (0.1.11-0ubuntu1, automatic), 
libgnomeui-common:amd64 (2.24.5-2ubuntu2, automatic), 
libkephal4abi1:amd64 (4.8.5-0ubuntu0.3, automatic), 
plasma-runners-addons:amd64 (4.8.5-0ubuntu0.1, automatic),
 liferea:amd64 (1.8.3-0.1ubuntu2), 
libxfce4util4:amd64 (4.8.2-1, automatic),
 libkscreensaver5:amd64 (4.8.5-0ubuntu0.3, automatic), 
libkmime4:amd64 (4.8.5-0ubuntu0.1, automatic), 
tango-icon-theme:amd64 (0.8.90-5, automatic),
 libsocket6-perl:amd64 (0.23-1build2, automatic),
 wmaker-common:amd64 (0.95.0+20111028-4, automatic),
 ntrack-module-libnl-0:amd64 (016-1ubuntu1, automatic), 
xfce4-appfinder:amd64 (4.8.0-3, automatic), 
kdelibs-bin:amd64 (4.8.5-0ubuntu0.1, automatic),
 gnash:amd64 (0.8.10-5ubuntu1, automatic), 
libkdewebkit5:amd64 (4.8.5-0ubuntu0.1, automatic), 
dia-common:amd64 (0.97.2-5, automatic), 
libexo-1-0:amd64 (0.6.2-4, automatic),
 libksieveui4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libaqbanking33-plugins:amd64 (5.0.22-1, automatic), 
libbonoboui2-0:amd64 (2.24.5-0ubuntu1.1, automatic), 
kdepimlibs-kio-plugins:amd64 (4.8.5-0ubuntu0.1, automatic), 
kde-runtime:amd64 (4.8.5-0ubuntu0.1, automatic), 
libkjsembed4:amd64 (4.8.5-0ubuntu0.1, automatic), 
evolution-rss:amd64 (0.2.90~20111111-3build1), 
gnucash-common:amd64 (2.4.10-1, automatic), 
libxfce4util-bin:amd64 (4.8.2-1, automatic), 
exo-utils:amd64 (0.6.2-4, automatic), 
kde-style-oxygen:amd64 (4.8.5-0ubuntu0.3, automatic), 
libkio5:amd64 (4.8.5-0ubuntu0.1, automatic), 
gpsd:amd64 (3.4-2, automatic), 
libakonadi-kabc4:amd64 (4.8.5-0ubuntu0.1, automatic), 
gtk2-engines-xfce:amd64 (2.8.1-3, automatic),
 libkjsapi4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libstreams0:amd64 (0.7.7-1.1ubuntu3, automatic), 
xfce4-utils:amd64 (4.8.3-1ubuntu2, automatic), 
imagemagick:amd64 (6.6.9.7-5ubuntu3.2, automatic),
 libqalculate5:amd64 (0.9.7-6ubuntu2, automatic), 
libhtml-tagset-perl:amd64 (3.20-2, automatic), 
libprocesscore4abi1:amd64 (4.8.5-0ubuntu0.3, automatic), 
liferea-data:amd64 (1.8.3-0.1ubuntu2, automatic), 
libntrack-qt4-1:amd64 (016-1ubuntu1, automatic), 
kopete:amd64 (4.8.5-0ubuntu0.2, automatic), 
kdelibs5-data:amd64 (4.8.5-0ubuntu0.1, automatic), 
xfce4-session:amd64 (4.8.3-0ubuntu2, automatic), 
libgraph4:amd64 (2.26.3-10ubuntu1, automatic), 
libkpimidentities4:amd64 (4.8.5-0ubuntu0.1, automatic),
 libkpimutils4:amd64 (4.8.5-0ubuntu0.1, automatic), 
planner-doc:amd64 (0.14.5-1ubuntu3, automatic), 
libwww-perl:amd64 (6.03-1, automatic), 
kate:amd64 (4.8.5-0ubuntu0.1, automatic), 
kmail:amd64 (4.8.5-0ubuntu0.1, automatic), 
xfconf:amd64 (4.8.1-1, automatic), 
libwraster3:amd64 (0.95.0+20111028-4, automatic), 
libgsl0ldbl:amd64 (1.15+dfsg-1build1, automatic), 
kscreensaver-xsavers:amd64 (4.8.5-0ubuntu0.1, automatic), 
libktoblzcheck1c2a:amd64 (1.37-1, automatic), 
libaqbanking-plugins-libgwenhywfar60:amd64 (5.0.22-1, automatic), 
marble-data:amd64 (4.8.5-0ubuntu0.2, automatic), 
libsolidcontrolifaces4abi2:amd64 (4.8.5-0ubuntu0.3, automatic), 
libbonoboui2-common:amd64 (2.24.5-0ubuntu1.1, automatic), 
xscreensaver:amd64 (5.15-2ubuntu1, automatic), 
libkde3support4:amd64 (4.8.5-0ubuntu0.1, automatic),
 plasma-desktop:amd64 (4.8.5-0ubuntu0.3, automatic),
 libjpeg-turbo-progs:amd64 (1.1.90+svn733-0ubuntu4.1, automatic), 
libknotifyconfig4:amd64 (4.8.5-0ubuntu0.1, automatic), 
language-pack-kde-en-base:amd64 (12.04+20130128, automatic), 
systemsettings:amd64 (4.8.5-0ubuntu0.3, automatic), 
libaqbanking33:amd64 (5.0.22-1, automatic), 
libio-socket-ssl-perl:amd64 (1.53-1, automatic), 
libmono-data-tds4.0-cil:amd64 (2.10.8.1-1ubuntu2.2, automatic), 
gnome-tweak-tool:amd64 (3.3.4-0ubuntu1), 
kdelibs5-plugins:amd64 (4.8.5-0ubuntu0.1, automatic), 
kdepim-runtime:amd64 (4.8.5-0ubuntu0.1, automatic), 
libprocessui4a:amd64 (4.8.5-0ubuntu0.3, automatic),
libkhtml5:amd64 (4.8.5-0ubuntu0.1, automatic), 
libwww-robotrules-perl:amd64 (6.01-1, automatic), 
libkdeui5:amd64 (4.8.5-0ubuntu0.1, automatic),
 liblwp-mediatypes-perl:amd64 (6.01-1, automatic),
 libakonadi-kcal4:amd64 (4.8.5-0ubuntu0.1, automatic),
 libkdesu5:amd64 (4.8.5-0ubuntu0.1, automatic), 
oxygen-cursor-theme:amd64 (0.0.2010-05-10-kde4.4.3-1ubuntu1, automatic), 
plasma-widget-networkmanagement:amd64 (0.9.0.1-0ubuntu2, automatic), 
xfce4-mixer:amd64 (4.8.0-2ubuntu1, automatic), 
libakonadi-notes4:amd64 (4.8.5-0ubuntu0.1, automatic), 
gnupg2:amd64 (2.0.17-2ubuntu2.12.04.2, automatic), 
libtemplateparser4:amd64 (4.8.5-0ubuntu0.1, automatic), 
okular:amd64 (4.8.5-0ubuntu0.1, automatic), 
libkatepartinterfaces4:amd64 (4.8.5-0ubuntu0.1, automatic), 
plasma-widgets-workspace:amd64 (4.8.5-0ubuntu0.3, automatic), 
libmsn0.3:amd64 (4.2.1-0ubuntu1, automatic), 
libtidy-0.99-0:amd64 (20091223cvs-1ubuntu2, automatic), 
libhtml-tableextract-perl:amd64 (2.11-1, automatic), 
kate-data:amd64 (4.8.5-0ubuntu0.1, automatic), 
libgnomecanvas2-common:amd64 (2.30.3-1ubuntu1.1, automatic), 
libakonadi-contact4:amd64 (4.8.5-0ubuntu0.1, automatic), 
libakonadi-kde4:amd64 (4.8.5-0ubuntu0.1, automatic), 
gsfonts-x11:amd64 (0.22, automatic),
gnome-hearts:amd64 (0.3-2ubuntu5),
 libsolidcontrol4abi2:amd64 (4.8.5-0ubuntu0.3, automatic), 
libgpgme++2:amd64 (4.8.5-0ubuntu0.1, automatic), 
kdepasswd:amd64 (4.8.5-0ubuntu0.1, automatic), 
kmix:amd64 (4.8.5-0ubuntu1, automatic), 
libstreamanalyzer0:amd64 (0.7.7-1.1ubuntu3, automatic),
 libkonq5abi1:amd64 (4.8.5-0ubuntu0.1, automatic), 
libio-socket-inet6-perl:amd64 (2.69-2, automatic), 
libdmtx0a:amd64 (0.7.2-1build2, automatic), 
libkwinglutils1:amd64 (4.8.5-0ubuntu0.3, automatic), 
plasma-widget-message-indicator:amd64 (0.5.8-1ubuntu1, automatic), 
libkwinnvidiahack4:amd64 (4.8.5-0ubuntu0.3, automatic)
End-Date: 2013-05-06  18:13:34
```[/SIZE]
[/SIZE]

---

### Post by abdorefky on 2013-05-06
i tried to purge them all . but it gave me this 
bash: syntax error near unexpected token `('

---

### Post by matt_symes on 2013-05-06
@OP. 

Please use the default font size and please also use code tags.

Use code tags by highlighting the text you want in your post and hitting the # button above where you type your reply.

I have formated your posts above to make them more readable for anybody that may offer you assistance.

---

### Post by abdorefky on 2013-05-06
Thank you, it looks much better now .
Thanks for your effort , and i will use # from now on .

---

### Post by matt_symes on 2013-05-06
Hi

I assume you used the gnome shell PPA to install gnome ?

If so then remove it using ```
ppa-purge
```

```
sudo apt-get install ppa-purge
```

```
sudo ppa-purge <name_of_ppa>
```
> 
i tried to purge them all . but it gave me this 
bash: syntax error near unexpected token `('

What command did you use that produced this error ?

Kind regards

---

### Post by abdorefky on 2013-05-06
allright , but all of this started because i wanted to reinstall gnome :) and tried the software center to install after the uninstall 

now after i purge all installed packages  and the ppa . should i install the gnome from the ppa or software center ?

if the software center made apply for the packages even when gnome not detected as installed , is that mean that when i uninstalled the gnome first time after upgrade 
i didn't removed it correct ? 
if so what is the remove correct for gnome 

ty

---

### Post by matt_symes on 2013-05-07
Hi

> **abdorefky said:**
> now after i purge all installed packages  and the ppa . should i install the gnome from the ppa or software center ?


I believe both should work. I am not currently using gnome shell so i may not be the best to answer this question.

What do others think ?

> if the software center made apply for the packages even when gnome not detected as installed , is that mean that when i uninstalled the gnome first time after upgrade 
i didn't removed it correct ? 
if so what is the remove correct for gnome 

ty

If you installed it from a PPA then the best course of action is to use *ppa-purge *to remove it as removing it using the software center may not remove it correctly.

If you installed it from the software center then it's best to use the software center to remove it.

Kind regards

---


---
title: "Adding Unity desktop"
date: 2016-11-09
forum: Desktop Environments
---

### Post by madtom1999 on 2016-11-09
I'm passing on my old XFCE laptop to a friend who wants to use the unity desktop. I've loaded it but the XFCE login window doesnt offer an alternative destop. How can I fix this?

---

### Post by Frogs Hair on 2016-11-09
What pakage/s did you install ?

---

### Post by ajgreeny on 2016-11-09
You need to run command```
sudo apt-get install ubuntu-desktop
```though there may be other ways which give you unity without all the ubuntu packages.
I will search a bit more on your behalf to see what I can find as it could be useful to me as well.

---

### Post by vasa1 on 2016-11-09
> **ajgreeny said:**
> ...
I will search a bit more on your behalf to see what I can find as it could be useful to me as well.
That will be interesting :)

But assuming OP has successfully installed ubuntu-desktop, it should show up as a dropdown at the time of login if OP clicks the correct icon. Otherwise, the previous session is used by default.

---

### Post by mikodo on 2016-11-09
> **ajgreeny said:**
> You need to run command```
sudo apt-get install ubuntu-desktop
```though there may be other ways which give you unity without all the ubuntu packages.
I will search a bit more on your behalf to see what I can find as it could be useful to me as well.
Well, you would need the 'depends' dependencies for sure I would expect.
 
One could choose from the 'recommended' packages as one would want, I suppose. Remember, the recommended packages are recommend for a reason. Unless one 'knows' they do not need some/all recommends, probably best to install those too.

The 'suggests' packages are just that. Only suggested, and one has more 'latitude' here, in having a well working desktop without them.

See: [http://packages.ubuntu.com/xenial/ubuntu-desktop](http://packages.ubuntu.com/xenial/ubuntu-desktop)

Commands to run to see the differences. *Note, only enter 'Y' if what is downloaded is wanted to be installed. Hit 'N" after looking but choosing to not download:

Compare these:

```
sudo apt-get --install-recommends install ubuntu-desktop

and

sudo apt-get install --no-install-recommends ubuntu-desktop

and

sudo apt-get install --no-install-suggested ubuntu-desktop

```


Here is what I get I 'try' those commands on my Xubuntu 'Xenial' desktop with those commands:

```
mikodo@mikodo:~$ sudo apt-get --install-recommends install ubuntu-desktop
[sudo] password for mikodo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  a11y-profile-manager-indicator account-plugin-facebook account-plugin-flickr
  account-plugin-google activity-log-manager adium-theme-ubuntu aisleriot apg
  appmenu-qt appmenu-qt5 apturl apturl-common bamfdaemon baobab
  branding-ubuntu build-essential checkbox-converged checkbox-gui cheese
  compiz compiz-core compiz-gnome compiz-plugins-default cups-pk-helper
  dconf-cli deja-dup dpkg-dev eog evolution-data-server
  evolution-data-server-online-accounts example-content fakeroot g++ g++-5
  gedit gedit-common geoclue geoclue-ubuntu-geoip gir1.2-accounts-1.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-gdata-0.0 gir1.2-goa-1.0
  gir1.2-gudev-1.0 gir1.2-ibus-1.0 gir1.2-peas-1.0 gir1.2-rb-3.0
  gir1.2-secret-1 gir1.2-signon-1.0 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0
  gir1.2-udisks-2.0 gir1.2-unity-5.0 gkbd-capplet gnome-bluetooth
  gnome-calendar gnome-disk-utility gnome-font-viewer gnome-mahjongg
  gnome-orca gnome-power-manager gnome-screensaver gnome-screenshot
  gnome-session-bin gnome-session-canberra gnome-session-common
  gnome-settings-daemon-schemas gnome-system-log gnome-system-monitor
  gnome-terminal gnome-terminal-data gnome-user-share gnome-video-effects
  grilo-plugins-0.2-base gstreamer1.0-alsa gstreamer1.0-clutter-3.0
  gstreamer1.0-plugins-base-apps gstreamer1.0-tools guile-2.0-libs ibus
  ibus-gtk ibus-gtk3 ibus-table indicator-appmenu indicator-bluetooth
  indicator-datetime indicator-keyboard indicator-power indicator-printers
  indicator-session jayatana liba11y-profile-manager-0.1-0
  liba11y-profile-manager-data libaccount-plugin-1.0-0
  libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-glib0
  libaccounts-qt5-1 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libatk-adaptor libavahi-ui-gtk3-0 libbamf3-2
  libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse libcdr-0.1-1
  libcheese-gtk25 libcompizconfig0 libdbusmenu-qt2 libdecoration0
  libdmapsharing-3.0-2 libecal-1.2-19 libedata-cal-1.2-28
  libedataserverui-1.2-1 libexempi3 libexiv2-14 libfakeroot libfcitx-config4
  libfcitx-gclient0 libfcitx-utils0 libframe6 libfreehand-0.1-1
  libfreerdp-cache1.1 libfreerdp-client1.1 libfreerdp-codec1.1
  libfreerdp-common1.1.0 libfreerdp-core1.1 libfreerdp-crypto1.1
  libfreerdp-gdi1.1 libfreerdp-locale1.1 libfreerdp-plugins-standard
  libfreerdp-primitives1.1 libfreerdp-utils1.1 libgail-3-0 libgail-common
  libgc1c2 libgeis1 libgeocode-glib0 libgeonames0 libgexiv2-2 libglewmx1.13
  libgmime-2.6-0 libgnome-bluetooth13 libgnomekbd-common libgnomekbd8
  libgom-1.0-0 libgom-1.0-common libgpod-common libgpod4 libgrail6
  libgrilo-0.2-1 libgweather-3-6 libgweather-common libibus-1.0-5
  libmediaart-2.0-0 libmetacity-private3a libmspub-0.1-1 libnux-4.0-0
  libnux-4.0-common libpagemaker-0.0-0 libpeas-1.0-0
  libpeas-1.0-0-python3loader libpeas-common libprotobuf9v5
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager
  libpwquality-common libpwquality1 libqt4-sql-sqlite libqt5opengl5
  libqt5printsupport5 libqt5webkit5 libquvi-scripts libquvi7
  libreoffice-avmedia-backend-gstreamer libreoffice-draw libreoffice-gnome
  libreoffice-impress libreoffice-math libreoffice-ogltrans
  libreoffice-pdfimport libreoffice-style-breeze librhythmbox-core9
  libsgutils2-2 libsignon-extension1 libsignon-glib1 libsignon-plugins-common1
  libsignon-qt5-1 libssh-4 libstdc++-5-dev libtelepathy-glib0
  libtimezonemap-data libtimezonemap1 libtotem-plparser-common
  libtotem-plparser18 libtotem0 libtracker-sparql-1.0-0
  libunity-control-center1 libunity-core-6.0-9 libunity-gtk2-parser0
  libunity-gtk3-parser0 libunity-misc4 libunity-settings-daemon1
  libunity-webapps0 libvisio-0.1-1 libvncclient1 libwhoopsie-preferences0
  libwinpr-crt0.1 libwinpr-dsparse0.1 libwinpr-environment0.1 libwinpr-file0.1
  libwinpr-handle0.1 libwinpr-heap0.1 libwinpr-input0.1
  libwinpr-interlocked0.1 libwinpr-library0.1 libwinpr-path0.1
  libwinpr-pool0.1 libwinpr-registry0.1 libwinpr-rpc0.1 libwinpr-sspi0.1
  libwinpr-synch0.1 libwinpr-sysinfo0.1 libwinpr-thread0.1 libwinpr-utils0.1
  libwmf0.2-7-gtk libzeitgeist-1.0-1 libzeitgeist-2.0-0 light-themes
  media-player-info metacity-common mousetweaks mtools nautilus nautilus-data
  nautilus-sendto nautilus-share notify-osd notify-osd-icons nux-tools
  overlay-scrollbar overlay-scrollbar-gtk2 pkg-config
  plainbox-provider-checkbox plainbox-provider-resource-generic
  plainbox-secure-policy plymouth-theme-ubuntu-logo pppconfig pppoeconf
  pulseaudio-module-bluetooth pyotherside python3-blinker python3-brlapi
  python3-cffi-backend python3-checkbox-support python3-cryptography
  python3-feedparser python3-guacamole python3-httplib2 python3-idna
  python3-jinja2 python3-jwt python3-louis python3-mako python3-markupsafe
  python3-oauthlib python3-padme python3-plainbox python3-pyasn1
  python3-pyatspi python3-pyparsing python3-speechd python3-xlsxwriter
  qml-module-io-thp-pyotherside qml-module-ubuntu-onlineaccounts qmlscene
  qtdeclarative5-accounts-plugin qtdeclarative5-dev-tools
  qtdeclarative5-qtquick2-plugin qtdeclarative5-test-plugin remmina
  remmina-common remmina-plugin-rdp remmina-plugin-vnc rhythmbox
  rhythmbox-data rhythmbox-plugin-zeitgeist rhythmbox-plugins seahorse
  session-migration session-shortcuts shotwell shotwell-common
  signon-keyring-extension signon-plugin-oauth2 signon-plugin-password
  signon-ui signon-ui-service signon-ui-x11 signond sni-qt syslinux
  syslinux-common syslinux-legacy thunderbird-gnome-support totem totem-common
  totem-plugins ubuntu-artwork ubuntu-docs ubuntu-session ubuntu-settings
  ubuntu-software ubuntu-sounds ubuntu-system-service ubuntu-touch-sounds
  ubuntu-wallpapers ubuntu-wallpapers-xenial unity
  unity-accessibility-profiles unity-asset-pool unity-control-center
  unity-control-center-faces unity-control-center-signon unity-greeter
  unity-gtk-module-common unity-gtk2-module unity-gtk3-module
  unity-lens-applications unity-lens-files unity-lens-music unity-lens-photos
  unity-lens-video unity-schemas unity-scope-calculator
  unity-scope-chromiumbookmarks unity-scope-colourlovers unity-scope-devhelp
  unity-scope-firefoxbookmarks unity-scope-gdrive unity-scope-home
  unity-scope-manpages unity-scope-openclipart unity-scope-texdoc
  unity-scope-tomboy unity-scope-video-remote unity-scope-virtualbox
  unity-scope-yelp unity-scope-zotero unity-scopes-master-default
  unity-scopes-runner unity-services unity-settings-daemon
  unity-webapps-common unity-webapps-qml unity-webapps-service
  usb-creator-common usb-creator-gtk vino webapp-container
  whoopsie-preferences zeitgeist-core zeitgeist-datahub
Suggested packages:
  gnome-cards-data gnome-video-effects-frei0r deja-dup-backend-cloudfiles
  deja-dup-backend-gvfs deja-dup-backend-s3 duplicity debian-keyring evolution
  evolution-data-server-dbg g++-multilib g++-5-multilib gcc-5-doc
  libstdc++6-5-dbg gedit-plugins apache2-bin libapache2-mod-dnssd
  gnome-video-effects-extra grilo-plugins-0.2-extra ibus-clutter ibus-doc
  ibus-qt4 ibus-table-array30 ibus-table-cangjie ibus-table-cangjie-big
  ibus-table-cangjie3 ibus-table-cangjie5 ibus-table-cantonese
  ibus-table-cantonhk ibus-table-cns11643 ibus-table-compose ibus-table-easy
  ibus-table-easy-big ibus-table-emoji ibus-table-erbi ibus-table-erbi-qs
  ibus-table-ipa-x-sampa ibus-table-jyutping ibus-table-latex ibus-table-quick
  ibus-table-quick-classic ibus-table-quick3 ibus-table-quick5
  ibus-table-rustrad ibus-table-scj6 ibus-table-stroke5 ibus-table-thai
  ibus-table-translit ibus-table-translit-ua ibus-table-viqr ibus-table-wu
  ibus-table-wubi ibus-table-yawerty ibus-table-yong click powerd
  unity-system-compositor exiv2 fcitx freerdp-x11 grilo-plugins-0.2 libqt4-dev
  libreoffice-evolution breeze-icon-theme sg3-utils libstdc++-5-doc floppyd
  brasero tracker gnome-sushi samba bonnie++ bootchart curl fwts git-core
  glmark2 glmark2-es2 nmap obexftp render-bench smartmontools sox stress
  sysstat x11-server-utils xdialog python-blinker-doc python-cryptography-doc
  python3-cryptography-vectors python-jinja2-doc python3-crypto python3-beaker
  python-mako-doc rhythmbox-plugin-cdrecorder gstreamer1.0-plugins-ugly gromit
  ubuntu-wallpapers-karmic ubuntu-wallpapers-lucid ubuntu-wallpapers-maverick
  ubuntu-wallpapers-natty ubuntu-wallpapers-oneiric ubuntu-wallpapers-precise
  ubuntu-wallpapers-quantal ubuntu-wallpapers-raring ubuntu-wallpapers-saucy
  ubuntu-wallpapers-trusty ubuntu-wallpapers-utopic ubuntu-wallpapers-vivid
  ubuntu-wallpapers-wily lightdm-remote-session-freerdp
  lightdm-remote-session-uccsconfigure remote-login-service tomboy
  xul-ext-unity | unity-chromium-extension
  qtdeclarative5-online-accounts-client0.1 qtdeclarative5-ubuntu-content1
  qtdeclarative5-ubuntu-download-manager0.1 vinagre
  qml-module-ubuntu-onlineaccounts-client
The following NEW packages will be installed:
  a11y-profile-manager-indicator account-plugin-facebook account-plugin-flickr
  account-plugin-google activity-log-manager adium-theme-ubuntu aisleriot apg
  appmenu-qt appmenu-qt5 apturl apturl-common bamfdaemon baobab
  branding-ubuntu build-essential checkbox-converged checkbox-gui cheese
  compiz compiz-core compiz-gnome compiz-plugins-default cups-pk-helper
  dconf-cli deja-dup dpkg-dev eog evolution-data-server
  evolution-data-server-online-accounts example-content fakeroot g++ g++-5
  gedit gedit-common geoclue geoclue-ubuntu-geoip gir1.2-accounts-1.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-gdata-0.0 gir1.2-goa-1.0
  gir1.2-gudev-1.0 gir1.2-ibus-1.0 gir1.2-peas-1.0 gir1.2-rb-3.0
  gir1.2-secret-1 gir1.2-signon-1.0 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0
  gir1.2-udisks-2.0 gir1.2-unity-5.0 gkbd-capplet gnome-bluetooth
  gnome-calendar gnome-disk-utility gnome-font-viewer gnome-mahjongg
  gnome-orca gnome-power-manager gnome-screensaver gnome-screenshot
  gnome-session-bin gnome-session-canberra gnome-session-common
  gnome-settings-daemon-schemas gnome-system-log gnome-system-monitor
  gnome-terminal gnome-terminal-data gnome-user-share gnome-video-effects
  grilo-plugins-0.2-base gstreamer1.0-alsa gstreamer1.0-clutter-3.0
  gstreamer1.0-plugins-base-apps gstreamer1.0-tools guile-2.0-libs ibus
  ibus-gtk ibus-gtk3 ibus-table indicator-appmenu indicator-bluetooth
  indicator-datetime indicator-keyboard indicator-power indicator-printers
  indicator-session jayatana liba11y-profile-manager-0.1-0
  liba11y-profile-manager-data libaccount-plugin-1.0-0
  libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-glib0
  libaccounts-qt5-1 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libatk-adaptor libavahi-ui-gtk3-0 libbamf3-2
  libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse libcdr-0.1-1
  libcheese-gtk25 libcompizconfig0 libdbusmenu-qt2 libdecoration0
  libdmapsharing-3.0-2 libecal-1.2-19 libedata-cal-1.2-28
  libedataserverui-1.2-1 libexempi3 libexiv2-14 libfakeroot libfcitx-config4
  libfcitx-gclient0 libfcitx-utils0 libframe6 libfreehand-0.1-1
  libfreerdp-cache1.1 libfreerdp-client1.1 libfreerdp-codec1.1
  libfreerdp-common1.1.0 libfreerdp-core1.1 libfreerdp-crypto1.1
  libfreerdp-gdi1.1 libfreerdp-locale1.1 libfreerdp-plugins-standard
  libfreerdp-primitives1.1 libfreerdp-utils1.1 libgail-3-0 libgail-common
  libgc1c2 libgeis1 libgeocode-glib0 libgeonames0 libgexiv2-2 libglewmx1.13
  libgmime-2.6-0 libgnome-bluetooth13 libgnomekbd-common libgnomekbd8
  libgom-1.0-0 libgom-1.0-common libgpod-common libgpod4 libgrail6
  libgrilo-0.2-1 libgweather-3-6 libgweather-common libibus-1.0-5
  libmediaart-2.0-0 libmetacity-private3a libmspub-0.1-1 libnux-4.0-0
  libnux-4.0-common libpagemaker-0.0-0 libpeas-1.0-0
  libpeas-1.0-0-python3loader libpeas-common libprotobuf9v5
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager
  libpwquality-common libpwquality1 libqt4-sql-sqlite libqt5opengl5
  libqt5printsupport5 libqt5webkit5 libquvi-scripts libquvi7
  libreoffice-avmedia-backend-gstreamer libreoffice-draw libreoffice-gnome
  libreoffice-impress libreoffice-math libreoffice-ogltrans
  libreoffice-pdfimport libreoffice-style-breeze librhythmbox-core9
  libsgutils2-2 libsignon-extension1 libsignon-glib1 libsignon-plugins-common1
  libsignon-qt5-1 libssh-4 libstdc++-5-dev libtelepathy-glib0
  libtimezonemap-data libtimezonemap1 libtotem-plparser-common
  libtotem-plparser18 libtotem0 libtracker-sparql-1.0-0
  libunity-control-center1 libunity-core-6.0-9 libunity-gtk2-parser0
  libunity-gtk3-parser0 libunity-misc4 libunity-settings-daemon1
  libunity-webapps0 libvisio-0.1-1 libvncclient1 libwhoopsie-preferences0
  libwinpr-crt0.1 libwinpr-dsparse0.1 libwinpr-environment0.1 libwinpr-file0.1
  libwinpr-handle0.1 libwinpr-heap0.1 libwinpr-input0.1
  libwinpr-interlocked0.1 libwinpr-library0.1 libwinpr-path0.1
  libwinpr-pool0.1 libwinpr-registry0.1 libwinpr-rpc0.1 libwinpr-sspi0.1
  libwinpr-synch0.1 libwinpr-sysinfo0.1 libwinpr-thread0.1 libwinpr-utils0.1
  libwmf0.2-7-gtk libzeitgeist-1.0-1 libzeitgeist-2.0-0 light-themes
  media-player-info metacity-common mousetweaks mtools nautilus nautilus-data
  nautilus-sendto nautilus-share notify-osd notify-osd-icons nux-tools
  overlay-scrollbar overlay-scrollbar-gtk2 pkg-config
  plainbox-provider-checkbox plainbox-provider-resource-generic
  plainbox-secure-policy plymouth-theme-ubuntu-logo pppconfig pppoeconf
  pulseaudio-module-bluetooth pyotherside python3-blinker python3-brlapi
  python3-cffi-backend python3-checkbox-support python3-cryptography
  python3-feedparser python3-guacamole python3-httplib2 python3-idna
  python3-jinja2 python3-jwt python3-louis python3-mako python3-markupsafe
  python3-oauthlib python3-padme python3-plainbox python3-pyasn1
  python3-pyatspi python3-pyparsing python3-speechd python3-xlsxwriter
  qml-module-io-thp-pyotherside qml-module-ubuntu-onlineaccounts qmlscene
  qtdeclarative5-accounts-plugin qtdeclarative5-dev-tools
  qtdeclarative5-qtquick2-plugin qtdeclarative5-test-plugin remmina
  remmina-common remmina-plugin-rdp remmina-plugin-vnc rhythmbox
  rhythmbox-data rhythmbox-plugin-zeitgeist rhythmbox-plugins seahorse
  session-migration session-shortcuts shotwell shotwell-common
  signon-keyring-extension signon-plugin-oauth2 signon-plugin-password
  signon-ui signon-ui-service signon-ui-x11 signond sni-qt syslinux
  syslinux-common syslinux-legacy thunderbird-gnome-support totem totem-common
  totem-plugins ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-session
  ubuntu-settings ubuntu-software ubuntu-sounds ubuntu-system-service
  ubuntu-touch-sounds ubuntu-wallpapers ubuntu-wallpapers-xenial unity
  unity-accessibility-profiles unity-asset-pool unity-control-center
  unity-control-center-faces unity-control-center-signon unity-greeter
  unity-gtk-module-common unity-gtk2-module unity-gtk3-module
  unity-lens-applications unity-lens-files unity-lens-music unity-lens-photos
  unity-lens-video unity-schemas unity-scope-calculator
  unity-scope-chromiumbookmarks unity-scope-colourlovers unity-scope-devhelp
  unity-scope-firefoxbookmarks unity-scope-gdrive unity-scope-home
  unity-scope-manpages unity-scope-openclipart unity-scope-texdoc
  unity-scope-tomboy unity-scope-video-remote unity-scope-virtualbox
  unity-scope-yelp unity-scope-zotero unity-scopes-master-default
  unity-scopes-runner unity-services unity-settings-daemon
  unity-webapps-common unity-webapps-qml unity-webapps-service
  usb-creator-common usb-creator-gtk vino webapp-container
  whoopsie-preferences zeitgeist-core zeitgeist-datahub
0 upgraded, 366 newly installed, 0 to remove and 0 not upgraded.
Need to get 109 MB of archives.
After this operation, 419 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
mikodo@mikodo:~$ 
mikodo@mikodo:~$ sudo apt-get install --no-install-recommends ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  adium-theme-ubuntu apg bamfdaemon checkbox-converged checkbox-gui compiz
  compiz-core compiz-gnome compiz-plugins-default dconf-cli dpkg-dev
  gir1.2-gudev-1.0 gir1.2-ibus-1.0 gkbd-capplet gnome-bluetooth
  gnome-session-bin gnome-session-canberra gnome-session-common
  gnome-settings-daemon-schemas gstreamer1.0-alsa gstreamer1.0-clutter-3.0
  gstreamer1.0-plugins-base-apps gstreamer1.0-tools ibus indicator-bluetooth
  indicator-datetime indicator-keyboard indicator-power libatk-adaptor
  libbamf3-2 libcanberra-gtk0 libcheese-gtk25 libcompizconfig0 libdecoration0
  libecal-1.2-19 libexempi3 libfcitx-config4 libfcitx-gclient0 libfcitx-utils0
  libframe6 libgail-3-0 libgail-common libgeis1 libgeonames0 libglewmx1.13
  libgnome-bluetooth13 libgnomekbd-common libgnomekbd8 libgrail6 libibus-1.0-5
  libmediaart-2.0-0 libmetacity-private3a libnux-4.0-0 libnux-4.0-common
  libprotobuf9v5 libpwquality-common libpwquality1 libtimezonemap-data
  libtimezonemap1 libtracker-sparql-1.0-0 libunity-control-center1
  libunity-core-6.0-9 libunity-misc4 libunity-settings-daemon1
  libzeitgeist-2.0-0 light-themes metacity-common nautilus nautilus-data
  notify-osd nux-tools pkg-config plainbox-provider-checkbox
  plainbox-provider-resource-generic plainbox-secure-policy pyotherside
  python3-checkbox-support python3-guacamole python3-jinja2 python3-markupsafe
  python3-padme python3-plainbox python3-pyparsing python3-xlsxwriter
  qml-module-io-thp-pyotherside qmlscene qtdeclarative5-dev-tools
  qtdeclarative5-test-plugin session-migration ubuntu-artwork ubuntu-session
  ubuntu-settings ubuntu-sounds ubuntu-wallpapers ubuntu-wallpapers-xenial
  unity unity-asset-pool unity-control-center unity-greeter unity-schemas
  unity-scope-home unity-scopes-master-default unity-services
  unity-settings-daemon
Suggested packages:
  debian-keyring ibus-clutter ibus-doc ibus-qt4 click powerd
  unity-system-compositor fcitx brasero eog totem | mp3-decoder tracker
  gnome-sushi bonnie++ bootchart curl fwts git-core glmark2 glmark2-es2 nmap
  obexftp render-bench smartmontools sox stress sysstat x11-server-utils
  python-jinja2-doc ubuntu-wallpapers-karmic ubuntu-wallpapers-lucid
  ubuntu-wallpapers-maverick ubuntu-wallpapers-natty ubuntu-wallpapers-oneiric
  ubuntu-wallpapers-precise ubuntu-wallpapers-quantal ubuntu-wallpapers-raring
  ubuntu-wallpapers-saucy ubuntu-wallpapers-trusty ubuntu-wallpapers-utopic
  ubuntu-wallpapers-vivid ubuntu-wallpapers-wily gnome-screensaver
  | xscreensaver libcanberra-gtk-module lightdm-remote-session-freerdp
  lightdm-remote-session-uccsconfigure remote-login-service gnome-screensaver
Recommended packages:
  gnome-system-monitor | mate-system-monitor build-essential fakeroot
  libalgorithm-merge-perl gnome-user-share libcanberra-pulse
  evolution-data-server geoclue-ubuntu-geoip | geoclue-provider
  ubuntu-touch-sounds libcanberra-gtk-module zeitgeist-core | zeitgeist
  notify-osd-icons a11y-profile-manager-indicator activity-log-manager
  aisleriot baobab branding-ubuntu cheese deja-dup eog example-content gedit
  gnome-calendar gnome-disk-utility gnome-font-viewer gnome-mahjongg
  gnome-orca gnome-power-manager gnome-screensaver gnome-screenshot
  gnome-system-log gnome-system-monitor gnome-terminal ibus-gtk ibus-gtk3
  ibus-table libproxy1-plugin-gsettings libproxy1-plugin-networkmanager
  libqt4-sql-sqlite libreoffice-gnome libreoffice-impress libreoffice-math
  libreoffice-ogltrans libreoffice-pdfimport libreoffice-style-breeze
  libwmf0.2-7-gtk mousetweaks nautilus-sendto nautilus-share
  overlay-scrollbar-gtk2 plymouth-theme-ubuntu-logo pppconfig pppoeconf
  pulseaudio-module-bluetooth remmina rhythmbox seahorse shotwell sni-qt
  thunderbird-gnome-support totem ubuntu-docs ubuntu-software
  unity-accessibility-profiles unity-webapps-common usb-creator-gtk vino
  zeitgeist-core zeitgeist-datahub unity-lens-video unity-scope-texdoc
  unity-scope-manpages unity-lens-files unity-scope-zotero
  unity-scope-colourlovers unity-scope-firefoxbookmarks unity-lens-photos
  unity-scope-chromiumbookmarks unity-lens-music unity-scope-virtualbox
  unity-scope-yelp unity-scope-tomboy unity-scope-devhelp
  unity-scope-openclipart unity-scope-calculator unity-lens-applications
  unity-scope-gdrive unity-scope-video-remote indicator-appmenu
  indicator-printers indicator-session session-shortcuts cups-pk-helper
  ubuntu-system-service unity-control-center-faces
The following NEW packages will be installed:
  adium-theme-ubuntu apg bamfdaemon checkbox-converged checkbox-gui compiz
  compiz-core compiz-gnome compiz-plugins-default dconf-cli dpkg-dev
  gir1.2-gudev-1.0 gir1.2-ibus-1.0 gkbd-capplet gnome-bluetooth
  gnome-session-bin gnome-session-canberra gnome-session-common
  gnome-settings-daemon-schemas gstreamer1.0-alsa gstreamer1.0-clutter-3.0
  gstreamer1.0-plugins-base-apps gstreamer1.0-tools ibus indicator-bluetooth
  indicator-datetime indicator-keyboard indicator-power libatk-adaptor
  libbamf3-2 libcanberra-gtk0 libcheese-gtk25 libcompizconfig0 libdecoration0
  libecal-1.2-19 libexempi3 libfcitx-config4 libfcitx-gclient0 libfcitx-utils0
  libframe6 libgail-3-0 libgail-common libgeis1 libgeonames0 libglewmx1.13
  libgnome-bluetooth13 libgnomekbd-common libgnomekbd8 libgrail6 libibus-1.0-5
  libmediaart-2.0-0 libmetacity-private3a libnux-4.0-0 libnux-4.0-common
  libprotobuf9v5 libpwquality-common libpwquality1 libtimezonemap-data
  libtimezonemap1 libtracker-sparql-1.0-0 libunity-control-center1
  libunity-core-6.0-9 libunity-misc4 libunity-settings-daemon1
  libzeitgeist-2.0-0 light-themes metacity-common nautilus nautilus-data
  notify-osd nux-tools pkg-config plainbox-provider-checkbox
  plainbox-provider-resource-generic plainbox-secure-policy pyotherside
  python3-checkbox-support python3-guacamole python3-jinja2 python3-markupsafe
  python3-padme python3-plainbox python3-pyparsing python3-xlsxwriter
  qml-module-io-thp-pyotherside qmlscene qtdeclarative5-dev-tools
  qtdeclarative5-test-plugin session-migration ubuntu-artwork ubuntu-desktop
  ubuntu-session ubuntu-settings ubuntu-sounds ubuntu-wallpapers
  ubuntu-wallpapers-xenial unity unity-asset-pool unity-control-center
  unity-greeter unity-schemas unity-scope-home unity-scopes-master-default
  unity-services unity-settings-daemon
0 upgraded, 105 newly installed, 0 to remove and 0 not upgraded.
Need to get 37.0 MB of archives.
After this operation, 103 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

sudo apt-get install --no-install-suggests ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  a11y-profile-manager-indicator account-plugin-facebook account-plugin-flickr
  account-plugin-google activity-log-manager adium-theme-ubuntu aisleriot apg
  appmenu-qt appmenu-qt5 apturl apturl-common bamfdaemon baobab
  branding-ubuntu build-essential checkbox-converged checkbox-gui cheese
  compiz compiz-core compiz-gnome compiz-plugins-default cups-pk-helper
  dconf-cli deja-dup dpkg-dev eog evolution-data-server
  evolution-data-server-online-accounts example-content fakeroot g++ g++-5
  gedit gedit-common geoclue geoclue-ubuntu-geoip gir1.2-accounts-1.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-gdata-0.0 gir1.2-goa-1.0
  gir1.2-gudev-1.0 gir1.2-ibus-1.0 gir1.2-peas-1.0 gir1.2-rb-3.0
  gir1.2-secret-1 gir1.2-signon-1.0 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0
  gir1.2-udisks-2.0 gir1.2-unity-5.0 gkbd-capplet gnome-bluetooth
  gnome-calendar gnome-disk-utility gnome-font-viewer gnome-mahjongg
  gnome-orca gnome-power-manager gnome-screensaver gnome-screenshot
  gnome-session-bin gnome-session-canberra gnome-session-common
  gnome-settings-daemon-schemas gnome-system-log gnome-system-monitor
  gnome-terminal gnome-terminal-data gnome-user-share gnome-video-effects
  grilo-plugins-0.2-base gstreamer1.0-alsa gstreamer1.0-clutter-3.0
  gstreamer1.0-plugins-base-apps gstreamer1.0-tools guile-2.0-libs ibus
  ibus-gtk ibus-gtk3 ibus-table indicator-appmenu indicator-bluetooth
  indicator-datetime indicator-keyboard indicator-power indicator-printers
  indicator-session jayatana liba11y-profile-manager-0.1-0
  liba11y-profile-manager-data libaccount-plugin-1.0-0
  libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-glib0
  libaccounts-qt5-1 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libatk-adaptor libavahi-ui-gtk3-0 libbamf3-2
  libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse libcdr-0.1-1
  libcheese-gtk25 libcompizconfig0 libdbusmenu-qt2 libdecoration0
  libdmapsharing-3.0-2 libecal-1.2-19 libedata-cal-1.2-28
  libedataserverui-1.2-1 libexempi3 libexiv2-14 libfakeroot libfcitx-config4
  libfcitx-gclient0 libfcitx-utils0 libframe6 libfreehand-0.1-1
  libfreerdp-cache1.1 libfreerdp-client1.1 libfreerdp-codec1.1
  libfreerdp-common1.1.0 libfreerdp-core1.1 libfreerdp-crypto1.1
  libfreerdp-gdi1.1 libfreerdp-locale1.1 libfreerdp-plugins-standard
  libfreerdp-primitives1.1 libfreerdp-utils1.1 libgail-3-0 libgail-common
  libgc1c2 libgeis1 libgeocode-glib0 libgeonames0 libgexiv2-2 libglewmx1.13
  libgmime-2.6-0 libgnome-bluetooth13 libgnomekbd-common libgnomekbd8
  libgom-1.0-0 libgom-1.0-common libgpod-common libgpod4 libgrail6
  libgrilo-0.2-1 libgweather-3-6 libgweather-common libibus-1.0-5
  libmediaart-2.0-0 libmetacity-private3a libmspub-0.1-1 libnux-4.0-0
  libnux-4.0-common libpagemaker-0.0-0 libpeas-1.0-0
  libpeas-1.0-0-python3loader libpeas-common libprotobuf9v5
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager
  libpwquality-common libpwquality1 libqt4-sql-sqlite libqt5opengl5
  libqt5printsupport5 libqt5webkit5 libquvi-scripts libquvi7
  libreoffice-avmedia-backend-gstreamer libreoffice-draw libreoffice-gnome
  libreoffice-impress libreoffice-math libreoffice-ogltrans
  libreoffice-pdfimport libreoffice-style-breeze librhythmbox-core9
  libsgutils2-2 libsignon-extension1 libsignon-glib1 libsignon-plugins-common1
  libsignon-qt5-1 libssh-4 libstdc++-5-dev libtelepathy-glib0
  libtimezonemap-data libtimezonemap1 libtotem-plparser-common
  libtotem-plparser18 libtotem0 libtracker-sparql-1.0-0
  libunity-control-center1 libunity-core-6.0-9 libunity-gtk2-parser0
  libunity-gtk3-parser0 libunity-misc4 libunity-settings-daemon1
  libunity-webapps0 libvisio-0.1-1 libvncclient1 libwhoopsie-preferences0
  libwinpr-crt0.1 libwinpr-dsparse0.1 libwinpr-environment0.1 libwinpr-file0.1
  libwinpr-handle0.1 libwinpr-heap0.1 libwinpr-input0.1
  libwinpr-interlocked0.1 libwinpr-library0.1 libwinpr-path0.1
  libwinpr-pool0.1 libwinpr-registry0.1 libwinpr-rpc0.1 libwinpr-sspi0.1
  libwinpr-synch0.1 libwinpr-sysinfo0.1 libwinpr-thread0.1 libwinpr-utils0.1
  libwmf0.2-7-gtk libzeitgeist-1.0-1 libzeitgeist-2.0-0 light-themes
  media-player-info metacity-common mousetweaks mtools nautilus nautilus-data
  nautilus-sendto nautilus-share notify-osd notify-osd-icons nux-tools
  overlay-scrollbar overlay-scrollbar-gtk2 pkg-config
  plainbox-provider-checkbox plainbox-provider-resource-generic
  plainbox-secure-policy plymouth-theme-ubuntu-logo pppconfig pppoeconf
  pulseaudio-module-bluetooth pyotherside python3-blinker python3-brlapi
  python3-cffi-backend python3-checkbox-support python3-cryptography
  python3-feedparser python3-guacamole python3-httplib2 python3-idna
  python3-jinja2 python3-jwt python3-louis python3-mako python3-markupsafe
  python3-oauthlib python3-padme python3-plainbox python3-pyasn1
  python3-pyatspi python3-pyparsing python3-speechd python3-xlsxwriter
  qml-module-io-thp-pyotherside qml-module-ubuntu-onlineaccounts qmlscene
  qtdeclarative5-accounts-plugin qtdeclarative5-dev-tools
  qtdeclarative5-qtquick2-plugin qtdeclarative5-test-plugin remmina
  remmina-common remmina-plugin-rdp remmina-plugin-vnc rhythmbox
  rhythmbox-data rhythmbox-plugin-zeitgeist rhythmbox-plugins seahorse
  session-migration session-shortcuts shotwell shotwell-common
  signon-keyring-extension signon-plugin-oauth2 signon-plugin-password
  signon-ui signon-ui-service signon-ui-x11 signond sni-qt syslinux
  syslinux-common syslinux-legacy thunderbird-gnome-support totem totem-common
  totem-plugins ubuntu-artwork ubuntu-docs ubuntu-session ubuntu-settings
  ubuntu-software ubuntu-sounds ubuntu-system-service ubuntu-touch-sounds
  ubuntu-wallpapers ubuntu-wallpapers-xenial unity
  unity-accessibility-profiles unity-asset-pool unity-control-center
  unity-control-center-faces unity-control-center-signon unity-greeter
  unity-gtk-module-common unity-gtk2-module unity-gtk3-module
  unity-lens-applications unity-lens-files unity-lens-music unity-lens-photos
  unity-lens-video unity-schemas unity-scope-calculator
  unity-scope-chromiumbookmarks unity-scope-colourlovers unity-scope-devhelp
  unity-scope-firefoxbookmarks unity-scope-gdrive unity-scope-home
  unity-scope-manpages unity-scope-openclipart unity-scope-texdoc
  unity-scope-tomboy unity-scope-video-remote unity-scope-virtualbox
  unity-scope-yelp unity-scope-zotero unity-scopes-master-default
  unity-scopes-runner unity-services unity-settings-daemon
  unity-webapps-common unity-webapps-qml unity-webapps-service
  usb-creator-common usb-creator-gtk vino webapp-container
  whoopsie-preferences zeitgeist-core zeitgeist-datahub
Suggested packages:
  gnome-cards-data gnome-video-effects-frei0r deja-dup-backend-cloudfiles
  deja-dup-backend-gvfs deja-dup-backend-s3 duplicity debian-keyring evolution
  evolution-data-server-dbg g++-multilib g++-5-multilib gcc-5-doc
  libstdc++6-5-dbg gedit-plugins apache2-bin libapache2-mod-dnssd
  gnome-video-effects-extra grilo-plugins-0.2-extra ibus-clutter ibus-doc
  ibus-qt4 ibus-table-array30 ibus-table-cangjie ibus-table-cangjie-big
  ibus-table-cangjie3 ibus-table-cangjie5 ibus-table-cantonese
  ibus-table-cantonhk ibus-table-cns11643 ibus-table-compose ibus-table-easy
  ibus-table-easy-big ibus-table-emoji ibus-table-erbi ibus-table-erbi-qs
  ibus-table-ipa-x-sampa ibus-table-jyutping ibus-table-latex ibus-table-quick
  ibus-table-quick-classic ibus-table-quick3 ibus-table-quick5
  ibus-table-rustrad ibus-table-scj6 ibus-table-stroke5 ibus-table-thai
  ibus-table-translit ibus-table-translit-ua ibus-table-viqr ibus-table-wu
  ibus-table-wubi ibus-table-yawerty ibus-table-yong click powerd
  unity-system-compositor exiv2 fcitx freerdp-x11 grilo-plugins-0.2 libqt4-dev
  libreoffice-evolution breeze-icon-theme sg3-utils libstdc++-5-doc floppyd
  brasero tracker gnome-sushi samba bonnie++ bootchart curl fwts git-core
  glmark2 glmark2-es2 nmap obexftp render-bench smartmontools sox stress
  sysstat x11-server-utils xdialog python-blinker-doc python-cryptography-doc
  python3-cryptography-vectors python-jinja2-doc python3-crypto python3-beaker
  python-mako-doc rhythmbox-plugin-cdrecorder gstreamer1.0-plugins-ugly gromit
  ubuntu-wallpapers-karmic ubuntu-wallpapers-lucid ubuntu-wallpapers-maverick
  ubuntu-wallpapers-natty ubuntu-wallpapers-oneiric ubuntu-wallpapers-precise
  ubuntu-wallpapers-quantal ubuntu-wallpapers-raring ubuntu-wallpapers-saucy
  ubuntu-wallpapers-trusty ubuntu-wallpapers-utopic ubuntu-wallpapers-vivid
  ubuntu-wallpapers-wily lightdm-remote-session-freerdp
  lightdm-remote-session-uccsconfigure remote-login-service tomboy
  xul-ext-unity | unity-chromium-extension
  qtdeclarative5-online-accounts-client0.1 qtdeclarative5-ubuntu-content1
  qtdeclarative5-ubuntu-download-manager0.1 vinagre
  qml-module-ubuntu-onlineaccounts-client
The following NEW packages will be installed:
  a11y-profile-manager-indicator account-plugin-facebook account-plugin-flickr
  account-plugin-google activity-log-manager adium-theme-ubuntu aisleriot apg
  appmenu-qt appmenu-qt5 apturl apturl-common bamfdaemon baobab
  branding-ubuntu build-essential checkbox-converged checkbox-gui cheese
  compiz compiz-core compiz-gnome compiz-plugins-default cups-pk-helper
  dconf-cli deja-dup dpkg-dev eog evolution-data-server
  evolution-data-server-online-accounts example-content fakeroot g++ g++-5
  gedit gedit-common geoclue geoclue-ubuntu-geoip gir1.2-accounts-1.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-gdata-0.0 gir1.2-goa-1.0
  gir1.2-gudev-1.0 gir1.2-ibus-1.0 gir1.2-peas-1.0 gir1.2-rb-3.0
  gir1.2-secret-1 gir1.2-signon-1.0 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0
  gir1.2-udisks-2.0 gir1.2-unity-5.0 gkbd-capplet gnome-bluetooth
  gnome-calendar gnome-disk-utility gnome-font-viewer gnome-mahjongg
  gnome-orca gnome-power-manager gnome-screensaver gnome-screenshot
  gnome-session-bin gnome-session-canberra gnome-session-common
  gnome-settings-daemon-schemas gnome-system-log gnome-system-monitor
  gnome-terminal gnome-terminal-data gnome-user-share gnome-video-effects
  grilo-plugins-0.2-base gstreamer1.0-alsa gstreamer1.0-clutter-3.0
  gstreamer1.0-plugins-base-apps gstreamer1.0-tools guile-2.0-libs ibus
  ibus-gtk ibus-gtk3 ibus-table indicator-appmenu indicator-bluetooth
  indicator-datetime indicator-keyboard indicator-power indicator-printers
  indicator-session jayatana liba11y-profile-manager-0.1-0
  liba11y-profile-manager-data libaccount-plugin-1.0-0
  libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-glib0
  libaccounts-qt5-1 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libatk-adaptor libavahi-ui-gtk3-0 libbamf3-2
  libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse libcdr-0.1-1
  libcheese-gtk25 libcompizconfig0 libdbusmenu-qt2 libdecoration0
  libdmapsharing-3.0-2 libecal-1.2-19 libedata-cal-1.2-28
  libedataserverui-1.2-1 libexempi3 libexiv2-14 libfakeroot libfcitx-config4
  libfcitx-gclient0 libfcitx-utils0 libframe6 libfreehand-0.1-1
  libfreerdp-cache1.1 libfreerdp-client1.1 libfreerdp-codec1.1
  libfreerdp-common1.1.0 libfreerdp-core1.1 libfreerdp-crypto1.1
  libfreerdp-gdi1.1 libfreerdp-locale1.1 libfreerdp-plugins-standard
  libfreerdp-primitives1.1 libfreerdp-utils1.1 libgail-3-0 libgail-common
  libgc1c2 libgeis1 libgeocode-glib0 libgeonames0 libgexiv2-2 libglewmx1.13
  libgmime-2.6-0 libgnome-bluetooth13 libgnomekbd-common libgnomekbd8
  libgom-1.0-0 libgom-1.0-common libgpod-common libgpod4 libgrail6
  libgrilo-0.2-1 libgweather-3-6 libgweather-common libibus-1.0-5
  libmediaart-2.0-0 libmetacity-private3a libmspub-0.1-1 libnux-4.0-0
  libnux-4.0-common libpagemaker-0.0-0 libpeas-1.0-0
  libpeas-1.0-0-python3loader libpeas-common libprotobuf9v5
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager
  libpwquality-common libpwquality1 libqt4-sql-sqlite libqt5opengl5
  libqt5printsupport5 libqt5webkit5 libquvi-scripts libquvi7
  libreoffice-avmedia-backend-gstreamer libreoffice-draw libreoffice-gnome
  libreoffice-impress libreoffice-math libreoffice-ogltrans
  libreoffice-pdfimport libreoffice-style-breeze librhythmbox-core9
  libsgutils2-2 libsignon-extension1 libsignon-glib1 libsignon-plugins-common1
  libsignon-qt5-1 libssh-4 libstdc++-5-dev libtelepathy-glib0
  libtimezonemap-data libtimezonemap1 libtotem-plparser-common
  libtotem-plparser18 libtotem0 libtracker-sparql-1.0-0
  libunity-control-center1 libunity-core-6.0-9 libunity-gtk2-parser0
  libunity-gtk3-parser0 libunity-misc4 libunity-settings-daemon1
  libunity-webapps0 libvisio-0.1-1 libvncclient1 libwhoopsie-preferences0
  libwinpr-crt0.1 libwinpr-dsparse0.1 libwinpr-environment0.1 libwinpr-file0.1
  libwinpr-handle0.1 libwinpr-heap0.1 libwinpr-input0.1
  libwinpr-interlocked0.1 libwinpr-library0.1 libwinpr-path0.1
  libwinpr-pool0.1 libwinpr-registry0.1 libwinpr-rpc0.1 libwinpr-sspi0.1
  libwinpr-synch0.1 libwinpr-sysinfo0.1 libwinpr-thread0.1 libwinpr-utils0.1
  libwmf0.2-7-gtk libzeitgeist-1.0-1 libzeitgeist-2.0-0 light-themes
  media-player-info metacity-common mousetweaks mtools nautilus nautilus-data
  nautilus-sendto nautilus-share notify-osd notify-osd-icons nux-tools
  overlay-scrollbar overlay-scrollbar-gtk2 pkg-config
  plainbox-provider-checkbox plainbox-provider-resource-generic
  plainbox-secure-policy plymouth-theme-ubuntu-logo pppconfig pppoeconf
  pulseaudio-module-bluetooth pyotherside python3-blinker python3-brlapi
  python3-cffi-backend python3-checkbox-support python3-cryptography
  python3-feedparser python3-guacamole python3-httplib2 python3-idna
  python3-jinja2 python3-jwt python3-louis python3-mako python3-markupsafe
  python3-oauthlib python3-padme python3-plainbox python3-pyasn1
  python3-pyatspi python3-pyparsing python3-speechd python3-xlsxwriter
  qml-module-io-thp-pyotherside qml-module-ubuntu-onlineaccounts qmlscene
  qtdeclarative5-accounts-plugin qtdeclarative5-dev-tools
  qtdeclarative5-qtquick2-plugin qtdeclarative5-test-plugin remmina
  remmina-common remmina-plugin-rdp remmina-plugin-vnc rhythmbox
  rhythmbox-data rhythmbox-plugin-zeitgeist rhythmbox-plugins seahorse
  session-migration session-shortcuts shotwell shotwell-common
  signon-keyring-extension signon-plugin-oauth2 signon-plugin-password
  signon-ui signon-ui-service signon-ui-x11 signond sni-qt syslinux
  syslinux-common syslinux-legacy thunderbird-gnome-support totem totem-common
  totem-plugins ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-session
  ubuntu-settings ubuntu-software ubuntu-sounds ubuntu-system-service
  ubuntu-touch-sounds ubuntu-wallpapers ubuntu-wallpapers-xenial unity
  unity-accessibility-profiles unity-asset-pool unity-control-center
  unity-control-center-faces unity-control-center-signon unity-greeter
  unity-gtk-module-common unity-gtk2-module unity-gtk3-module
  unity-lens-applications unity-lens-files unity-lens-music unity-lens-photos
  unity-lens-video unity-schemas unity-scope-calculator
  unity-scope-chromiumbookmarks unity-scope-colourlovers unity-scope-devhelp
  unity-scope-firefoxbookmarks unity-scope-gdrive unity-scope-home
  unity-scope-manpages unity-scope-openclipart unity-scope-texdoc
  unity-scope-tomboy unity-scope-video-remote unity-scope-virtualbox
  unity-scope-yelp unity-scope-zotero unity-scopes-master-default
  unity-scopes-runner unity-services unity-settings-daemon
  unity-webapps-common unity-webapps-qml unity-webapps-service
  usb-creator-common usb-creator-gtk vino webapp-container
  whoopsie-preferences zeitgeist-core zeitgeist-datahub
0 upgraded, 366 newly installed, 0 to remove and 0 not upgraded.
Need to get 109 MB of archives.
After this operation, 419 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

mikodo@mikodo:~$




```

---

### Post by madtom1999 on 2016-11-10
oops - on the only other machine I've used with Unity on it the log-in box had the desktop-switcher as an option on the log-in box! I've just found the button on the top panel and all is ok now
Thanks for your help!

---

### Post by ajgreeny on 2016-11-11
Great! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction, even though it looks as if it was perhaps solved already before creating this thread.

It is a great help to users searching the forum to see solutions marked.

---


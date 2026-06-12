---
title: "Converting Ubuntu to Ubuntu GNOME?"
date: 2014-05-04
forum: Desktop Environments
---

### Post by kansasnoob on 2014-05-04
**Update**: [My solution is in post #14]("http://ubuntuforums.org/showthread.php?t=2222046&page=2&p=13017699#post13017699"), just remember that **there is no guarantee that what worked for me will work for you!**

A few weeks ago, while getting 'ubuntu-gnome-desktop' added to 'tasksel' so netboot installations would be simpler, Ubuntu GNOME dev requested that I fiddle around with converting a standard Ubuntu installation to Ubuntu GNOME and that task finally rose to the top of my to-do list. I hope the mods won't mind me working on this here so I can share things with the Ubuntu GNOME QA mailing list. I really need to use code tags to make this understandable :)

If anyone else wants to play feel free, but be mindful that I DO NOT have anything figured out! **[COLOR="#FF0000"]If you break it you own it!!!! [/COLOR]**

This is the actual content of the PM I recieved on April 5th:

> I gave that a quick test and it seems to do the right thing (from mini.iso install).

I have no idea however, how well things will work when cross-grading.

It would be nice to try (from vanilla ubuntu desktop)
apt-get remove ubuntu-default-settings ubuntu-desktop
apt-get install ubuntu-gnome-desktop^
apt-get autoremove

I suspect we would still get be left with u-c-c/u-s-d/UOA stack, but maybe that is unavoidable for cross-grading


The first thing I did was gather some info by seeing what Ubuntu specific packages are added to a freshly installed and fully updated Ubuntu GNOME Trusty install when adding 'ubuntu-desktop'. I also wanted to check for any arch specific differences between i386 and amd64. The most important parts are highlighted.

Here's the result in Trusty i386:

```
lance@lance-desktop:~$ sudo apt-get install ubuntu-desktop
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  account-plugin-facebook account-plugin-flickr account-plugin-google
  account-plugin-twitter activity-log-manager
  activity-log-manager-control-center adium-theme-ubuntu appmenu-qt
  appmenu-qt5 bamfdaemon branding-ubuntu checkbox-gui checkbox-ng
  checkbox-ng-service compiz compiz-core compiz-gnome compiz-plugins-default
  dmz-cursor-theme doc-base ethtool example-content friends friends-dispatcher
  friends-facebook friends-twitter geoclue-ubuntu-geoip gir1.2-accounts-1.0
  gir1.2-appindicator3-0.1 gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2
  gir1.2-edataserver-1.2 gir1.2-messagingmenu-1.0 gir1.2-signon-1.0
  gnome-power-manager gnome-screensaver gnomine gsettings-ubuntu-schemas
  gstreamer0.10-plugins-base-apps gstreamer0.10-tools
  gstreamer1.0-plugins-base-apps gstreamer1.0-tools gtk2-engines-murrine
  gtk3-engines-unico hud indicator-applet indicator-appmenu
  indicator-bluetooth indicator-datetime indicator-keyboard indicator-messages
  indicator-power indicator-printers indicator-session indicator-sound
  landscape-client-ui-install language-selector-gnome libaccount-plugin-1.0-0
  libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-qt5-1
  libaudio2 libbamf3-2 libcolumbus1 libcolumbus1-common libcompizconfig0
  libdbusmenu-qt2 libdbusmenu-qt5 libdecoration0 libfreerdp-plugins-standard
  libfreerdp1 libfriends0 libgee2 libglew1.10 libglewmx1.10 libgsettings-qt1
  libhud2 liblightdm-gobject-1-0 libmetacity-private0a libmysqlclient18
  libnux-4.0-0 libnux-4.0-common liboxideqt-qmlplugin liboxideqtcore0
  libpanel-applet-4-0 libpocketsphinx1 libprotobuf8 libqt4-dbus
  libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl
  libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql
  libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns
  libqt5core5a libqt5dbus5 libqt5feedback5 libqt5gui5 libqt5multimedia5
  libqt5network5 libqt5opengl5 libqt5organizer5 libqt5positioning5
  libqt5printsupport5 libqt5qml-graphicaleffects libqt5qml5 libqt5quick5
  libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5svg5 libqt5test5
  libqt5webkit5 libqt5webkit5-qmlwebkitplugin libqt5widgets5 libqt5xml5
  libqtassistantclient4 libqtcore4 libqtdbus4 libqtgui4 libqtwebkit4
  libreoffice-style-human libsignon-extension1 libsignon-plugins-common1
  libsignon-qt5-1 libsphinxbase1 libssh-4 libthumbnailer0 libtimezonemap1
  libufe-xidgetter0 libunity-action-qt1 libunity-core-6.0-9
  libunity-gtk2-parser0 libunity-gtk3-parser0 libunity-misc4 libunity-webapps0
  libunityvoice1 libupstart1 liburl-dispatcher1 libuuid-perl libvncserver0
  libwhoopsie-preferences0 libwnck-common libwnck22 libx86-1 libxcb-randr0
  libxcb-render-util0 libxcb-xkb1 libyaml-tiny-perl light-themes lightdm
  metacity-common mysql-common notify-osd notify-osd-icons nux-tools onboard
  onboard-data overlay-scrollbar overlay-scrollbar-gtk2 overlay-scrollbar-gtk3
  pkg-config plainbox-provider-checkbox plainbox-provider-resource-generic
  plainbox-secure-policy plymouth-theme-ubuntu-logo pm-utils python-gconf
  python-qt4 python-qt4-dbus python-sip python3-checkbox-ng
  python3-checkbox-support python3-feedparser python3-lxml python3-plainbox
  python3-pyparsing python3-requests python3-urllib3 qdbus qt-at-spi qtchooser
  qtcore4-l10n qtdeclarative5-accounts-plugin qtdeclarative5-dialogs-plugin
  qtdeclarative5-localstorage-plugin qtdeclarative5-privatewidgets-plugin
  qtdeclarative5-qtfeedback-plugin qtdeclarative5-qtquick2-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-unity-action-plugin
  qtdeclarative5-window-plugin remmina remmina-common remmina-plugin-rdp
  remmina-plugin-vnc signon-keyring-extension signon-plugin-oauth2 signon-ui
  signond sni-qt sphinx-voxforge-hmm-en sphinx-voxforge-lm-en
  telepathy-indicator thunderbird thunderbird-gnome-support totem-mozilla
  ubuntu-artwork ubuntu-docs ubuntu-mono ubuntu-session ubuntu-settings
  ubuntu-sounds ubuntu-sso-client-qt ubuntu-ui-toolkit-theme ubuntu-wallpapers
  ubuntu-wallpapers-trusty ubuntuone-client-data unity unity-asset-pool
  unity-control-center unity-control-center-signon unity-greeter
  unity-gtk-module-common unity-gtk2-module unity-gtk3-module
  unity-lens-applications unity-lens-files unity-lens-friends unity-lens-music
  unity-lens-photos unity-lens-video unity-scope-audacious
  unity-scope-calculator unity-scope-chromiumbookmarks unity-scope-clementine
  unity-scope-colourlovers unity-scope-devhelp unity-scope-firefoxbookmarks
  unity-scope-gdrive unity-scope-gmusicbrowser unity-scope-gourmet
  unity-scope-guayadeque unity-scope-home unity-scope-manpages
  unity-scope-musicstores unity-scope-musique unity-scope-openclipart
  unity-scope-texdoc unity-scope-tomboy unity-scope-video-remote
  unity-scope-virtualbox unity-scope-yelp unity-scope-zotero
  unity-scopes-master-default unity-scopes-runner unity-services
  unity-settings-daemon unity-voice-service unity-webapps-common
  unity-webapps-qml unity-webapps-service vbetool webaccounts-extension-common
  webapp-container webbrowser-app whoopsie-preferences xcursor-themes
  xul-ext-unity xul-ext-webaccounts xul-ext-websites-integration
Suggested packages:
  libqt5core5 rarian-compat murrine-themes click
  unity-greeter-session-broadcast nas freerdp-x11 glew-utils
  libqt4-declarative-folderlistmodel libqt4-declarative-gestures
  libqt4-declarative-particles libqt4-declarative-shaders qt4-qmlviewer
  libqt4-dev libicu48 qt4-qtconfig crystalcursors kde-icons-crystal
  url-dispatcher libvncserver0-dbg bonnie++ bootchart curl fwts git-core
  glmark2 glmark2-es2 mesa-utils nmap obexftp render-bench smartmontools sox
  stress sysstat wmctrl cpufrequtils radeontool python-gnome2-doc
  python-qt4-dbg python3-lxml-dbg python3-xlsxwriter qt4-default qt5-default
  ttf-lyx ubuntu-wallpapers-saucy ubuntu-wallpapers-karmic
  ubuntu-wallpapers-lucid ubuntu-wallpapers-maverick ubuntu-wallpapers-natty
  ubuntu-wallpapers-oneiric ubuntu-wallpapers-precise
  ubuntu-wallpapers-quantal ubuntu-wallpapers-raring
  lightdm-remote-session-freerdp lightdm-remote-session-uccsconfigure
  remote-login-service audacious clementine gmusicbrowser guayadeque musique
  tomboy qtdeclarative5-ubuntu-content0.1
[B][COLOR="#FF0000"]The following NEW packages will be installed[/COLOR]:
  account-plugin-facebook account-plugin-flickr account-plugin-google
  account-plugin-twitter activity-log-manager
  activity-log-manager-control-center adium-theme-ubuntu appmenu-qt
  appmenu-qt5 bamfdaemon branding-ubuntu checkbox-gui checkbox-ng
  checkbox-ng-service compiz compiz-core compiz-gnome compiz-plugins-default
  dmz-cursor-theme doc-base ethtool example-content friends friends-dispatcher
  friends-facebook friends-twitter geoclue-ubuntu-geoip gir1.2-accounts-1.0
  gir1.2-appindicator3-0.1 gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2
  gir1.2-edataserver-1.2 gir1.2-messagingmenu-1.0 gir1.2-signon-1.0
  gnome-power-manager gnome-screensaver gnomine gsettings-ubuntu-schemas
  gstreamer0.10-plugins-base-apps gstreamer0.10-tools
  gstreamer1.0-plugins-base-apps gstreamer1.0-tools gtk2-engines-murrine
  gtk3-engines-unico hud indicator-applet indicator-appmenu
  indicator-bluetooth indicator-datetime indicator-keyboard indicator-messages
  indicator-power indicator-printers indicator-session indicator-sound
  landscape-client-ui-install language-selector-gnome libaccount-plugin-1.0-0
  libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-qt5-1
  libaudio2 libbamf3-2 libcolumbus1 libcolumbus1-common libcompizconfig0
  libdbusmenu-qt2 libdbusmenu-qt5 libdecoration0 libfreerdp-plugins-standard
  libfreerdp1 libfriends0 libgee2 libglew1.10 libglewmx1.10 libgsettings-qt1
  libhud2 liblightdm-gobject-1-0 libmetacity-private0a libmysqlclient18
  libnux-4.0-0 libnux-4.0-common liboxideqt-qmlplugin liboxideqtcore0
  libpanel-applet-4-0 libpocketsphinx1 libprotobuf8 libqt4-dbus
  libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl
  libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql
  libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns
  libqt5core5a libqt5dbus5 libqt5feedback5 libqt5gui5 libqt5multimedia5
  libqt5network5 libqt5opengl5 libqt5organizer5 libqt5positioning5
  libqt5printsupport5 libqt5qml-graphicaleffects libqt5qml5 libqt5quick5
  libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5svg5 libqt5test5
  libqt5webkit5 libqt5webkit5-qmlwebkitplugin libqt5widgets5 libqt5xml5
  libqtassistantclient4 libqtcore4 libqtdbus4 libqtgui4 libqtwebkit4
  libreoffice-style-human libsignon-extension1 libsignon-plugins-common1
  libsignon-qt5-1 libsphinxbase1 libssh-4 libthumbnailer0 libtimezonemap1
  libufe-xidgetter0 libunity-action-qt1 libunity-core-6.0-9
  libunity-gtk2-parser0 libunity-gtk3-parser0 libunity-misc4 libunity-webapps0
  libunityvoice1 libupstart1 liburl-dispatcher1 libuuid-perl libvncserver0
  libwhoopsie-preferences0 libwnck-common libwnck22 libx86-1 libxcb-randr0
  libxcb-render-util0 libxcb-xkb1 libyaml-tiny-perl light-themes lightdm
  metacity-common mysql-common notify-osd notify-osd-icons nux-tools onboard
  onboard-data overlay-scrollbar overlay-scrollbar-gtk2 overlay-scrollbar-gtk3
  pkg-config plainbox-provider-checkbox plainbox-provider-resource-generic
  plainbox-secure-policy plymouth-theme-ubuntu-logo pm-utils python-gconf
  python-qt4 python-qt4-dbus python-sip python3-checkbox-ng
  python3-checkbox-support python3-feedparser python3-lxml python3-plainbox
  python3-pyparsing python3-requests python3-urllib3 qdbus qt-at-spi qtchooser
  qtcore4-l10n qtdeclarative5-accounts-plugin qtdeclarative5-dialogs-plugin
  qtdeclarative5-localstorage-plugin qtdeclarative5-privatewidgets-plugin
  qtdeclarative5-qtfeedback-plugin qtdeclarative5-qtquick2-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-unity-action-plugin
  qtdeclarative5-window-plugin remmina remmina-common remmina-plugin-rdp
  remmina-plugin-vnc signon-keyring-extension signon-plugin-oauth2 signon-ui
  signond sni-qt sphinx-voxforge-hmm-en sphinx-voxforge-lm-en
  telepathy-indicator thunderbird thunderbird-gnome-support totem-mozilla
  ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-session
  ubuntu-settings ubuntu-sounds ubuntu-sso-client-qt ubuntu-ui-toolkit-theme
  ubuntu-wallpapers ubuntu-wallpapers-trusty ubuntuone-client-data unity
  unity-asset-pool unity-control-center unity-control-center-signon
  unity-greeter unity-gtk-module-common unity-gtk2-module unity-gtk3-module
  unity-lens-applications unity-lens-files unity-lens-friends unity-lens-music
  unity-lens-photos unity-lens-video unity-scope-audacious
  unity-scope-calculator unity-scope-chromiumbookmarks unity-scope-clementine
  unity-scope-colourlovers unity-scope-devhelp unity-scope-firefoxbookmarks
  unity-scope-gdrive unity-scope-gmusicbrowser unity-scope-gourmet
  unity-scope-guayadeque unity-scope-home unity-scope-manpages
  unity-scope-musicstores unity-scope-musique unity-scope-openclipart
  unity-scope-texdoc unity-scope-tomboy unity-scope-video-remote
  unity-scope-virtualbox unity-scope-yelp unity-scope-zotero
  unity-scopes-master-default unity-scopes-runner unity-services
  unity-settings-daemon unity-voice-service unity-webapps-common
  unity-webapps-qml unity-webapps-service vbetool webaccounts-extension-common
  webapp-container webbrowser-app whoopsie-preferences xcursor-themes
  xul-ext-unity xul-ext-webaccounts xul-ext-websites-integration
[COLOR="#FF0000"]0 upgraded, 282 newly installed, 0 to remove and 3 not upgraded.
Need to get 158 MB of archives.
After this operation, 548 MB of additional disk space will be used[/COLOR].[/B]
Do you want to continue? [Y/n] n
Abort.
```

And the results in amd64:

```
lance@lance-desktop:~$ sudo apt-get install ubuntu-desktop
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  account-plugin-facebook account-plugin-flickr account-plugin-google
  account-plugin-twitter activity-log-manager
  activity-log-manager-control-center adium-theme-ubuntu appmenu-qt
  appmenu-qt5 bamfdaemon branding-ubuntu checkbox-gui checkbox-ng
  checkbox-ng-service compiz compiz-core compiz-gnome compiz-plugins-default
  dmz-cursor-theme doc-base ethtool example-content friends friends-dispatcher
  friends-facebook friends-twitter geoclue-ubuntu-geoip gir1.2-accounts-1.0
  gir1.2-appindicator3-0.1 gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2
  gir1.2-edataserver-1.2 gir1.2-messagingmenu-1.0 gir1.2-signon-1.0
  gnome-power-manager gnome-screensaver gnomine gsettings-ubuntu-schemas
  gstreamer0.10-plugins-base-apps gstreamer0.10-tools
  gstreamer1.0-plugins-base-apps gstreamer1.0-tools gtk2-engines-murrine
  gtk3-engines-unico hud indicator-applet indicator-appmenu
  indicator-bluetooth indicator-datetime indicator-keyboard indicator-messages
  indicator-power indicator-printers indicator-session indicator-sound
  landscape-client-ui-install language-selector-gnome libaccount-plugin-1.0-0
  libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-qt5-1
  libaudio2 libbamf3-2 libcolumbus1 libcolumbus1-common libcompizconfig0
  libdbusmenu-qt2 libdbusmenu-qt5 libdecoration0 libfreerdp-plugins-standard
  libfreerdp1 libfriends0 libgee2 libglew1.10 libglewmx1.10 libgsettings-qt1
  libhud2 liblightdm-gobject-1-0 libmetacity-private0a libmysqlclient18
  libnux-4.0-0 libnux-4.0-common liboxideqt-qmlplugin liboxideqtcore0
  libpanel-applet-4-0 libpocketsphinx1 libprotobuf8 libqt4-dbus
  libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl
  libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql
  libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns
  libqt5core5a libqt5dbus5 libqt5feedback5 libqt5gui5 libqt5multimedia5
  libqt5network5 libqt5opengl5 libqt5organizer5 libqt5positioning5
  libqt5printsupport5 libqt5qml-graphicaleffects libqt5qml5 libqt5quick5
  libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5svg5 libqt5test5
  libqt5webkit5 libqt5webkit5-qmlwebkitplugin libqt5widgets5 libqt5xml5
  libqtassistantclient4 libqtcore4 libqtdbus4 libqtgui4 libqtwebkit4
  libreoffice-style-human libsignon-extension1 libsignon-plugins-common1
  libsignon-qt5-1 libsphinxbase1 libssh-4 libthumbnailer0 libtimezonemap1
  libufe-xidgetter0 libunity-action-qt1 libunity-core-6.0-9
  libunity-gtk2-parser0 libunity-gtk3-parser0 libunity-misc4 libunity-webapps0
  libunityvoice1 libupstart1 liburl-dispatcher1 libuuid-perl libvncserver0
  libwhoopsie-preferences0 libwnck-common libwnck22 libx86-1 libxcb-randr0
  libxcb-render-util0 libxcb-xkb1 libyaml-tiny-perl light-themes lightdm
  metacity-common mysql-common notify-osd notify-osd-icons nux-tools onboard
  onboard-data overlay-scrollbar overlay-scrollbar-gtk2 overlay-scrollbar-gtk3
  pkg-config plainbox-provider-checkbox plainbox-provider-resource-generic
  plainbox-secure-policy plymouth-theme-ubuntu-logo pm-utils python-gconf
  python-qt4 python-qt4-dbus python-sip python3-checkbox-ng
  python3-checkbox-support python3-feedparser python3-lxml python3-plainbox
  python3-pyparsing python3-requests python3-urllib3 qdbus qt-at-spi qtchooser
  qtcore4-l10n qtdeclarative5-accounts-plugin qtdeclarative5-dialogs-plugin
  qtdeclarative5-localstorage-plugin qtdeclarative5-privatewidgets-plugin
  qtdeclarative5-qtfeedback-plugin qtdeclarative5-qtquick2-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-unity-action-plugin
  qtdeclarative5-window-plugin remmina remmina-common remmina-plugin-rdp
  remmina-plugin-vnc signon-keyring-extension signon-plugin-oauth2 signon-ui
  signond sni-qt sphinx-voxforge-hmm-en sphinx-voxforge-lm-en
  telepathy-indicator thunderbird thunderbird-gnome-support totem-mozilla
  ubuntu-artwork ubuntu-docs ubuntu-mono ubuntu-session ubuntu-settings
  ubuntu-sounds ubuntu-sso-client-qt ubuntu-ui-toolkit-theme ubuntu-wallpapers
  ubuntu-wallpapers-trusty ubuntuone-client-data unity unity-asset-pool
  unity-control-center unity-control-center-signon unity-greeter
  unity-gtk-module-common unity-gtk2-module unity-gtk3-module
  unity-lens-applications unity-lens-files unity-lens-friends unity-lens-music
  unity-lens-photos unity-lens-video unity-scope-audacious
  unity-scope-calculator unity-scope-chromiumbookmarks unity-scope-clementine
  unity-scope-colourlovers unity-scope-devhelp unity-scope-firefoxbookmarks
  unity-scope-gdrive unity-scope-gmusicbrowser unity-scope-gourmet
  unity-scope-guayadeque unity-scope-home unity-scope-manpages
  unity-scope-musicstores unity-scope-musique unity-scope-openclipart
  unity-scope-texdoc unity-scope-tomboy unity-scope-video-remote
  unity-scope-virtualbox unity-scope-yelp unity-scope-zotero
  unity-scopes-master-default unity-scopes-runner unity-services
  unity-settings-daemon unity-voice-service unity-webapps-common
  unity-webapps-qml unity-webapps-service vbetool webaccounts-extension-common
  webapp-container webbrowser-app whoopsie-preferences xcursor-themes
  xul-ext-unity xul-ext-webaccounts xul-ext-websites-integration
Suggested packages:
  libqt5core5 rarian-compat murrine-themes click
  unity-greeter-session-broadcast nas freerdp-x11 glew-utils
  libqt4-declarative-folderlistmodel libqt4-declarative-gestures
  libqt4-declarative-particles libqt4-declarative-shaders qt4-qmlviewer
  libqt4-dev libicu48 qt4-qtconfig crystalcursors kde-icons-crystal
  url-dispatcher libvncserver0-dbg bonnie++ bootchart curl fwts git-core
  glmark2 glmark2-es2 mesa-utils nmap obexftp render-bench smartmontools sox
  stress sysstat wmctrl cpufrequtils radeontool python-gnome2-doc
  python-qt4-dbg python3-lxml-dbg python3-xlsxwriter qt4-default qt5-default
  ttf-lyx ubuntu-wallpapers-saucy ubuntu-wallpapers-karmic
  ubuntu-wallpapers-lucid ubuntu-wallpapers-maverick ubuntu-wallpapers-natty
  ubuntu-wallpapers-oneiric ubuntu-wallpapers-precise
  ubuntu-wallpapers-quantal ubuntu-wallpapers-raring
  lightdm-remote-session-freerdp lightdm-remote-session-uccsconfigure
  remote-login-service audacious clementine gmusicbrowser guayadeque musique
  tomboy qtdeclarative5-ubuntu-content0.1
[B][COLOR="#FF0000"]The following NEW packages will be installed[/COLOR]:
  account-plugin-facebook account-plugin-flickr account-plugin-google
  account-plugin-twitter activity-log-manager
  activity-log-manager-control-center adium-theme-ubuntu appmenu-qt
  appmenu-qt5 bamfdaemon branding-ubuntu checkbox-gui checkbox-ng
  checkbox-ng-service compiz compiz-core compiz-gnome compiz-plugins-default
  dmz-cursor-theme doc-base ethtool example-content friends friends-dispatcher
  friends-facebook friends-twitter geoclue-ubuntu-geoip gir1.2-accounts-1.0
  gir1.2-appindicator3-0.1 gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2
  gir1.2-edataserver-1.2 gir1.2-messagingmenu-1.0 gir1.2-signon-1.0
  gnome-power-manager gnome-screensaver gnomine gsettings-ubuntu-schemas
  gstreamer0.10-plugins-base-apps gstreamer0.10-tools
  gstreamer1.0-plugins-base-apps gstreamer1.0-tools gtk2-engines-murrine
  gtk3-engines-unico hud indicator-applet indicator-appmenu
  indicator-bluetooth indicator-datetime indicator-keyboard indicator-messages
  indicator-power indicator-printers indicator-session indicator-sound
  landscape-client-ui-install language-selector-gnome libaccount-plugin-1.0-0
  libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-qt5-1
  libaudio2 libbamf3-2 libcolumbus1 libcolumbus1-common libcompizconfig0
  libdbusmenu-qt2 libdbusmenu-qt5 libdecoration0 libfreerdp-plugins-standard
  libfreerdp1 libfriends0 libgee2 libglew1.10 libglewmx1.10 libgsettings-qt1
  libhud2 liblightdm-gobject-1-0 libmetacity-private0a libmysqlclient18
  libnux-4.0-0 libnux-4.0-common liboxideqt-qmlplugin liboxideqtcore0
  libpanel-applet-4-0 libpocketsphinx1 libprotobuf8 libqt4-dbus
  libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl
  libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql
  libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns
  libqt5core5a libqt5dbus5 libqt5feedback5 libqt5gui5 libqt5multimedia5
  libqt5network5 libqt5opengl5 libqt5organizer5 libqt5positioning5
  libqt5printsupport5 libqt5qml-graphicaleffects libqt5qml5 libqt5quick5
  libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5svg5 libqt5test5
  libqt5webkit5 libqt5webkit5-qmlwebkitplugin libqt5widgets5 libqt5xml5
  libqtassistantclient4 libqtcore4 libqtdbus4 libqtgui4 libqtwebkit4
  libreoffice-style-human libsignon-extension1 libsignon-plugins-common1
  libsignon-qt5-1 libsphinxbase1 libssh-4 libthumbnailer0 libtimezonemap1
  libufe-xidgetter0 libunity-action-qt1 libunity-core-6.0-9
  libunity-gtk2-parser0 libunity-gtk3-parser0 libunity-misc4 libunity-webapps0
  libunityvoice1 libupstart1 liburl-dispatcher1 libuuid-perl libvncserver0
  libwhoopsie-preferences0 libwnck-common libwnck22 libx86-1 libxcb-randr0
  libxcb-render-util0 libxcb-xkb1 libyaml-tiny-perl light-themes lightdm
  metacity-common mysql-common notify-osd notify-osd-icons nux-tools onboard
  onboard-data overlay-scrollbar overlay-scrollbar-gtk2 overlay-scrollbar-gtk3
  pkg-config plainbox-provider-checkbox plainbox-provider-resource-generic
  plainbox-secure-policy plymouth-theme-ubuntu-logo pm-utils python-gconf
  python-qt4 python-qt4-dbus python-sip python3-checkbox-ng
  python3-checkbox-support python3-feedparser python3-lxml python3-plainbox
  python3-pyparsing python3-requests python3-urllib3 qdbus qt-at-spi qtchooser
  qtcore4-l10n qtdeclarative5-accounts-plugin qtdeclarative5-dialogs-plugin
  qtdeclarative5-localstorage-plugin qtdeclarative5-privatewidgets-plugin
  qtdeclarative5-qtfeedback-plugin qtdeclarative5-qtquick2-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-unity-action-plugin
  qtdeclarative5-window-plugin remmina remmina-common remmina-plugin-rdp
  remmina-plugin-vnc signon-keyring-extension signon-plugin-oauth2 signon-ui
  signond sni-qt sphinx-voxforge-hmm-en sphinx-voxforge-lm-en
  telepathy-indicator thunderbird thunderbird-gnome-support totem-mozilla
  ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-session
  ubuntu-settings ubuntu-sounds ubuntu-sso-client-qt ubuntu-ui-toolkit-theme
  ubuntu-wallpapers ubuntu-wallpapers-trusty ubuntuone-client-data unity
  unity-asset-pool unity-control-center unity-control-center-signon
  unity-greeter unity-gtk-module-common unity-gtk2-module unity-gtk3-module
  unity-lens-applications unity-lens-files unity-lens-friends unity-lens-music
  unity-lens-photos unity-lens-video unity-scope-audacious
  unity-scope-calculator unity-scope-chromiumbookmarks unity-scope-clementine
  unity-scope-colourlovers unity-scope-devhelp unity-scope-firefoxbookmarks
  unity-scope-gdrive unity-scope-gmusicbrowser unity-scope-gourmet
  unity-scope-guayadeque unity-scope-home unity-scope-manpages
  unity-scope-musicstores unity-scope-musique unity-scope-openclipart
  unity-scope-texdoc unity-scope-tomboy unity-scope-video-remote
  unity-scope-virtualbox unity-scope-yelp unity-scope-zotero
  unity-scopes-master-default unity-scopes-runner unity-services
  unity-settings-daemon unity-voice-service unity-webapps-common
  unity-webapps-qml unity-webapps-service vbetool webaccounts-extension-common
  webapp-container webbrowser-app whoopsie-preferences xcursor-themes
  xul-ext-unity xul-ext-webaccounts xul-ext-websites-integration
[COLOR="#FF0000"]0 upgraded, 282 newly installed, 0 to remove and 3 not upgraded.
Need to get 158 MB of archives.
After this operation, 562 MB of additional disk space will be used[/COLOR].[/B]
Do you want to continue? [Y/n] n
Abort.
```

Nothing jumps out at me as arch specific so it's time to move on to step #2 which may take a few hours to complete.

BTW if this appears to be at all worthwhile I'll do the same for converting Ubuntu GNOME to Ubuntu and a couple of other fun things :D

---

### Post by kansasnoob on 2014-05-05
I'm about ready to blow up my first test installation but I want to post some incomplete results:

```
sudo apt-get remove ubuntu-default-settings ubuntu-desktop --assume-no

lance@lance-desktop:~$ sudo apt-get remove ubuntu-default-settings ubuntu-desktop --assume-no
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**[COLOR="#FF0000"]Virtual packages like 'ubuntu-default-settings' can't be removed[/COLOR]**
The following packages will be REMOVED:
  ubuntu-desktop
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
After this operation, 61.4 kB disk space will be freed.
Do you want to continue? [Y/n] N
Abort.
```

With the "^" added to "apt-get install ubuntu-gnome-desktop^" the CLI output is too verbose to copy directly from the terminal so I ran:

```
sudo apt-get install ubuntu-gnome-desktop^ --just-print > white.txt
```

And the results were:

```
Reading package lists...
Building dependency tree...
Reading state information...
acl is already the newest version.
acpi-support is already the newest version.
acpid is already the newest version.
aisleriot is already the newest version.
alsa-base is already the newest version.
alsa-utils is already the newest version.
anacron is already the newest version.
apg is already the newest version.
app-install-data-partner is already the newest version.
apport is already the newest version.
apport-gtk is already the newest version.
apport-symptoms is already the newest version.
apt-xapian-index is already the newest version.
aptdaemon is already the newest version.
aptdaemon-data is already the newest version.
apturl is already the newest version.
apturl-common is already the newest version.
aspell is already the newest version.
aspell-en is already the newest version.
at-spi2-core is already the newest version.
avahi-autoipd is already the newest version.
avahi-daemon is already the newest version.
avahi-utils is already the newest version.
baobab is already the newest version.
bc is already the newest version.
binutils is already the newest version.
bluez is already the newest version.
bluez-alsa is already the newest version.
bluez-cups is already the newest version.
brasero is already the newest version.
brasero-cdrkit is already the newest version.
brasero-common is already the newest version.
brltty is already the newest version.
cheese is already the newest version.
cheese-common is already the newest version.
colord is already the newest version.
cpp is already the newest version.
cpp-4.8 is already the newest version.
cracklib-runtime is already the newest version.
crda is already the newest version.
cups is already the newest version.
cups-browsed is already the newest version.
cups-bsd is already the newest version.
cups-client is already the newest version.
cups-common is already the newest version.
cups-core-drivers is already the newest version.
cups-daemon is already the newest version.
cups-filters is already the newest version.
cups-filters-core-drivers is already the newest version.
cups-pk-helper is already the newest version.
cups-ppdc is already the newest version.
cups-server-common is already the newest version.
dbus-x11 is already the newest version.
dc is already the newest version.
dconf-cli is already the newest version.
dconf-gsettings-backend is already the newest version.
dconf-service is already the newest version.
deja-dup is already the newest version.
deja-dup-backend-gvfs is already the newest version.
desktop-file-utils is already the newest version.
dialog is already the newest version.
dictionaries-common is already the newest version.
diffstat is already the newest version.
dnsmasq-base is already the newest version.
duplicity is already the newest version.
dvd+rw-tools is already the newest version.
empathy is already the newest version.
empathy-common is already the newest version.
enchant is already the newest version.
eog is already the newest version.
espeak-data is already the newest version.
evince is already the newest version.
evince-common is already the newest version.
evolution-data-server is already the newest version.
evolution-data-server-common is already the newest version.
evolution-data-server-online-accounts is already the newest version.
file-roller is already the newest version.
folks-common is already the newest version.
fontconfig is already the newest version.
fontconfig-config is already the newest version.
fonts-dejavu-core is already the newest version.
fonts-droid is already the newest version.
fonts-freefont-ttf is already the newest version.
fonts-kacst is already the newest version.
fonts-kacst-one is already the newest version.
fonts-khmeros-core is already the newest version.
fonts-lao is already the newest version.
fonts-liberation is already the newest version.
fonts-lklug-sinhala is already the newest version.
fonts-nanum is already the newest version.
fonts-opensymbol is already the newest version.
fonts-sil-abyssinica is already the newest version.
fonts-sil-padauk is already the newest version.
fonts-takao-pgothic is already the newest version.
fonts-thai-tlwg is already the newest version.
fonts-tibetan-machine is already the newest version.
fonts-tlwg-garuda is already the newest version.
fonts-tlwg-kinnari is already the newest version.
fonts-tlwg-loma is already the newest version.
fonts-tlwg-mono is already the newest version.
fonts-tlwg-norasi is already the newest version.
fonts-tlwg-purisa is already the newest version.
fonts-tlwg-sawasdee is already the newest version.
fonts-tlwg-typewriter is already the newest version.
fonts-tlwg-typist is already the newest version.
fonts-tlwg-typo is already the newest version.
fonts-tlwg-umpush is already the newest version.
fonts-tlwg-waree is already the newest version.
foomatic-db-compressed-ppds is already the newest version.
gcc is already the newest version.
gcc-4.8 is already the newest version.
gconf-service is already the newest version.
gconf-service-backend is already the newest version.
gconf2 is already the newest version.
gconf2-common is already the newest version.
gcr is already the newest version.
gdb is already the newest version.
gdisk is already the newest version.
gedit is already the newest version.
gedit-common is already the newest version.
genisoimage is already the newest version.
geoclue is already the newest version.
gettext is already the newest version.
ghostscript is already the newest version.
ghostscript-x is already the newest version.
gir1.2-atk-1.0 is already the newest version.
gir1.2-atspi-2.0 is already the newest version.
gir1.2-dbusmenu-glib-0.4 is already the newest version.
gir1.2-dee-1.0 is already the newest version.
gir1.2-freedesktop is already the newest version.
gir1.2-gdata-0.0 is already the newest version.
gir1.2-gdkpixbuf-2.0 is already the newest version.
gir1.2-gmenu-3.0 is already the newest version.
gir1.2-gnomebluetooth-1.0 is already the newest version.
gir1.2-gnomekeyring-1.0 is already the newest version.
gir1.2-goa-1.0 is already the newest version.
gir1.2-gst-plugins-base-1.0 is already the newest version.
gir1.2-gstreamer-1.0 is already the newest version.
gir1.2-gtk-3.0 is already the newest version.
gir1.2-gtksource-3.0 is already the newest version.
gir1.2-gudev-1.0 is already the newest version.
gir1.2-ibus-1.0 is already the newest version.
gir1.2-javascriptcoregtk-3.0 is already the newest version.
gir1.2-networkmanager-1.0 is already the newest version.
gir1.2-notify-0.7 is already the newest version.
gir1.2-packagekitglib-1.0 is already the newest version.
gir1.2-pango-1.0 is already the newest version.
gir1.2-peas-1.0 is already the newest version.
gir1.2-rb-3.0 is already the newest version.
gir1.2-secret-1 is already the newest version.
gir1.2-soup-2.4 is already the newest version.
gir1.2-totem-1.0 is already the newest version.
gir1.2-totem-plparser-1.0 is already the newest version.
gir1.2-udisks-2.0 is already the newest version.
gir1.2-unity-5.0 is already the newest version.
gir1.2-vte-2.90 is already the newest version.
gir1.2-webkit-3.0 is already the newest version.
gir1.2-wnck-3.0 is already the newest version.
gkbd-capplet is already the newest version.
glib-networking is already the newest version.
glib-networking-common is already the newest version.
glib-networking-services is already the newest version.
gnome-accessibility-themes is already the newest version.
gnome-bluetooth is already the newest version.
gnome-calculator is already the newest version.
gnome-contacts is already the newest version.
gnome-control-center-shared-data is already the newest version.
gnome-desktop3-data is already the newest version.
gnome-disk-utility is already the newest version.
gnome-font-viewer is already the newest version.
gnome-icon-theme is already the newest version.
gnome-icon-theme-symbolic is already the newest version.
gnome-keyring is already the newest version.
gnome-mahjongg is already the newest version.
gnome-menus is already the newest version.
gnome-mines is already the newest version.
gnome-orca is already the newest version.
gnome-screenshot is already the newest version.
gnome-session-bin is already the newest version.
gnome-session-canberra is already the newest version.
gnome-session-common is already the newest version.
gnome-settings-daemon-schemas is already the newest version.
gnome-sudoku is already the newest version.
gnome-system-log is already the newest version.
gnome-system-monitor is already the newest version.
gnome-terminal is already the newest version.
gnome-terminal-data is already the newest version.
gnome-user-guide is already the newest version.
gnome-user-share is already the newest version.
gnome-video-effects is already the newest version.
growisofs is already the newest version.
gsettings-desktop-schemas is already the newest version.
gsfonts is already the newest version.
gstreamer0.10-alsa is already the newest version.
gstreamer0.10-nice is already the newest version.
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
gstreamer0.10-pulseaudio is already the newest version.
gstreamer0.10-x is already the newest version.
gstreamer1.0-alsa is already the newest version.
gstreamer1.0-clutter is already the newest version.
gstreamer1.0-nice is already the newest version.
gstreamer1.0-plugins-base is already the newest version.
gstreamer1.0-plugins-good is already the newest version.
gstreamer1.0-pulseaudio is already the newest version.
gstreamer1.0-x is already the newest version.
gucharmap is already the newest version.
guile-2.0-libs is already the newest version.
gvfs is already the newest version.
gvfs-backends is already the newest version.
gvfs-bin is already the newest version.
gvfs-common is already the newest version.
gvfs-daemons is already the newest version.
gvfs-fuse is already the newest version.
gvfs-libs is already the newest version.
hardening-includes is already the newest version.
hicolor-icon-theme is already the newest version.
hplip is already the newest version.
hplip-data is already the newest version.
humanity-icon-theme is already the newest version.
hunspell-en-us is already the newest version.
hwdata is already the newest version.
ibus is already the newest version.
ibus-gtk is already the newest version.
ibus-gtk3 is already the newest version.
ibus-pinyin is already the newest version.
ibus-table is already the newest version.
im-config is already the newest version.
indicator-application is already the newest version.
inputattach is already the newest version.
intel-gpu-tools is already the newest version.
intltool-debian is already the newest version.
iproute is already the newest version.
iputils-arping is already the newest version.
iw is already the newest version.
kerneloops-daemon is already the newest version.
laptop-detect is already the newest version.
libaa1 is already the newest version.
libaccounts-glib0 is already the newest version.
libappindicator3-1 is already the newest version.
libapt-pkg-perl is already the newest version.
libarchive-zip-perl is already the newest version.
libarchive13 is already the newest version.
libart-2.0-2 is already the newest version.
libasan0 is already the newest version.
libasound2 is already the newest version.
libasound2-data is already the newest version.
libasound2-plugins is already the newest version.
libaspell15 is already the newest version.
libasprintf-dev is already the newest version.
libassuan0 is already the newest version.
libasyncns0 is already the newest version.
libatasmart4 is already the newest version.
libatk-adaptor is already the newest version.
libatk-bridge2.0-0 is already the newest version.
libatk1.0-0 is already the newest version.
libatk1.0-data is already the newest version.
libatkmm-1.6-1 is already the newest version.
libatomic1 is already the newest version.
libatspi2.0-0 is already the newest version.
libauthen-sasl-perl is already the newest version.
libautodie-perl is already the newest version.
libavahi-client3 is already the newest version.
libavahi-common-data is already the newest version.
libavahi-common3 is already the newest version.
libavahi-core7 is already the newest version.
libavahi-glib1 is already the newest version.
libavahi-gobject0 is already the newest version.
libavc1394-0 is already the newest version.
libbluetooth3 is already the newest version.
libboost-date-time1.54.0 is already the newest version.
libboost-system1.54.0 is already the newest version.
libbrasero-media3-1 is already the newest version.
libbrlapi0.6 is already the newest version.
libburn4 is already the newest version.
libc-dev-bin is already the newest version.
libc6-dbg is already the newest version.
libc6-dev is already the newest version.
libcaca0 is already the newest version.
libcairo-gobject2 is already the newest version.
libcairo2 is already the newest version.
libcairomm-1.0-1 is already the newest version.
libcamel-1.2-45 is already the newest version.
libcanberra-gtk-module is already the newest version.
libcanberra-gtk0 is already the newest version.
libcanberra-gtk3-0 is already the newest version.
libcanberra-gtk3-module is already the newest version.
libcanberra-pulse is already the newest version.
libcanberra0 is already the newest version.
libcdio-cdda1 is already the newest version.
libcdio-paranoia1 is already the newest version.
libcdio13 is already the newest version.
libcdparanoia0 is already the newest version.
libcdr-0.0-0 is already the newest version.
libcheese-gtk23 is already the newest version.
libcheese7 is already the newest version.
libclass-accessor-perl is already the newest version.
libclone-perl is already the newest version.
libcloog-isl4 is already the newest version.
libclucene-contribs1 is already the newest version.
libclucene-core1 is already the newest version.
libclutter-1.0-0 is already the newest version.
libclutter-1.0-common is already the newest version.
libclutter-gst-2.0-0 is already the newest version.
libclutter-gtk-1.0-0 is already the newest version.
libcmis-0.4-4 is already the newest version.
libcogl-common is already the newest version.
libcogl-pango15 is already the newest version.
libcogl15 is already the newest version.
libcolamd2.8.0 is already the newest version.
libcolord1 is already the newest version.
libcolorhug1 is already the newest version.
libcrack2 is already the newest version.
libcroco3 is already the newest version.
libcrypt-passwdmd5-perl is already the newest version.
libcups2 is already the newest version.
libcupscgi1 is already the newest version.
libcupsfilters1 is already the newest version.
libcupsimage2 is already the newest version.
libcupsmime1 is already the newest version.
libcupsppdc1 is already the newest version.
libcurl3 is already the newest version.
libdaemon0 is already the newest version.
libdatrie1 is already the newest version.
libdbusmenu-glib4 is already the newest version.
libdbusmenu-gtk3-4 is already the newest version.
libdbusmenu-gtk4 is already the newest version.
libdconf1 is already the newest version.
libdee-1.0-4 is already the newest version.
libdigest-hmac-perl is already the newest version.
libdjvulibre-text is already the newest version.
libdjvulibre21 is already the newest version.
libdmapsharing-3.0-2 is already the newest version.
libdotconf0 is already the newest version.
libdrm-intel1 is already the newest version.
libdrm-nouveau2 is already the newest version.
libdrm-radeon1 is already the newest version.
libdv4 is already the newest version.
libebackend-1.2-7 is already the newest version.
libebook-1.2-14 is already the newest version.
libebook-contacts-1.2-0 is already the newest version.
libecal-1.2-16 is already the newest version.
libedata-book-1.2-20 is already the newest version.
libedata-cal-1.2-23 is already the newest version.
libedataserver-1.2-18 is already the newest version.
libegl1-mesa is already the newest version.
libegl1-mesa-drivers is already the newest version.
libelfg0 is already the newest version.
libemail-valid-perl is already the newest version.
libenchant1c2a is already the newest version.
libespeak1 is already the newest version.
libevdocument3-4 is already the newest version.
libevent-2.0-5 is already the newest version.
libevview3-3 is already the newest version.
libexempi3 is already the newest version.
libexif12 is already the newest version.
libexiv2-12 is already the newest version.
libexttextcat-2.0-0 is already the newest version.
libexttextcat-data is already the newest version.
libfarstream-0.1-0 is already the newest version.
libfarstream-0.2-2 is already the newest version.
libfftw3-single3 is already the newest version.
libfile-basedir-perl is already the newest version.
libfile-copy-recursive-perl is already the newest version.
libfile-desktopentry-perl is already the newest version.
libfile-fcntllock-perl is already the newest version.
libfile-mimeinfo-perl is already the newest version.
libflac8 is already the newest version.
libfolks-eds25 is already the newest version.
libfolks-telepathy25 is already the newest version.
libfolks25 is already the newest version.
libfontconfig1 is already the newest version.
libfontembed1 is already the newest version.
libfontenc1 is already the newest version.
libframe6 is already the newest version.
libfreetype6 is already the newest version.
libfs6 is already the newest version.
libgail-3-0 is already the newest version.
libgail-common is already the newest version.
libgail18 is already the newest version.
libgbm1 is already the newest version.
libgc1c2 is already the newest version.
libgcc-4.8-dev is already the newest version.
libgconf-2-4 is already the newest version.
libgcr-ui-3-1 is already the newest version.
libgd3 is already the newest version.
libgdata-common is already the newest version.
libgdata13 is already the newest version.
libgdk-pixbuf2.0-0 is already the newest version.
libgdk-pixbuf2.0-common is already the newest version.
libgee-0.8-2 is already the newest version.
libgeis1 is already the newest version.
libgeoclue0 is already the newest version.
libgettextpo-dev is already the newest version.
libgettextpo0 is already the newest version.
libgexiv2-2 is already the newest version.
libgl1-mesa-dri is already the newest version.
libgl1-mesa-glx is already the newest version.
libglamor0 is already the newest version.
libglapi-mesa is already the newest version.
libglib2.0-bin is already the newest version.
libglibmm-2.4-1c2a is already the newest version.
libglu1-mesa is already the newest version.
libgmime-2.6-0 is already the newest version.
libgmp10 is already the newest version.
libgnome-bluetooth11 is already the newest version.
libgnome-control-center1 is already the newest version.
libgnome-desktop-3-7 is already the newest version.
libgnome-keyring-common is already the newest version.
libgnome-keyring0 is already the newest version.
libgnome-menu-3-0 is already the newest version.
libgnomekbd-common is already the newest version.
libgnomekbd8 is already the newest version.
libgoa-1.0-0b is already the newest version.
libgoa-1.0-common is already the newest version.
libgomp1 is already the newest version.
libgpgme11 is already the newest version.
libgphoto2-6 is already the newest version.
libgphoto2-l10n is already the newest version.
libgphoto2-port10 is already the newest version.
libgpm2 is already the newest version.
libgpod-common is already the newest version.
libgpod4 is already the newest version.
libgrail6 is already the newest version.
libgraphite2-3 is already the newest version.
libgrip0 is already the newest version.
libgs9 is already the newest version.
libgs9-common is already the newest version.
libgssdp-1.0-3 is already the newest version.
libgstreamer-plugins-base0.10-0 is already the newest version.
libgstreamer-plugins-base1.0-0 is already the newest version.
libgstreamer-plugins-good1.0-0 is already the newest version.
libgstreamer0.10-0 is already the newest version.
libgstreamer1.0-0 is already the newest version.
libgtk-3-0 is already the newest version.
libgtk-3-bin is already the newest version.
libgtk-3-common is already the newest version.
libgtk2.0-0 is already the newest version.
libgtk2.0-bin is already the newest version.
libgtk2.0-common is already the newest version.
libgtkmm-3.0-1 is already the newest version.
libgtksourceview-3.0-1 is already the newest version.
libgtksourceview-3.0-common is already the newest version.
libgtop2-7 is already the newest version.
libgtop2-common is already the newest version.
libgucharmap-2-90-7 is already the newest version.
libgudev-1.0-0 is already the newest version.
libgupnp-1.0-4 is already the newest version.
libgupnp-igd-1.0-4 is already the newest version.
libgusb2 is already the newest version.
libgutenprint2 is already the newest version.
libgweather-3-6 is already the newest version.
libgweather-common is already the newest version.
libgxps2 is already the newest version.
libharfbuzz-icu0 is already the newest version.
libharfbuzz0b is already the newest version.
libhpmud0 is already the newest version.
libhunspell-1.3-0 is already the newest version.
libhyphen0 is already the newest version.
libibus-1.0-5 is already the newest version.
libical1 is already the newest version.
libice6 is already the newest version.
libicu52 is already the newest version.
libido3-0.1-0 is already the newest version.
libiec61883-0 is already the newest version.
libieee1284-3 is already the newest version.
libijs-0.35 is already the newest version.
libimobiledevice4 is already the newest version.
libindicator3-7 is already the newest version.
libio-pty-perl is already the newest version.
libio-socket-inet6-perl is already the newest version.
libio-socket-ssl-perl is already the newest version.
libio-string-perl is already the newest version.
libipc-run-perl is already the newest version.
libipc-system-simple-perl is already the newest version.
libisl10 is already the newest version.
libisofs6 is already the newest version.
libitm1 is already the newest version.
libiw30 is already the newest version.
libjack-jackd2-0 is already the newest version.
libjasper1 is already the newest version.
libjavascriptcoregtk-3.0-0 is already the newest version.
libjbig2dec0 is already the newest version.
libjpeg-turbo8 is already the newest version.
libjpeg8 is already the newest version.
libjson-glib-1.0-0 is already the newest version.
libjson-glib-1.0-common is already the newest version.
libjte1 is already the newest version.
libkpathsea6 is already the newest version.
liblangtag-common is already the newest version.
liblangtag1 is already the newest version.
liblcms2-2 is already the newest version.
libldb1 is already the newest version.
liblircclient0 is already the newest version.
liblist-moreutils-perl is already the newest version.
libllvm3.4 is already the newest version.
liblouis-data is already the newest version.
liblouis2 is already the newest version.
libltdl7 is already the newest version.
liblua5.2-0 is already the newest version.
liblzo2-2 is already the newest version.
libmailtools-perl is already the newest version.
libmbim-glib0 is already the newest version.
libmeanwhile1 is already the newest version.
libmessaging-menu0 is already the newest version.
libmhash2 is already the newest version.
libminiupnpc8 is already the newest version.
libmission-control-plugins0 is already the newest version.
libmm-glib0 is already the newest version.
libmnl0 is already the newest version.
libmpc3 is already the newest version.
libmpfr4 is already the newest version.
libmspub-0.0-0 is already the newest version.
libmtdev1 is already the newest version.
libmtp-common is already the newest version.
libmtp-runtime is already the newest version.
libmtp9 is already the newest version.
libmythes-1.2-0 is already the newest version.
libnatpmp1 is already the newest version.
libnautilus-extension1a is already the newest version.
libneon27-gnutls is already the newest version.
libnet-dns-perl is already the newest version.
libnet-domain-tld-perl is already the newest version.
libnet-ip-perl is already the newest version.
libnet-libidn-perl is already the newest version.
libnet-smtp-ssl-perl is already the newest version.
libnet-ssleay-perl is already the newest version.
libnetfilter-conntrack3 is already the newest version.
libnettle4 is already the newest version.
libnice10 is already the newest version.
libnl-3-200 is already the newest version.
libnl-genl-3-200 is already the newest version.
libnl-route-3-200 is already the newest version.
libnm-glib-vpn1 is already the newest version.
libnm-glib4 is already the newest version.
libnm-gtk-common is already the newest version.
libnm-gtk0 is already the newest version.
libnm-util2 is already the newest version.
libnotify-bin is already the newest version.
libnotify4 is already the newest version.
libnspr4 is already the newest version.
libnss-mdns is already the newest version.
libnss3 is already the newest version.
libnss3-nssdb is already the newest version.
libntdb1 is already the newest version.
liboauth0 is already the newest version.
libogg0 is already the newest version.
libopencc1 is already the newest version.
libopenobex1 is already the newest version.
libopenvg1-mesa is already the newest version.
liborc-0.4-0 is already the newest version.
liborcus-0.6-0 is already the newest version.
libp11-kit-gnome-keyring is already the newest version.
libpackagekit-glib2-16 is already the newest version.
libpam-gnome-keyring is already the newest version.
libpango-1.0-0 is already the newest version.
libpango1.0-0 is already the newest version.
libpangocairo-1.0-0 is already the newest version.
libpangoft2-1.0-0 is already the newest version.
libpangomm-1.4-1 is already the newest version.
libpangox-1.0-0 is already the newest version.
libpangoxft-1.0-0 is already the newest version.
libpaper-utils is already the newest version.
libpaper1 is already the newest version.
libparse-debianchangelog-perl is already the newest version.
libpciaccess0 is already the newest version.
libpcsclite1 is already the newest version.
libpeas-1.0-0 is already the newest version.
libpeas-common is already the newest version.
libperl5.18 is already the newest version.
libperlio-gzip-perl is already the newest version.
libpixman-1-0 is already the newest version.
libplist1 is already the newest version.
libpolkit-agent-1-0 is already the newest version.
libpolkit-backend-1-0 is already the newest version.
libpoppler-glib8 is already the newest version.
libpoppler44 is already the newest version.
libportaudio2 is already the newest version.
libproxy1 is already the newest version.
libproxy1-plugin-gsettings is already the newest version.
libproxy1-plugin-networkmanager is already the newest version.
libpulse-mainloop-glib0 is already the newest version.
libpulse0 is already the newest version.
libpulsedsp is already the newest version.
libpurple-bin is already the newest version.
libpurple0 is already the newest version.
libpwquality-common is already the newest version.
libpwquality1 is already the newest version.
libpython-stdlib is already the newest version.
libpython2.7 is already the newest version.
libpython2.7-minimal is already the newest version.
libpython2.7-stdlib is already the newest version.
libpython3.4 is already the newest version.
libpyzy-1.0-0 is already the newest version.
libqmi-glib0 is already the newest version.
libqpdf13 is already the newest version.
libquadmath0 is already the newest version.
libraptor2-0 is already the newest version.
librasqal3 is already the newest version.
libraw1394-11 is already the newest version.
libraw9 is already the newest version.
librdf0 is already the newest version.
libreadline5 is already the newest version.
libreoffice-avmedia-backend-gstreamer is already the newest version.
libreoffice-base-core is already the newest version.
libreoffice-calc is already the newest version.
libreoffice-common is already the newest version.
libreoffice-core is already the newest version.
libreoffice-draw is already the newest version.
libreoffice-gnome is already the newest version.
libreoffice-gtk is already the newest version.
libreoffice-impress is already the newest version.
libreoffice-math is already the newest version.
libreoffice-ogltrans is already the newest version.
libreoffice-pdfimport is already the newest version.
libreoffice-presentation-minimizer is already the newest version.
libreoffice-writer is already the newest version.
librest-0.7-0 is already the newest version.
librhythmbox-core8 is already the newest version.
librsvg2-2 is already the newest version.
librsvg2-common is already the newest version.
librsync1 is already the newest version.
libsamplerate0 is already the newest version.
libsane is already the newest version.
libsane-common is already the newest version.
libsane-hpaio is already the newest version.
libsbc1 is already the newest version.
libsecret-1-0 is already the newest version.
libsecret-common is already the newest version.
libsensors4 is already the newest version.
libsgutils2-2 is already the newest version.
libshout3 is already the newest version.
libsigc++-2.0-0c2a is already the newest version.
libsignon-glib1 is already the newest version.
libsm6 is already the newest version.
libsmbclient is already the newest version.
libsndfile1 is already the newest version.
libsnmp-base is already the newest version.
libsnmp30 is already the newest version.
libsocket6-perl is already the newest version.
libsonic0 is already the newest version.
libsoup-gnome2.4-1 is already the newest version.
libsoup2.4-1 is already the newest version.
libspectre1 is already the newest version.
libspeechd2 is already the newest version.
libspeex1 is already the newest version.
libspeexdsp1 is already the newest version.
libstartup-notification0 is already the newest version.
libsub-identify-perl is already the newest version.
libsub-name-perl is already the newest version.
libsystemd-journal0 is already the newest version.
libt1-5 is already the newest version.
libtag1-vanilla is already the newest version.
libtag1c2a is already the newest version.
libtalloc2 is already the newest version.
libtcl8.6 is already the newest version.
libtdb1 is already the newest version.
libtelepathy-farstream3 is already the newest version.
libtelepathy-glib0 is already the newest version.
libtelepathy-logger3 is already the newest version.
libtevent0 is already the newest version.
libtext-levenshtein-perl is already the newest version.
libthai-data is already the newest version.
libthai0 is already the newest version.
libtheora0 is already the newest version.
libtiff5 is already the newest version.
libtimedate-perl is already the newest version.
libtk8.6 is already the newest version.
libtotem-plparser18 is already the newest version.
libtotem0 is already the newest version.
libtxc-dxtn-s2tc0 is already the newest version.
libudisks2-0 is already the newest version.
libunistring0 is already the newest version.
libunity-control-center1 is already the newest version.
libunity-protocol-private0 is already the newest version.
libunity-scopes-json-def-desktop is already the newest version.
libunity9 is already the newest version.
libupower-glib1 is already the newest version.
liburi-perl is already the newest version.
libusbmuxd2 is already the newest version.
libutempter0 is already the newest version.
libv4l-0 is already the newest version.
libv4lconvert0 is already the newest version.
libvisio-0.0-0 is already the newest version.
libvisual-0.4-0 is already the newest version.
libvisual-0.4-plugins is already the newest version.
libvorbis0a is already the newest version.
libvorbisenc2 is already the newest version.
libvorbisfile3 is already the newest version.
libvpx1 is already the newest version.
libvte-2.90-9 is already the newest version.
libvte-2.90-common is already the newest version.
libwacom-common is already the newest version.
libwacom2 is already the newest version.
libwavpack1 is already the newest version.
libwayland-client0 is already the newest version.
libwayland-cursor0 is already the newest version.
libwayland-egl1-mesa is already the newest version.
libwayland-server0 is already the newest version.
libwbclient0 is already the newest version.
libwebkitgtk-3.0-0 is already the newest version.
libwebkitgtk-3.0-common is already the newest version.
libwebp5 is already the newest version.
libwebpmux1 is already the newest version.
libwhoopsie0 is already the newest version.
libwmf0.2-7 is already the newest version.
libwmf0.2-7-gtk is already the newest version.
libwnck-3-0 is already the newest version.
libwnck-3-common is already the newest version.
libwpd-0.9-9 is already the newest version.
libwpg-0.2-2 is already the newest version.
libwps-0.2-2 is already the newest version.
libwrap0 is already the newest version.
libx11-xcb1 is already the newest version.
libxapian22 is already the newest version.
libxatracker2 is already the newest version.
libxaw7 is already the newest version.
libxcb-dri2-0 is already the newest version.
libxcb-dri3-0 is already the newest version.
libxcb-glx0 is already the newest version.
libxcb-icccm4 is already the newest version.
libxcb-image0 is already the newest version.
libxcb-present0 is already the newest version.
libxcb-render0 is already the newest version.
libxcb-shape0 is already the newest version.
libxcb-shm0 is already the newest version.
libxcb-sync1 is already the newest version.
libxcb-util0 is already the newest version.
libxcb-xfixes0 is already the newest version.
libxcomposite1 is already the newest version.
libxcursor1 is already the newest version.
libxdamage1 is already the newest version.
libxfixes3 is already the newest version.
libxfont1 is already the newest version.
libxft2 is already the newest version.
libxi6 is already the newest version.
libxinerama1 is already the newest version.
libxkbcommon0 is already the newest version.
libxkbfile1 is already the newest version.
libxklavier16 is already the newest version.
libxmu6 is already the newest version.
libxp6 is already the newest version.
libxpm4 is already the newest version.
libxrandr2 is already the newest version.
libxrender1 is already the newest version.
libxres1 is already the newest version.
libxshmfence1 is already the newest version.
libxslt1.1 is already the newest version.
libxss1 is already the newest version.
libxt6 is already the newest version.
libxtst6 is already the newest version.
libxv1 is already the newest version.
libxvmc1 is already the newest version.
libxxf86dga1 is already the newest version.
libxxf86vm1 is already the newest version.
libyajl2 is already the newest version.
libyelp0 is already the newest version.
libzeitgeist-1.0-1 is already the newest version.
libzeitgeist-2.0-0 is already the newest version.
libzephyr4 is already the newest version.
lintian is already the newest version.
linux-libc-dev is already the newest version.
linux-sound-base is already the newest version.
lp-solve is already the newest version.
make is already the newest version.
manpages-dev is already the newest version.
media-player-info is already the newest version.
memtest86+ is already the newest version.
mobile-broadband-provider-info is already the newest version.
modemmanager is already the newest version.
mousetweaks is already the newest version.
mscompress is already the newest version.
mtools is already the newest version.
nautilus is already the newest version.
nautilus-data is already the newest version.
nautilus-sendto is already the newest version.
nautilus-sendto-empathy is already the newest version.
nautilus-share is already the newest version.
network-manager is already the newest version.
network-manager-gnome is already the newest version.
network-manager-pptp is already the newest version.
network-manager-pptp-gnome is already the newest version.
obex-data-server is already the newest version.
obexd-client is already the newest version.
oneconf is already the newest version.
oneconf-common is already the newest version.
openprinting-ppds is already the newest version.
p11-kit is already the newest version.
p11-kit-modules is already the newest version.
patch is already the newest version.
patchutils is already the newest version.
pcmciautils is already the newest version.
plymouth-label is already the newest version.
policykit-1 is already the newest version.
policykit-1-gnome is already the newest version.
policykit-desktop-privileges is already the newest version.
poppler-data is already the newest version.
poppler-utils is already the newest version.
pptp-linux is already the newest version.
printer-driver-c2esp is already the newest version.
printer-driver-foo2zjs is already the newest version.
printer-driver-foo2zjs-common is already the newest version.
printer-driver-gutenprint is already the newest version.
printer-driver-hpcups is already the newest version.
printer-driver-min12xxw is already the newest version.
printer-driver-pnm2ppa is already the newest version.
printer-driver-postscript-hp is already the newest version.
printer-driver-ptouch is already the newest version.
printer-driver-pxljr is already the newest version.
printer-driver-sag-gdi is already the newest version.
printer-driver-splix is already the newest version.
pulseaudio is already the newest version.
pulseaudio-module-bluetooth is already the newest version.
pulseaudio-module-x11 is already the newest version.
pulseaudio-utils is already the newest version.
python is already the newest version.
python-apt is already the newest version.
python-aptdaemon is already the newest version.
python-aptdaemon.gtk3widgets is already the newest version.
python-cairo is already the newest version.
python-chardet is already the newest version.
python-commandnotfound is already the newest version.
python-crypto is already the newest version.
python-cups is already the newest version.
python-cupshelpers is already the newest version.
python-dbus is already the newest version.
python-dbus-dev is already the newest version.
python-debian is already the newest version.
python-debtagshw is already the newest version.
python-defer is already the newest version.
python-dirspec is already the newest version.
python-gdbm is already the newest version.
python-gi is already the newest version.
python-gi-cairo is already the newest version.
python-gnomekeyring is already the newest version.
python-gobject is already the newest version.
python-gobject-2 is already the newest version.
python-gtk2 is already the newest version.
python-httplib2 is already the newest version.
python-ibus is already the newest version.
python-imaging is already the newest version.
python-ldb is already the newest version.
python-libxml2 is already the newest version.
python-lockfile is already the newest version.
python-lxml is already the newest version.
python-minimal is already the newest version.
python-notify is already the newest version.
python-ntdb is already the newest version.
python-oauthlib is already the newest version.
python-oneconf is already the newest version.
python-openssl is already the newest version.
python-pam is already the newest version.
python-pexpect is already the newest version.
python-pil is already the newest version.
python-piston-mini-client is already the newest version.
python-pkg-resources is already the newest version.
python-pycurl is already the newest version.
python-renderpm is already the newest version.
python-reportlab is already the newest version.
python-reportlab-accel is already the newest version.
python-samba is already the newest version.
python-serial is already the newest version.
python-six is already the newest version.
python-smbc is already the newest version.
python-talloc is already the newest version.
python-tdb is already the newest version.
python-twisted-bin is already the newest version.
python-twisted-core is already the newest version.
python-twisted-web is already the newest version.
python-ubuntu-sso-client is already the newest version.
python-xapian is already the newest version.
python-xdg is already the newest version.
python-zeitgeist is already the newest version.
python-zope.interface is already the newest version.
python2.7 is already the newest version.
python2.7-minimal is already the newest version.
python3-apport is already the newest version.
python3-aptdaemon is already the newest version.
python3-aptdaemon.gtk3widgets is already the newest version.
python3-aptdaemon.pkcompat is already the newest version.
python3-brlapi is already the newest version.
python3-cairo is already the newest version.
python3-chardet is already the newest version.
python3-crypto is already the newest version.
python3-debian is already the newest version.
python3-defer is already the newest version.
python3-gi-cairo is already the newest version.
python3-httplib2 is already the newest version.
python3-louis is already the newest version.
python3-mako is already the newest version.
python3-markupsafe is already the newest version.
python3-oauthlib is already the newest version.
python3-oneconf is already the newest version.
python3-piston-mini-client is already the newest version.
python3-pkg-resources is already the newest version.
python3-problem-report is already the newest version.
python3-pyatspi is already the newest version.
python3-pycurl is already the newest version.
python3-six is already the newest version.
python3-speechd is already the newest version.
python3-uno is already the newest version.
python3-xdg is already the newest version.
python3-xkit is already the newest version.
qpdf is already the newest version.
rfkill is already the newest version.
rhythmbox is already the newest version.
rhythmbox-data is already the newest version.
rhythmbox-mozilla is already the newest version.
rhythmbox-plugin-cdrecorder is already the newest version.
rhythmbox-plugin-magnatune is already the newest version.
rhythmbox-plugin-zeitgeist is already the newest version.
rhythmbox-plugins is already the newest version.
rtkit is already the newest version.
samba-common is already the newest version.
samba-common-bin is already the newest version.
samba-libs is already the newest version.
sane-utils is already the newest version.
seahorse is already the newest version.
session-migration is already the newest version.
sessioninstaller is already the newest version.
shotwell is already the newest version.
shotwell-common is already the newest version.
simple-scan is already the newest version.
smbclient is already the newest version.
software-center-aptdaemon-plugins is already the newest version.
sound-theme-freedesktop is already the newest version.
speech-dispatcher is already the newest version.
speech-dispatcher-audio-plugins is already the newest version.
ssh-askpass-gnome is already the newest version.
ssl-cert is already the newest version.
syslinux is already the newest version.
syslinux-common is already the newest version.
syslinux-legacy is already the newest version.
system-config-printer-common is already the newest version.
system-config-printer-gnome is already the newest version.
system-config-printer-udev is already the newest version.
t1utils is already the newest version.
tcl is already the newest version.
tcl8.6 is already the newest version.
tcpd is already the newest version.
telepathy-gabble is already the newest version.
telepathy-haze is already the newest version.
telepathy-idle is already the newest version.
telepathy-logger is already the newest version.
telepathy-mission-control-5 is already the newest version.
telepathy-salut is already the newest version.
tk is already the newest version.
tk8.6 is already the newest version.
toshset is already the newest version.
totem is already the newest version.
totem-common is already the newest version.
totem-plugins is already the newest version.
transmission-common is already the newest version.
transmission-gtk is already the newest version.
ttf-indic-fonts-core is already the newest version.
ttf-punjabi-fonts is already the newest version.
ttf-ubuntu-font-family is already the newest version.
ubuntu-drivers-common is already the newest version.
ubuntu-extras-keyring is already the newest version.
ubuntu-release-upgrader-gtk is already the newest version.
ubuntu-sso-client is already the newest version.
ubuntu-system-service is already the newest version.
udisks2 is already the newest version.
unattended-upgrades is already the newest version.
uno-libs3 is already the newest version.
unzip is already the newest version.
update-inetd is already the newest version.
update-manager is already the newest version.
update-notifier is already the newest version.
update-notifier-common is already the newest version.
upower is already the newest version.
ure is already the newest version.
usb-creator-common is already the newest version.
usb-creator-gtk is already the newest version.
usb-modeswitch is already the newest version.
usb-modeswitch-data is already the newest version.
usbmuxd is already the newest version.
vino is already the newest version.
wamerican is already the newest version.
whoopsie is already the newest version.
wireless-regdb is already the newest version.
wireless-tools is already the newest version.
wodim is already the newest version.
wpasupplicant is already the newest version.
x11-apps is already the newest version.
x11-common is already the newest version.
x11-session-utils is already the newest version.
x11-utils is already the newest version.
x11-xfs-utils is already the newest version.
x11-xkb-utils is already the newest version.
x11-xserver-utils is already the newest version.
xbitmaps is already the newest version.
xdg-user-dirs is already the newest version.
xdg-user-dirs-gtk is already the newest version.
xdg-utils is already the newest version.
xdiagnose is already the newest version.
xfonts-base is already the newest version.
xfonts-encodings is already the newest version.
xfonts-mathml is already the newest version.
xfonts-scalable is already the newest version.
xfonts-utils is already the newest version.
xinit is already the newest version.
xinput is already the newest version.
xorg is already the newest version.
xorg-docs-core is already the newest version.
xserver-common is already the newest version.
xserver-xorg is already the newest version.
xserver-xorg-core is already the newest version.
xserver-xorg-input-all is already the newest version.
xserver-xorg-input-evdev is already the newest version.
xserver-xorg-input-mouse is already the newest version.
xserver-xorg-input-synaptics is already the newest version.
xserver-xorg-input-vmmouse is already the newest version.
xserver-xorg-input-wacom is already the newest version.
xserver-xorg-video-all is already the newest version.
xserver-xorg-video-ati is already the newest version.
xserver-xorg-video-cirrus is already the newest version.
xserver-xorg-video-fbdev is already the newest version.
xserver-xorg-video-glamoregl is already the newest version.
xserver-xorg-video-intel is already the newest version.
xserver-xorg-video-mach64 is already the newest version.
xserver-xorg-video-mga is already the newest version.
xserver-xorg-video-modesetting is already the newest version.
xserver-xorg-video-neomagic is already the newest version.
xserver-xorg-video-nouveau is already the newest version.
xserver-xorg-video-openchrome is already the newest version.
xserver-xorg-video-qxl is already the newest version.
xserver-xorg-video-r128 is already the newest version.
xserver-xorg-video-radeon is already the newest version.
xserver-xorg-video-s3 is already the newest version.
xserver-xorg-video-savage is already the newest version.
xserver-xorg-video-siliconmotion is already the newest version.
xserver-xorg-video-sis is already the newest version.
xserver-xorg-video-sisusb is already the newest version.
xserver-xorg-video-tdfx is already the newest version.
xserver-xorg-video-trident is already the newest version.
xserver-xorg-video-vesa is already the newest version.
xserver-xorg-video-vmware is already the newest version.
xterm is already the newest version.
xul-ext-ubufox is already the newest version.
xz-utils is already the newest version.
yelp is already the newest version.
yelp-xsl is already the newest version.
zeitgeist is already the newest version.
zeitgeist-core is already the newest version.
zeitgeist-datahub is already the newest version.
zenity is already the newest version.
zenity-common is already the newest version.
zip is already the newest version.
libenca0 is already the newest version.
libenca0 set to manually installed.
app-install-data is already the newest version.
firefox is already the newest version.
libdpkg-perl is already the newest version.
libjbig0 is already the newest version.
software-center is already the newest version.
Suggested packages:
  gir1.2-colordgtk-1.0 evolution-ews evolution-plugins-experimental
  desktop-base libdata-dump-perl libcrypt-ssleay-perl tango-icon-theme
  libauthen-ntlm-perl razor libdbi-perl pyzor libmail-dkim-perl tracker-gui
[B][COLOR="#FF0000"]The following NEW packages will be installed:
  argyll dconf-editor deja-dup-backend-cloudfiles deja-dup-backend-s3
  evolution evolution-common evolution-indicator evolution-plugins
  fonts-cantarell gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0
  gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-evince-3.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0
  gir1.2-gnomedesktop-3.0 gir1.2-gtkclutter-1.0 gir1.2-gtop-2.0
  gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-nmgtk-1.0 gir1.2-polkit-1.0
  gir1.2-rest-0.7 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-tracker-0.16 gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gir1.2-zpj-0.0 gjs
  gnome-backgrounds gnome-color-manager gnome-control-center
  gnome-control-center-data gnome-documents gnome-icon-theme-extras
  gnome-icon-theme-full gnome-online-accounts gnome-online-miners
  gnome-session gnome-settings-daemon gnome-shell gnome-shell-common
  gnome-shell-extensions gnome-sushi gnome-themes-standard
  gnome-themes-standard-data gnome-tweak-tool grilo-plugins-0.2
  gtk2-engines-pixbuf gvfs-backends-goa itstool libcaribou-common libcaribou0
  libcolord-gtk1 libencode-locale-perl liberror-perl libevolution
  libfile-listing-perl libfont-afm-perl libgdm1 libgif4 libgjs0e
  libgoa-backend-1.0-1 libgrilo-0.2-1 libgsf-1-114 libgsf-1-common
  libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0
  libgupnp-av-1.0-2 libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libicc2 libimdi0 libio-html-perl libiptcdata0
  liblwp-mediatypes-perl liblwp-protocol-https-perl libmail-spf-perl
  libmediaart-1.0-0 libmozjs-24-0 libmusicbrainz5-0 libmutter0c
  libnet-http-perl libnetaddr-ip-perl libnss-myhostname libpst4
  libreoffice-style-tango libsys-hostname-long-perl libtracker-extract-0.16-0
  libtracker-miner-0.16-0 libtracker-sparql-0.16-0 libwww-perl
  libwww-robotrules-perl libxcb-keysyms1 libxcb-xf86dri0 libxcb-xv0
  libxml2-utils libytnef0 libzapojit-0.0-0 mcp-account-manager-goa mutter
  mutter-common notification-daemon plymouth-theme-ubuntu-gnome-logo
  plymouth-theme-ubuntu-gnome-text python-boto python-cloudfiles
  python-requests python-urllib3 re2c sa-compile spamassassin spamc tracker
  tracker-extract tracker-miner-fs tracker-utils ubuntu-gnome-default-settings
  ubuntu-gnome-desktop ubuntu-gnome-wallpapers ubuntu-gnome-wallpapers-trusty
  unoconv xserver-xephyr xsltproc yelp-tools zsync
The following packages will be upgraded:
  python3-software-properties software-properties-common
  software-properties-gtk
3 upgraded, 143 newly installed, 0 to remove and 0 not upgraded.[/COLOR][/B]
Inst libgtkhtml-4.0-common (4.6.6-2ubuntu1 Ubuntu:14.04/trusty [all])
Inst libgtkhtml-4.0-0 (4.6.6-2ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libgtkhtml-editor-4.0-0 (4.6.6-2ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libytnef0 (1.5-6 Ubuntu:14.04/trusty [i386])
Inst libevolution (3.10.4-0ubuntu1 Ubuntu:14.04/trusty [i386])
Inst evolution-common (3.10.4-0ubuntu1 Ubuntu:14.04/trusty [all])
Inst evolution (3.10.4-0ubuntu1 Ubuntu:14.04/trusty [i386])
Inst gnome-themes-standard-data (3.10.0-1ubuntu2 Ubuntu:14.04/trusty [all])
Inst gnome-themes-standard (3.10.0-1ubuntu2 Ubuntu:14.04/trusty [i386])
Inst libcaribou-common (0.4.13-0ubuntu1 Ubuntu:14.04/trusty [all])
Inst libcaribou0 (0.4.13-0ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libcolord-gtk1 (0.1.25-1.1 Ubuntu:14.04/trusty [i386])
Inst libgdm1 (3.10.0.1-0ubuntu3 Ubuntu:14.04/trusty [i386])
Inst libgif4 (4.1.6-11 Ubuntu:14.04/trusty [i386])
Inst libgoa-backend-1.0-1 (3.10.3-0ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libgrilo-0.2-1 (0.2.10-1 Ubuntu:14.04/trusty [i386])
Inst libimdi0 (1.5.1-5ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libmediaart-1.0-0 (0.4.0-1ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libpst4 (0.6.59-1build1 Ubuntu:14.04/trusty [i386])
Inst libxcb-xf86dri0 (1.10-2ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libxcb-xv0 (1.10-2ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libicc2 (2.12+argyll1.5.1-5ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libmusicbrainz5-0 (5.0.1-2 Ubuntu:14.04/trusty [i386])
Inst libnss-myhostname (0.3-6 Ubuntu:14.04/trusty [i386])
Inst libxcb-keysyms1 (0.3.9-1ubuntu1 Ubuntu:14.04/trusty [i386])
Inst python-cloudfiles (1.7.11-2build1 Ubuntu:14.04/trusty [all])
Inst argyll (1.5.1-5ubuntu1 Ubuntu:14.04/trusty [i386])
Inst dconf-editor (0.20.0-1 Ubuntu:14.04/trusty [i386])
Inst deja-dup-backend-cloudfiles (30.0-0ubuntu4 Ubuntu:14.04/trusty [all])
Inst python-urllib3 (1.7.1-1build1 Ubuntu:14.04/trusty [all])
Inst python-requests (2.2.1-1 Ubuntu:14.04/trusty [all])
Inst python-boto (2.20.1-2ubuntu2 Ubuntu:14.04/trusty [all])
Inst deja-dup-backend-s3 (30.0-0ubuntu4 Ubuntu:14.04/trusty [all])
Inst evolution-plugins (3.10.4-0ubuntu1 Ubuntu:14.04/trusty [i386])
Inst fonts-cantarell (0.0.15-1 Ubuntu:14.04/trusty [all])
Inst gir1.2-gdm-1.0 (3.10.0.1-0ubuntu3 Ubuntu:14.04/trusty [i386])
Inst gnome-settings-daemon (3.8.6.1-0ubuntu11 Ubuntu:14.04/trusty [i386])
Inst gir1.2-cogl-1.0 (1.16.2-1 Ubuntu:14.04/trusty [i386])
Inst gir1.2-coglpango-1.0 (1.16.2-1 Ubuntu:14.04/trusty [i386])
Inst gir1.2-json-1.0 (0.16.2-1ubuntu1 Ubuntu:14.04/trusty [i386])
Inst gir1.2-clutter-1.0 (1.16.4-0ubuntu2 Ubuntu:14.04/trusty [i386])
Inst gir1.2-gdesktopenums-3.0 (3.10.1-0ubuntu1 Ubuntu:14.04/trusty [i386])
Inst mutter-common (3.10.4-0ubuntu2 Ubuntu:14.04/trusty [all])
Inst libmutter0c (3.10.4-0ubuntu2 Ubuntu:14.04/trusty [i386])
Inst gir1.2-mutter-3.0 (3.10.4-0ubuntu2 Ubuntu:14.04/trusty [i386])
Inst gir1.2-telepathyglib-0.12 (0.22.1-1ubuntu2 Ubuntu:14.04/trusty [i386])
Inst gnome-icon-theme-full (3.10.0-0ubuntu2 Ubuntu:14.04/trusty [all])
Inst libmozjs-24-0 (24.2.0-1 Ubuntu:14.04/trusty [i386])
Inst libgjs0e (1.39.91-0ubuntu1 Ubuntu:14.04/trusty [i386])
Inst gir1.2-accountsservice-1.0 (0.6.35-0ubuntu7 Ubuntu:14.04/trusty [i386])
Inst gir1.2-caribou-1.0 (0.4.13-0ubuntu1 Ubuntu:14.04/trusty [i386])
Inst gir1.2-gck-1 (3.10.1-1 Ubuntu:14.04/trusty [i386])
Inst gir1.2-gcr-3 (3.10.1-1 Ubuntu:14.04/trusty [i386])
Inst gir1.2-xkl-1.0 (5.4-0ubuntu1 Ubuntu:14.04/trusty [i386])
Inst gir1.2-gkbd-3.0 (3.6.0-0ubuntu2 Ubuntu:14.04/trusty [i386])
Inst gir1.2-gnomedesktop-3.0 (3.8.4-0ubuntu3 Ubuntu:14.04/trusty [i386])
Inst gir1.2-nmgtk-1.0 (0.9.8.8-0ubuntu4 Ubuntu:14.04/trusty [i386])
Inst gir1.2-polkit-1.0 (0.105-4ubuntu2 Ubuntu:14.04/trusty [i386])
Inst gir1.2-telepathylogger-0.2 (0.8.0-3 Ubuntu:14.04/trusty [i386])
Inst gir1.2-upowerglib-1.0 (0.9.23-2ubuntu1 Ubuntu:14.04/trusty [i386])
Inst gjs (1.39.91-0ubuntu1 Ubuntu:14.04/trusty [i386])
Inst gnome-shell-common (3.10.4-0ubuntu5 Ubuntu:14.04/trusty [all])
Inst gnome-shell (3.10.4-0ubuntu5 Ubuntu:14.04/trusty [i386])
Inst gnome-session (3.9.90-0ubuntu12 Ubuntu:14.04/trusty [all])
Inst mutter (3.10.4-0ubuntu2 Ubuntu:14.04/trusty [i386])
Inst gdm (3.10.0.1-0ubuntu3 Ubuntu:14.04/trusty [i386])
Inst gir1.2-clutter-gst-2.0 (2.0.8-1build1 Ubuntu:14.04/trusty [i386])
Inst gir1.2-evince-3.0 (3.10.3-0ubuntu10 Ubuntu:14.04/trusty [i386])
Inst gir1.2-gtkclutter-1.0 (1.4.4-3ubuntu2 Ubuntu:14.04/trusty [i386])
Inst gir1.2-gtop-2.0 (2.28.5-2 Ubuntu:14.04/trusty [i386])
Inst gir1.2-rest-0.7 (0.7.90-0ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libiptcdata0 (1.0.4-3ubuntu3 Ubuntu:14.04/trusty [i386])
Inst libtracker-sparql-0.16-0 (0.16.2-1ubuntu4 Ubuntu:14.04/trusty [i386])
Inst libtracker-extract-0.16-0 (0.16.2-1ubuntu4 Ubuntu:14.04/trusty [i386])
Inst libtracker-miner-0.16-0 (0.16.2-1ubuntu4 Ubuntu:14.04/trusty [i386])
Inst gir1.2-tracker-0.16 (0.16.2-1ubuntu4 Ubuntu:14.04/trusty [i386])
Inst libzapojit-0.0-0 (0.0.3-1ubuntu1 Ubuntu:14.04/trusty [i386])
Inst gir1.2-zpj-0.0 (0.0.3-1ubuntu1 Ubuntu:14.04/trusty [i386])
Inst gnome-backgrounds (3.12.0-1 Ubuntu:14.04/trusty [all])
Inst gnome-color-manager (3.8.3-1ubuntu1 Ubuntu:14.04/trusty [i386])
Inst gnome-control-center-data (1:3.6.3-0ubuntu56 Ubuntu:14.04/trusty [all])
Inst gnome-control-center (1:3.6.3-0ubuntu56 Ubuntu:14.04/trusty [i386])
Inst tracker (0.16.2-1ubuntu4 Ubuntu:14.04/trusty [i386])
Inst libgupnp-av-1.0-2 (0.12.5-1ubuntu1 Ubuntu:14.04/trusty [i386])
Inst grilo-plugins-0.2 (0.2.12-2 Ubuntu:14.04/trusty [i386])
Inst gnome-online-miners (3.10.3-0ubuntu3 Ubuntu:14.04/trusty [i386])
Inst gnome-documents (3.10.2-0ubuntu1 Ubuntu:14.04/trusty [i386])
Inst gnome-icon-theme-extras (3.12.0-1ubuntu1 Ubuntu:14.04/trusty [all])
Inst gnome-online-accounts (3.10.3-0ubuntu1 Ubuntu:14.04/trusty [i386])
Inst gnome-shell-extensions (3.10.1-0ubuntu2 Ubuntu:14.04/trusty [all])
Inst gnome-tweak-tool (3.10.1-2ubuntu1 Ubuntu:14.04/trusty [all])
Inst gtk2-engines-pixbuf (2.24.23-0ubuntu1 Ubuntu:14.04/trusty [i386])
Inst gvfs-backends-goa (1.20.1-1ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libencode-locale-perl (1.03-1 Ubuntu:14.04/trusty [all])
Inst liberror-perl (0.17-1.1 Ubuntu:14.04/trusty [all])
Inst libhttp-date-perl (6.02-1 Ubuntu:14.04/trusty [all])
Inst libfile-listing-perl (6.04-1 Ubuntu:14.04/trusty [all])
Inst libfont-afm-perl (1.20-1 Ubuntu:14.04/trusty [all])
Inst libgsf-1-common (1.14.27-2ubuntu2 Ubuntu:14.04/trusty [all])
Inst libgsf-1-114 (1.14.27-2ubuntu2 Ubuntu:14.04/trusty [i386])
Inst libhtml-tagset-perl (3.20-2 Ubuntu:14.04/trusty [all])
Inst libhtml-parser-perl (3.71-1build1 Ubuntu:14.04/trusty [i386])
Inst libio-html-perl (1.00-1 Ubuntu:14.04/trusty [all])
Inst liblwp-mediatypes-perl (6.02-1 Ubuntu:14.04/trusty [all])
Inst libhttp-message-perl (6.06-1 Ubuntu:14.04/trusty [all])
Inst libhtml-form-perl (6.03-1 Ubuntu:14.04/trusty [all])
Inst libhtml-tree-perl (5.03-1 Ubuntu:14.04/trusty [all])
Inst libhtml-format-perl (2.11-1 Ubuntu:14.04/trusty [all])
Inst libhttp-cookies-perl (6.00-2 Ubuntu:14.04/trusty [all])
Inst libhttp-daemon-perl (6.01-1 Ubuntu:14.04/trusty [all])
Inst libhttp-negotiate-perl (6.00-2 Ubuntu:14.04/trusty [all])
Inst libnet-http-perl (6.06-1 Ubuntu:14.04/trusty [all])
Inst libwww-robotrules-perl (6.01-1 Ubuntu:14.04/trusty [all])
Inst libwww-perl (6.05-2 Ubuntu:14.04/trusty [all]) []
Inst liblwp-protocol-https-perl (6.04-2 Ubuntu:14.04/trusty [all])
Inst libnetaddr-ip-perl (4.071+dfsg-1 Ubuntu:14.04/trusty [i386])
Inst libmail-spf-perl (2.9.0-2 Ubuntu:14.04/trusty [all])
Inst libreoffice-style-tango (1:4.2.3~rc3-0ubuntu2 Ubuntu:14.04/trusty [all])
Inst libsys-hostname-long-perl (1.4-3 Ubuntu:14.04/trusty [all])
Inst libxml2-utils (2.9.1+dfsg1-3ubuntu4 Ubuntu:14.04/trusty [i386])
Inst mcp-account-manager-goa (3.8.6-0ubuntu9 Ubuntu:14.04/trusty [i386])
Inst notification-daemon (0.7.6-1 Ubuntu:14.04/trusty [i386])
Inst plymouth-theme-ubuntu-gnome-logo (14.04.1 Ubuntu:14.04/trusty [all])
Inst plymouth-theme-ubuntu-gnome-text (14.04.1 Ubuntu:14.04/trusty [all])
Inst software-properties-common [0.92.36] (0.92.37 Ubuntu:14.04/trusty-updates [all]) []
Inst software-properties-gtk [0.92.36] (0.92.37 Ubuntu:14.04/trusty-updates [all]) []
Inst python3-software-properties [0.92.36] (0.92.37 Ubuntu:14.04/trusty-updates [all])
Inst re2c (0.13.5-1build2 Ubuntu:14.04/trusty [i386])
Inst spamassassin (3.4.0-1ubuntu1 Ubuntu:14.04/trusty [all])
Inst sa-compile (3.4.0-1ubuntu1 Ubuntu:14.04/trusty [all])
Inst spamc (3.4.0-1ubuntu1 Ubuntu:14.04/trusty [i386])
Inst tracker-extract (0.16.2-1ubuntu4 Ubuntu:14.04/trusty [i386])
Inst tracker-miner-fs (0.16.2-1ubuntu4 Ubuntu:14.04/trusty [i386])
Inst tracker-utils (0.16.2-1ubuntu4 Ubuntu:14.04/trusty [i386])
Inst ubuntu-gnome-default-settings (14.04.1 Ubuntu:14.04/trusty [all])
Inst gnome-sushi (3.11.90-0ubuntu1 Ubuntu:14.04/trusty [i386])
Inst itstool (2.0.2-2 Ubuntu:14.04/trusty [all])
Inst xsltproc (1.1.28-2build1 Ubuntu:14.04/trusty [i386])
Inst yelp-tools (3.10.0-1 Ubuntu:14.04/trusty [all])
Inst zsync (0.6.2-1ubuntu1 Ubuntu:14.04/trusty [i386])
Inst ubuntu-gnome-desktop (0.32 Ubuntu:14.04/trusty [i386])
Inst ubuntu-gnome-wallpapers-trusty (14.04.1 Ubuntu:14.04/trusty [all])
Inst ubuntu-gnome-wallpapers (14.04.1 Ubuntu:14.04/trusty [all])
Inst xserver-xephyr (2:1.15.1-0ubuntu2 Ubuntu:14.04/trusty [i386])
Inst evolution-indicator (0.2.20-0ubuntu15 Ubuntu:14.04/trusty [i386])
Inst unoconv (0.6-6 Ubuntu:14.04/trusty [all])
Conf libgtkhtml-4.0-common (4.6.6-2ubuntu1 Ubuntu:14.04/trusty [all])
Conf libgtkhtml-4.0-0 (4.6.6-2ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libgtkhtml-editor-4.0-0 (4.6.6-2ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libytnef0 (1.5-6 Ubuntu:14.04/trusty [i386])
Conf libevolution (3.10.4-0ubuntu1 Ubuntu:14.04/trusty [i386])
Conf evolution-common (3.10.4-0ubuntu1 Ubuntu:14.04/trusty [all])
Conf evolution (3.10.4-0ubuntu1 Ubuntu:14.04/trusty [i386])
Conf gnome-themes-standard-data (3.10.0-1ubuntu2 Ubuntu:14.04/trusty [all])
Conf gnome-themes-standard (3.10.0-1ubuntu2 Ubuntu:14.04/trusty [i386])
Conf libcaribou-common (0.4.13-0ubuntu1 Ubuntu:14.04/trusty [all])
Conf libcaribou0 (0.4.13-0ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libcolord-gtk1 (0.1.25-1.1 Ubuntu:14.04/trusty [i386])
Conf libgdm1 (3.10.0.1-0ubuntu3 Ubuntu:14.04/trusty [i386])
Conf libgif4 (4.1.6-11 Ubuntu:14.04/trusty [i386])
Conf libgoa-backend-1.0-1 (3.10.3-0ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libgrilo-0.2-1 (0.2.10-1 Ubuntu:14.04/trusty [i386])
Conf libimdi0 (1.5.1-5ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libmediaart-1.0-0 (0.4.0-1ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libpst4 (0.6.59-1build1 Ubuntu:14.04/trusty [i386])
Conf libxcb-xf86dri0 (1.10-2ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libxcb-xv0 (1.10-2ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libicc2 (2.12+argyll1.5.1-5ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libmusicbrainz5-0 (5.0.1-2 Ubuntu:14.04/trusty [i386])
Conf libnss-myhostname (0.3-6 Ubuntu:14.04/trusty [i386])
Conf libxcb-keysyms1 (0.3.9-1ubuntu1 Ubuntu:14.04/trusty [i386])
Conf python-cloudfiles (1.7.11-2build1 Ubuntu:14.04/trusty [all])
Conf argyll (1.5.1-5ubuntu1 Ubuntu:14.04/trusty [i386])
Conf dconf-editor (0.20.0-1 Ubuntu:14.04/trusty [i386])
Conf deja-dup-backend-cloudfiles (30.0-0ubuntu4 Ubuntu:14.04/trusty [all])
Conf python-urllib3 (1.7.1-1build1 Ubuntu:14.04/trusty [all])
Conf python-requests (2.2.1-1 Ubuntu:14.04/trusty [all])
Conf python-boto (2.20.1-2ubuntu2 Ubuntu:14.04/trusty [all])
Conf deja-dup-backend-s3 (30.0-0ubuntu4 Ubuntu:14.04/trusty [all])
Conf evolution-plugins (3.10.4-0ubuntu1 Ubuntu:14.04/trusty [i386])
Conf fonts-cantarell (0.0.15-1 Ubuntu:14.04/trusty [all])
Conf gir1.2-gdm-1.0 (3.10.0.1-0ubuntu3 Ubuntu:14.04/trusty [i386])
Conf gnome-settings-daemon (3.8.6.1-0ubuntu11 Ubuntu:14.04/trusty [i386])
Conf gir1.2-cogl-1.0 (1.16.2-1 Ubuntu:14.04/trusty [i386])
Conf gir1.2-coglpango-1.0 (1.16.2-1 Ubuntu:14.04/trusty [i386])
Conf gir1.2-json-1.0 (0.16.2-1ubuntu1 Ubuntu:14.04/trusty [i386])
Conf gir1.2-clutter-1.0 (1.16.4-0ubuntu2 Ubuntu:14.04/trusty [i386])
Conf gir1.2-gdesktopenums-3.0 (3.10.1-0ubuntu1 Ubuntu:14.04/trusty [i386])
Conf mutter-common (3.10.4-0ubuntu2 Ubuntu:14.04/trusty [all])
Conf libmutter0c (3.10.4-0ubuntu2 Ubuntu:14.04/trusty [i386])
Conf gir1.2-mutter-3.0 (3.10.4-0ubuntu2 Ubuntu:14.04/trusty [i386])
Conf gir1.2-telepathyglib-0.12 (0.22.1-1ubuntu2 Ubuntu:14.04/trusty [i386])
Conf gnome-icon-theme-full (3.10.0-0ubuntu2 Ubuntu:14.04/trusty [all])
Conf libmozjs-24-0 (24.2.0-1 Ubuntu:14.04/trusty [i386])
Conf libgjs0e (1.39.91-0ubuntu1 Ubuntu:14.04/trusty [i386])
Conf gir1.2-accountsservice-1.0 (0.6.35-0ubuntu7 Ubuntu:14.04/trusty [i386])
Conf gir1.2-caribou-1.0 (0.4.13-0ubuntu1 Ubuntu:14.04/trusty [i386])
Conf gir1.2-gck-1 (3.10.1-1 Ubuntu:14.04/trusty [i386])
Conf gir1.2-gcr-3 (3.10.1-1 Ubuntu:14.04/trusty [i386])
Conf gir1.2-xkl-1.0 (5.4-0ubuntu1 Ubuntu:14.04/trusty [i386])
Conf gir1.2-gkbd-3.0 (3.6.0-0ubuntu2 Ubuntu:14.04/trusty [i386])
Conf gir1.2-gnomedesktop-3.0 (3.8.4-0ubuntu3 Ubuntu:14.04/trusty [i386])
Conf gir1.2-nmgtk-1.0 (0.9.8.8-0ubuntu4 Ubuntu:14.04/trusty [i386])
Conf gir1.2-polkit-1.0 (0.105-4ubuntu2 Ubuntu:14.04/trusty [i386])
Conf gir1.2-telepathylogger-0.2 (0.8.0-3 Ubuntu:14.04/trusty [i386])
Conf gir1.2-upowerglib-1.0 (0.9.23-2ubuntu1 Ubuntu:14.04/trusty [i386])
Conf gjs (1.39.91-0ubuntu1 Ubuntu:14.04/trusty [i386])
Conf gnome-shell-common (3.10.4-0ubuntu5 Ubuntu:14.04/trusty [all])
Conf gnome-shell (3.10.4-0ubuntu5 Ubuntu:14.04/trusty [i386])
Conf gnome-session (3.9.90-0ubuntu12 Ubuntu:14.04/trusty [all])
Conf mutter (3.10.4-0ubuntu2 Ubuntu:14.04/trusty [i386])
Conf gdm (3.10.0.1-0ubuntu3 Ubuntu:14.04/trusty [i386])
Conf gir1.2-clutter-gst-2.0 (2.0.8-1build1 Ubuntu:14.04/trusty [i386])
Conf gir1.2-evince-3.0 (3.10.3-0ubuntu10 Ubuntu:14.04/trusty [i386])
Conf gir1.2-gtkclutter-1.0 (1.4.4-3ubuntu2 Ubuntu:14.04/trusty [i386])
Conf gir1.2-gtop-2.0 (2.28.5-2 Ubuntu:14.04/trusty [i386])
Conf gir1.2-rest-0.7 (0.7.90-0ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libiptcdata0 (1.0.4-3ubuntu3 Ubuntu:14.04/trusty [i386])
Conf libtracker-sparql-0.16-0 (0.16.2-1ubuntu4 Ubuntu:14.04/trusty [i386])
Conf libtracker-extract-0.16-0 (0.16.2-1ubuntu4 Ubuntu:14.04/trusty [i386])
Conf libtracker-miner-0.16-0 (0.16.2-1ubuntu4 Ubuntu:14.04/trusty [i386])
Conf gir1.2-tracker-0.16 (0.16.2-1ubuntu4 Ubuntu:14.04/trusty [i386])
Conf libzapojit-0.0-0 (0.0.3-1ubuntu1 Ubuntu:14.04/trusty [i386])
Conf gir1.2-zpj-0.0 (0.0.3-1ubuntu1 Ubuntu:14.04/trusty [i386])
Conf gnome-backgrounds (3.12.0-1 Ubuntu:14.04/trusty [all])
Conf gnome-color-manager (3.8.3-1ubuntu1 Ubuntu:14.04/trusty [i386])
Conf gnome-control-center-data (1:3.6.3-0ubuntu56 Ubuntu:14.04/trusty [all])
Conf gnome-control-center (1:3.6.3-0ubuntu56 Ubuntu:14.04/trusty [i386])
Conf tracker (0.16.2-1ubuntu4 Ubuntu:14.04/trusty [i386])
Conf libgupnp-av-1.0-2 (0.12.5-1ubuntu1 Ubuntu:14.04/trusty [i386])
Conf grilo-plugins-0.2 (0.2.12-2 Ubuntu:14.04/trusty [i386])
Conf gnome-online-miners (3.10.3-0ubuntu3 Ubuntu:14.04/trusty [i386])
Conf gnome-documents (3.10.2-0ubuntu1 Ubuntu:14.04/trusty [i386])
Conf gnome-icon-theme-extras (3.12.0-1ubuntu1 Ubuntu:14.04/trusty [all])
Conf gnome-online-accounts (3.10.3-0ubuntu1 Ubuntu:14.04/trusty [i386])
Conf gnome-shell-extensions (3.10.1-0ubuntu2 Ubuntu:14.04/trusty [all])
Conf gnome-tweak-tool (3.10.1-2ubuntu1 Ubuntu:14.04/trusty [all])
Conf gtk2-engines-pixbuf (2.24.23-0ubuntu1 Ubuntu:14.04/trusty [i386])
Conf gvfs-backends-goa (1.20.1-1ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libencode-locale-perl (1.03-1 Ubuntu:14.04/trusty [all])
Conf liberror-perl (0.17-1.1 Ubuntu:14.04/trusty [all])
Conf libhttp-date-perl (6.02-1 Ubuntu:14.04/trusty [all])
Conf libfile-listing-perl (6.04-1 Ubuntu:14.04/trusty [all])
Conf libfont-afm-perl (1.20-1 Ubuntu:14.04/trusty [all])
Conf libgsf-1-common (1.14.27-2ubuntu2 Ubuntu:14.04/trusty [all])
Conf libgsf-1-114 (1.14.27-2ubuntu2 Ubuntu:14.04/trusty [i386])
Conf libhtml-tagset-perl (3.20-2 Ubuntu:14.04/trusty [all])
Conf libhtml-parser-perl (3.71-1build1 Ubuntu:14.04/trusty [i386])
Conf libio-html-perl (1.00-1 Ubuntu:14.04/trusty [all])
Conf liblwp-mediatypes-perl (6.02-1 Ubuntu:14.04/trusty [all])
Conf libhttp-message-perl (6.06-1 Ubuntu:14.04/trusty [all])
Conf libhtml-form-perl (6.03-1 Ubuntu:14.04/trusty [all])
Conf libhtml-tree-perl (5.03-1 Ubuntu:14.04/trusty [all])
Conf libhtml-format-perl (2.11-1 Ubuntu:14.04/trusty [all])
Conf libhttp-cookies-perl (6.00-2 Ubuntu:14.04/trusty [all])
Conf libhttp-daemon-perl (6.01-1 Ubuntu:14.04/trusty [all])
Conf libhttp-negotiate-perl (6.00-2 Ubuntu:14.04/trusty [all])
Conf libnet-http-perl (6.06-1 Ubuntu:14.04/trusty [all])
Conf libwww-robotrules-perl (6.01-1 Ubuntu:14.04/trusty [all])
Conf libwww-perl (6.05-2 Ubuntu:14.04/trusty [all])
Conf liblwp-protocol-https-perl (6.04-2 Ubuntu:14.04/trusty [all])
Conf libnetaddr-ip-perl (4.071+dfsg-1 Ubuntu:14.04/trusty [i386])
Conf libmail-spf-perl (2.9.0-2 Ubuntu:14.04/trusty [all])
Conf libreoffice-style-tango (1:4.2.3~rc3-0ubuntu2 Ubuntu:14.04/trusty [all])
Conf libsys-hostname-long-perl (1.4-3 Ubuntu:14.04/trusty [all])
Conf libxml2-utils (2.9.1+dfsg1-3ubuntu4 Ubuntu:14.04/trusty [i386])
Conf mcp-account-manager-goa (3.8.6-0ubuntu9 Ubuntu:14.04/trusty [i386])
Conf notification-daemon (0.7.6-1 Ubuntu:14.04/trusty [i386])
Conf plymouth-theme-ubuntu-gnome-logo (14.04.1 Ubuntu:14.04/trusty [all])
Conf plymouth-theme-ubuntu-gnome-text (14.04.1 Ubuntu:14.04/trusty [all])
Conf python3-software-properties (0.92.37 Ubuntu:14.04/trusty-updates [all])
Conf software-properties-common (0.92.37 Ubuntu:14.04/trusty-updates [all])
Conf software-properties-gtk (0.92.37 Ubuntu:14.04/trusty-updates [all])
Conf re2c (0.13.5-1build2 Ubuntu:14.04/trusty [i386])
Conf spamassassin (3.4.0-1ubuntu1 Ubuntu:14.04/trusty [all])
Conf sa-compile (3.4.0-1ubuntu1 Ubuntu:14.04/trusty [all])
Conf spamc (3.4.0-1ubuntu1 Ubuntu:14.04/trusty [i386])
Conf tracker-extract (0.16.2-1ubuntu4 Ubuntu:14.04/trusty [i386])
Conf tracker-miner-fs (0.16.2-1ubuntu4 Ubuntu:14.04/trusty [i386])
Conf tracker-utils (0.16.2-1ubuntu4 Ubuntu:14.04/trusty [i386])
Conf ubuntu-gnome-default-settings (14.04.1 Ubuntu:14.04/trusty [all])
Conf gnome-sushi (3.11.90-0ubuntu1 Ubuntu:14.04/trusty [i386])
Conf itstool (2.0.2-2 Ubuntu:14.04/trusty [all])
Conf xsltproc (1.1.28-2build1 Ubuntu:14.04/trusty [i386])
Conf yelp-tools (3.10.0-1 Ubuntu:14.04/trusty [all])
Conf zsync (0.6.2-1ubuntu1 Ubuntu:14.04/trusty [i386])
Conf ubuntu-gnome-desktop (0.32 Ubuntu:14.04/trusty [i386])
Conf ubuntu-gnome-wallpapers-trusty (14.04.1 Ubuntu:14.04/trusty [all])
Conf ubuntu-gnome-wallpapers (14.04.1 Ubuntu:14.04/trusty [all])
Conf xserver-xephyr (2:1.15.1-0ubuntu2 Ubuntu:14.04/trusty [i386])
Conf evolution-indicator (0.2.20-0ubuntu15 Ubuntu:14.04/trusty [i386])
Conf unoconv (0.6-6 Ubuntu:14.04/trusty [all])
```

In order to parse the difference between just installing 'ubuntu-gnome-desktop' without the "^" this will be needed:

```
lance@lance-desktop:~$ sudo apt-get install ubuntu-gnome-desktop
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  argyll dconf-editor deja-dup-backend-cloudfiles deja-dup-backend-s3
  evolution evolution-common evolution-indicator evolution-plugins
  fonts-cantarell gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0
  gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-evince-3.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0
  gir1.2-gnomedesktop-3.0 gir1.2-gtkclutter-1.0 gir1.2-gtop-2.0
  gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-nmgtk-1.0 gir1.2-polkit-1.0
  gir1.2-rest-0.7 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-tracker-0.16 gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gir1.2-zpj-0.0 gjs
  gnome-backgrounds gnome-color-manager gnome-control-center
  gnome-control-center-data gnome-documents gnome-icon-theme-extras
  gnome-icon-theme-full gnome-online-accounts gnome-online-miners
  gnome-session gnome-settings-daemon gnome-shell gnome-shell-common
  gnome-shell-extensions gnome-sushi gnome-themes-standard
  gnome-themes-standard-data gnome-tweak-tool grilo-plugins-0.2
  gtk2-engines-pixbuf gvfs-backends-goa itstool libcaribou-common libcaribou0
  libcolord-gtk1 libencode-locale-perl liberror-perl libevolution
  libfile-listing-perl libfont-afm-perl libgdm1 libgif4 libgjs0e
  libgoa-backend-1.0-1 libgrilo-0.2-1 libgsf-1-114 libgsf-1-common
  libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0
  libgupnp-av-1.0-2 libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libicc2 libimdi0 libio-html-perl libiptcdata0
  liblwp-mediatypes-perl liblwp-protocol-https-perl libmail-spf-perl
  libmediaart-1.0-0 libmozjs-24-0 libmusicbrainz5-0 libmutter0c
  libnet-http-perl libnetaddr-ip-perl libnss-myhostname libpst4
  libreoffice-style-tango libsys-hostname-long-perl libtracker-extract-0.16-0
  libtracker-miner-0.16-0 libtracker-sparql-0.16-0 libwww-perl
  libwww-robotrules-perl libxcb-keysyms1 libxcb-xf86dri0 libxcb-xv0
  libxml2-utils libytnef0 libzapojit-0.0-0 mcp-account-manager-goa mutter
  mutter-common plymouth-theme-ubuntu-gnome-logo
  plymouth-theme-ubuntu-gnome-text python-boto python-cloudfiles
  python-requests python-urllib3 re2c sa-compile spamassassin spamc tracker
  tracker-extract tracker-miner-fs tracker-utils ubuntu-gnome-default-settings
  ubuntu-gnome-wallpapers ubuntu-gnome-wallpapers-trusty unoconv
  xserver-xephyr xsltproc yelp-tools zsync
Suggested packages:
  gir1.2-colordgtk-1.0 evolution-ews evolution-plugins-experimental
  desktop-base libdata-dump-perl libcrypt-ssleay-perl tango-icon-theme
  libauthen-ntlm-perl razor libdbi-perl pyzor libmail-dkim-perl tracker-gui
[B][COLOR="#FF0000"]The following NEW packages will be installed:
  argyll dconf-editor deja-dup-backend-cloudfiles deja-dup-backend-s3
  evolution evolution-common evolution-indicator evolution-plugins
  fonts-cantarell gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0
  gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-evince-3.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0
  gir1.2-gnomedesktop-3.0 gir1.2-gtkclutter-1.0 gir1.2-gtop-2.0
  gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-nmgtk-1.0 gir1.2-polkit-1.0
  gir1.2-rest-0.7 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-tracker-0.16 gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gir1.2-zpj-0.0 gjs
  gnome-backgrounds gnome-color-manager gnome-control-center
  gnome-control-center-data gnome-documents gnome-icon-theme-extras
  gnome-icon-theme-full gnome-online-accounts gnome-online-miners
  gnome-session gnome-settings-daemon gnome-shell gnome-shell-common
  gnome-shell-extensions gnome-sushi gnome-themes-standard
  gnome-themes-standard-data gnome-tweak-tool grilo-plugins-0.2
  gtk2-engines-pixbuf gvfs-backends-goa itstool libcaribou-common libcaribou0
  libcolord-gtk1 libencode-locale-perl liberror-perl libevolution
  libfile-listing-perl libfont-afm-perl libgdm1 libgif4 libgjs0e
  libgoa-backend-1.0-1 libgrilo-0.2-1 libgsf-1-114 libgsf-1-common
  libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0
  libgupnp-av-1.0-2 libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libicc2 libimdi0 libio-html-perl libiptcdata0
  liblwp-mediatypes-perl liblwp-protocol-https-perl libmail-spf-perl
  libmediaart-1.0-0 libmozjs-24-0 libmusicbrainz5-0 libmutter0c
  libnet-http-perl libnetaddr-ip-perl libnss-myhostname libpst4
  libreoffice-style-tango libsys-hostname-long-perl libtracker-extract-0.16-0
  libtracker-miner-0.16-0 libtracker-sparql-0.16-0 libwww-perl
  libwww-robotrules-perl libxcb-keysyms1 libxcb-xf86dri0 libxcb-xv0
  libxml2-utils libytnef0 libzapojit-0.0-0 mcp-account-manager-goa mutter
  mutter-common plymouth-theme-ubuntu-gnome-logo
  plymouth-theme-ubuntu-gnome-text python-boto python-cloudfiles
  python-requests python-urllib3 re2c sa-compile spamassassin spamc tracker
  tracker-extract tracker-miner-fs tracker-utils ubuntu-gnome-default-settings
  ubuntu-gnome-desktop ubuntu-gnome-wallpapers ubuntu-gnome-wallpapers-trusty
  unoconv xserver-xephyr xsltproc yelp-tools zsync
0 upgraded, 142 newly installed, 0 to remove and 3 not upgraded.
Need to get 58.2 MB of archives.
After this operation, 162 MB of additional disk space will be used.[/COLOR][/B]
Do you want to continue? [Y/n] n
Abort.

```

I'll try to "diff -u" that later, but now it's time to blow something up :twisted:

I found the difference;

With "^" installs 'notification-daemon'.

Without "^" does not install 'notification-daemon'.

I see now that 'notification-daemon' is used by both Ubuntu GNOME and the flashback sessions, but not by Ubuntu itself.

---

### Post by kansasnoob on 2014-05-05
Just to be certain I changed the package order on that first command:

```
lance@lance-desktop:~$ sudo apt-get remove ubuntu-desktop ubuntu-default-settings
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'ubuntu-default-settings' can't be removed
The following packages will be REMOVED:
  ubuntu-desktop
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
After this operation, 61.4 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 164898 files and directories currently installed.)
Removing ubuntu-desktop (1.325) ...

```

No change :)

---

### Post by kansasnoob on 2014-05-05
No surprise being prompted to change dispaly managers:

[ATTACH=CONFIG]252885[/ATTACH]   [ATTACH=CONFIG]252886[/ATTACH]

Applicable bits from /var/log/apt/history.log:

```
Start-Date: 2014-05-05  09:00:45
Commandline: apt-get install ubuntu-gnome-desktop^
Install: gir1.2-upowerglib-1.0:i386 (0.9.23-2ubuntu1), libtracker-extract-0.16-0:i386 (0.16.2-1ubuntu4), libgtkhtml-4.0-common:i386 (4.6.6-2ubuntu1), libpst4:i386 (0.6.59-1build1), gir1.2-telepathylogger-0.2:i386 (0.8.0-3), gnome-control-center:i386 (3.6.3-0ubuntu56), libtracker-sparql-0.16-0:i386 (0.16.2-1ubuntu4), libtracker-miner-0.16-0:i386 (0.16.2-1ubuntu4), mcp-account-manager-goa:i386 (3.8.6-0ubuntu9), gnome-sushi:i386 (3.11.90-0ubuntu1), libsys-hostname-long-perl:i386 (1.4-3), ubuntu-gnome-desktop:i386 (0.32), liblwp-mediatypes-perl:i386 (6.02-1), evolution-indicator:i386 (0.2.20-0ubuntu15), libfont-afm-perl:i386 (1.20-1), libhtml-form-perl:i386 (6.03-1), gir1.2-gcr-3:i386 (3.10.1-1), gnome-control-center-data:i386 (3.6.3-0ubuntu56), libhttp-message-perl:i386 (6.06-1), gir1.2-gdesktopenums-3.0:i386 (3.10.1-0ubuntu1), gnome-documents:i386 (3.10.2-0ubuntu1), gnome-color-manager:i386 (3.8.3-1ubuntu1), evolution-common:i386 (3.10.4-0ubuntu1), spamc:i386 (3.4.0-1ubuntu1), tracker:i386 (0.16.2-1ubuntu4), libfile-listing-perl:i386 (6.04-1), libreoffice-style-tango:i386 (4.2.3~rc3-0ubuntu2), gnome-themes-standard:i386 (3.10.0-1ubuntu2), gir1.2-clutter-1.0:i386 (1.16.4-0ubuntu2), gir1.2-evince-3.0:i386 (3.10.3-0ubuntu10), libgrilo-0.2-1:i386 (0.2.10-1), plymouth-theme-ubuntu-gnome-text:i386 (14.04.1), evolution:i386 (3.10.4-0ubuntu1), gnome-icon-theme-extras:i386 (3.12.0-1ubuntu1), libmozjs-24-0:i386 (24.2.0-1), libiptcdata0:i386 (1.0.4-3ubuntu3), gnome-tweak-tool:i386 (3.10.1-2ubuntu1), gir1.2-rest-0.7:i386 (0.7.90-0ubuntu1), grilo-plugins-0.2:i386 (0.2.12-2), zsync:i386 (0.6.2-1ubuntu1), gir1.2-caribou-1.0:i386 (0.4.13-0ubuntu1), gir1.2-json-1.0:i386 (0.16.2-1ubuntu1), libytnef0:i386 (1.5-6), liberror-perl:i386 (0.17-1.1), libcaribou-common:i386 (0.4.13-0ubuntu1), evolution-plugins:i386 (3.10.4-0ubuntu1), libgtkhtml-4.0-0:i386 (4.6.6-2ubuntu1), ubuntu-gnome-wallpapers:i386 (14.04.1), gir1.2-telepathyglib-0.12:i386 (0.22.1-1ubuntu2), mutter-common:i386 (3.10.4-0ubuntu2), fonts-cantarell:i386 (0.0.15-1), libhttp-cookies-perl:i386 (6.00-2), gir1.2-zpj-0.0:i386 (0.0.3-1ubuntu1), gnome-settings-daemon:i386 (3.8.6.1-0ubuntu11), libwww-perl:i386 (6.05-2), ubuntu-gnome-wallpapers-trusty:i386 (14.04.1), notification-daemon:i386 (0.7.6-1), deja-dup-backend-cloudfiles:i386 (30.0-0ubuntu4), gnome-shell:i386 (3.10.4-0ubuntu5), python-cloudfiles:i386 (1.7.11-2build1), libzapojit-0.0-0:i386 (0.0.3-1ubuntu1), sa-compile:i386 (3.4.0-1ubuntu1), gir1.2-gck-1:i386 (3.10.1-1), deja-dup-backend-s3:i386 (30.0-0ubuntu4), libhttp-negotiate-perl:i386 (6.00-2), libhtml-tree-perl:i386 (5.03-1), xserver-xephyr:i386 (1.15.1-0ubuntu2), gir1.2-cogl-1.0:i386 (1.16.2-1), libgtkhtml-editor-4.0-0:i386 (4.6.6-2ubuntu1), libmediaart-1.0-0:i386 (0.4.0-1ubuntu1), xsltproc:i386 (1.1.28-2build1), libnet-http-perl:i386 (6.06-1), libnss-myhostname:i386 (0.3-6), libmail-spf-perl:i386 (2.9.0-2), gtk2-engines-pixbuf:i386 (2.24.23-0ubuntu1), gnome-online-miners:i386 (3.10.3-0ubuntu3), libhtml-parser-perl:i386 (3.71-1build1), libgsf-1-common:i386 (1.14.27-2ubuntu2), re2c:i386 (0.13.5-1build2), gvfs-backends-goa:i386 (1.20.1-1ubuntu1), gnome-backgrounds:i386 (3.12.0-1), libxml2-utils:i386 (2.9.1+dfsg1-3ubuntu4), gdm:i386 (3.10.0.1-0ubuntu3), itstool:i386 (2.0.2-2), ubuntu-gnome-default-settings:i386 (14.04.1), gnome-shell-common:i386 (3.10.4-0ubuntu5), libgupnp-av-1.0-2:i386 (0.12.5-1ubuntu1), gnome-session:i386 (3.9.90-0ubuntu12), gnome-shell-extensions:i386 (3.10.1-0ubuntu2), gnome-online-accounts:i386 (3.10.3-0ubuntu1), libxcb-keysyms1:i386 (0.3.9-1ubuntu1), tracker-extract:i386 (0.16.2-1ubuntu4), dconf-editor:i386 (0.20.0-1), libicc2:i386 (2.12+argyll1.5.1-5ubuntu1), gnome-themes-standard-data:i386 (3.10.0-1ubuntu2), libnetaddr-ip-perl:i386 (4.071+dfsg-1), gir1.2-nmgtk-1.0:i386 (0.9.8.8-0ubuntu4), gir1.2-gdm-1.0:i386 (3.10.0.1-0ubuntu3), gjs:i386 (1.39.91-0ubuntu1), python-urllib3:i386 (1.7.1-1build1), libhttp-date-perl:i386 (6.02-1), libmutter0c:i386 (3.10.4-0ubuntu2), yelp-tools:i386 (3.10.0-1), libcolord-gtk1:i386 (0.1.25-1.1), unoconv:i386 (0.6-6), libwww-robotrules-perl:i386 (6.01-1), gir1.2-gtop-2.0:i386 (2.28.5-2), python-requests:i386 (2.2.1-1), gir1.2-tracker-0.16:i386 (0.16.2-1ubuntu4), libgoa-backend-1.0-1:i386 (3.10.3-0ubuntu1), tracker-miner-fs:i386 (0.16.2-1ubuntu4), libencode-locale-perl:i386 (1.03-1), libgif4:i386 (4.1.6-11), python-boto:i386 (2.20.1-2ubuntu2), tracker-utils:i386 (0.16.2-1ubuntu4), plymouth-theme-ubuntu-gnome-logo:i386 (14.04.1), libhttp-daemon-perl:i386 (6.01-1), gir1.2-mutter-3.0:i386 (3.10.4-0ubuntu2), libxcb-xv0:i386 (1.10-2ubuntu1), gir1.2-gtkclutter-1.0:i386 (1.4.4-3ubuntu2), argyll:i386 (1.5.1-5ubuntu1), libmusicbrainz5-0:i386 (5.0.1-2), gir1.2-clutter-gst-2.0:i386 (2.0.8-1build1), libhtml-format-perl:i386 (2.11-1), spamassassin:i386 (3.4.0-1ubuntu1), gnome-icon-theme-full:i386 (3.10.0-0ubuntu2), libgjs0e:i386 (1.39.91-0ubuntu1), gir1.2-accountsservice-1.0:i386 (0.6.35-0ubuntu7), gir1.2-polkit-1.0:i386 (0.105-4ubuntu2), mutter:i386 (3.10.4-0ubuntu2), libcaribou0:i386 (0.4.13-0ubuntu1), libevolution:i386 (3.10.4-0ubuntu1), libgdm1:i386 (3.10.0.1-0ubuntu3), libhtml-tagset-perl:i386 (3.20-2), libimdi0:i386 (1.5.1-5ubuntu1), libio-html-perl:i386 (1.00-1), gir1.2-coglpango-1.0:i386 (1.16.2-1), liblwp-protocol-https-perl:i386 (6.04-2), libgsf-1-114:i386 (1.14.27-2ubuntu2), gir1.2-xkl-1.0:i386 (5.4-0ubuntu1), gir1.2-gnomedesktop-3.0:i386 (3.8.4-0ubuntu3), libxcb-xf86dri0:i386 (1.10-2ubuntu1), gir1.2-gkbd-3.0:i386 (3.6.0-0ubuntu2)
Upgrade: software-properties-gtk:i386 (0.92.36, 0.92.37), python3-software-properties:i386 (0.92.36, 0.92.37), software-properties-common:i386 (0.92.36, 0.92.37)
End-Date: 2014-05-05  09:10:43
```

And from /var/log/apt/term.log:

```
Log started: 2014-05-05  09:00:45
Selecting previously unselected package libgtkhtml-4.0-common.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 164896 files and directories currently installed.)
Preparing to unpack .../libgtkhtml-4.0-common_4.6.6-2ubuntu1_all.deb ...
Unpacking libgtkhtml-4.0-common (4.6.6-2ubuntu1) ...
Selecting previously unselected package libgtkhtml-4.0-0.
Preparing to unpack .../libgtkhtml-4.0-0_4.6.6-2ubuntu1_i386.deb ...
Unpacking libgtkhtml-4.0-0 (4.6.6-2ubuntu1) ...
Selecting previously unselected package libgtkhtml-editor-4.0-0.
Preparing to unpack .../libgtkhtml-editor-4.0-0_4.6.6-2ubuntu1_i386.deb ...
Unpacking libgtkhtml-editor-4.0-0 (4.6.6-2ubuntu1) ...
Selecting previously unselected package libytnef0:i386.
Preparing to unpack .../libytnef0_1.5-6_i386.deb ...
Unpacking libytnef0:i386 (1.5-6) ...
Selecting previously unselected package libevolution.
Preparing to unpack .../libevolution_3.10.4-0ubuntu1_i386.deb ...
Unpacking libevolution (3.10.4-0ubuntu1) ...
Selecting previously unselected package evolution-common.
Preparing to unpack .../evolution-common_3.10.4-0ubuntu1_all.deb ...
Unpacking evolution-common (3.10.4-0ubuntu1) ...
Selecting previously unselected package evolution.
Preparing to unpack .../evolution_3.10.4-0ubuntu1_i386.deb ...
Unpacking evolution (3.10.4-0ubuntu1) ...
Selecting previously unselected package gnome-themes-standard-data.
Preparing to unpack .../gnome-themes-standard-data_3.10.0-1ubuntu2_all.deb ...
Unpacking gnome-themes-standard-data (3.10.0-1ubuntu2) ...
Selecting previously unselected package gnome-themes-standard:i386.
Preparing to unpack .../gnome-themes-standard_3.10.0-1ubuntu2_i386.deb ...
Unpacking gnome-themes-standard:i386 (3.10.0-1ubuntu2) ...
Selecting previously unselected package libcaribou-common.
Preparing to unpack .../libcaribou-common_0.4.13-0ubuntu1_all.deb ...
Unpacking libcaribou-common (0.4.13-0ubuntu1) ...
Selecting previously unselected package libcaribou0:i386.
Preparing to unpack .../libcaribou0_0.4.13-0ubuntu1_i386.deb ...
Unpacking libcaribou0:i386 (0.4.13-0ubuntu1) ...
Selecting previously unselected package libcolord-gtk1:i386.
Preparing to unpack .../libcolord-gtk1_0.1.25-1.1_i386.deb ...
Unpacking libcolord-gtk1:i386 (0.1.25-1.1) ...
Selecting previously unselected package libgdm1.
Preparing to unpack .../libgdm1_3.10.0.1-0ubuntu3_i386.deb ...
Unpacking libgdm1 (3.10.0.1-0ubuntu3) ...
Selecting previously unselected package libgif4:i386.
Preparing to unpack .../libgif4_4.1.6-11_i386.deb ...
Unpacking libgif4:i386 (4.1.6-11) ...
Selecting previously unselected package libgoa-backend-1.0-1:i386.
Preparing to unpack .../libgoa-backend-1.0-1_3.10.3-0ubuntu1_i386.deb ...
Unpacking libgoa-backend-1.0-1:i386 (3.10.3-0ubuntu1) ...
Selecting previously unselected package libgrilo-0.2-1:i386.
Preparing to unpack .../libgrilo-0.2-1_0.2.10-1_i386.deb ...
Unpacking libgrilo-0.2-1:i386 (0.2.10-1) ...
Selecting previously unselected package libimdi0:i386.
Preparing to unpack .../libimdi0_1.5.1-5ubuntu1_i386.deb ...
Unpacking libimdi0:i386 (1.5.1-5ubuntu1) ...
Selecting previously unselected package libmediaart-1.0-0:i386.
Preparing to unpack .../libmediaart-1.0-0_0.4.0-1ubuntu1_i386.deb ...
Unpacking libmediaart-1.0-0:i386 (0.4.0-1ubuntu1) ...
Selecting previously unselected package libpst4:i386.
Preparing to unpack .../libpst4_0.6.59-1build1_i386.deb ...
Unpacking libpst4:i386 (0.6.59-1build1) ...
Selecting previously unselected package libxcb-xf86dri0:i386.
Preparing to unpack .../libxcb-xf86dri0_1.10-2ubuntu1_i386.deb ...
Unpacking libxcb-xf86dri0:i386 (1.10-2ubuntu1) ...
Selecting previously unselected package libxcb-xv0:i386.
Preparing to unpack .../libxcb-xv0_1.10-2ubuntu1_i386.deb ...
Unpacking libxcb-xv0:i386 (1.10-2ubuntu1) ...
Selecting previously unselected package libicc2:i386.
Preparing to unpack .../libicc2_2.12+argyll1.5.1-5ubuntu1_i386.deb ...
Unpacking libicc2:i386 (2.12+argyll1.5.1-5ubuntu1) ...
Selecting previously unselected package libmusicbrainz5-0:i386.
Preparing to unpack .../libmusicbrainz5-0_5.0.1-2_i386.deb ...
Unpacking libmusicbrainz5-0:i386 (5.0.1-2) ...
Selecting previously unselected package libnss-myhostname:i386.
Preparing to unpack .../libnss-myhostname_0.3-6_i386.deb ...
Unpacking libnss-myhostname:i386 (0.3-6) ...
Selecting previously unselected package libxcb-keysyms1:i386.
Preparing to unpack .../libxcb-keysyms1_0.3.9-1ubuntu1_i386.deb ...
Unpacking libxcb-keysyms1:i386 (0.3.9-1ubuntu1) ...
Selecting previously unselected package python-cloudfiles.
Preparing to unpack .../python-cloudfiles_1.7.11-2build1_all.deb ...
Unpacking python-cloudfiles (1.7.11-2build1) ...
Selecting previously unselected package argyll.
Preparing to unpack .../argyll_1.5.1-5ubuntu1_i386.deb ...
Unpacking argyll (1.5.1-5ubuntu1) ...
Selecting previously unselected package dconf-editor.
Preparing to unpack .../dconf-editor_0.20.0-1_i386.deb ...
Unpacking dconf-editor (0.20.0-1) ...
Selecting previously unselected package deja-dup-backend-cloudfiles.
Preparing to unpack .../deja-dup-backend-cloudfiles_30.0-0ubuntu4_all.deb ...
Unpacking deja-dup-backend-cloudfiles (30.0-0ubuntu4) ...
Selecting previously unselected package python-urllib3.
Preparing to unpack .../python-urllib3_1.7.1-1build1_all.deb ...
Unpacking python-urllib3 (1.7.1-1build1) ...
Selecting previously unselected package python-requests.
Preparing to unpack .../python-requests_2.2.1-1_all.deb ...
Unpacking python-requests (2.2.1-1) ...
Selecting previously unselected package python-boto.
Preparing to unpack .../python-boto_2.20.1-2ubuntu2_all.deb ...
Unpacking python-boto (2.20.1-2ubuntu2) ...
Selecting previously unselected package deja-dup-backend-s3.
Preparing to unpack .../deja-dup-backend-s3_30.0-0ubuntu4_all.deb ...
Unpacking deja-dup-backend-s3 (30.0-0ubuntu4) ...
Selecting previously unselected package evolution-plugins.
Preparing to unpack .../evolution-plugins_3.10.4-0ubuntu1_i386.deb ...
Unpacking evolution-plugins (3.10.4-0ubuntu1) ...
Selecting previously unselected package fonts-cantarell.
Preparing to unpack .../fonts-cantarell_0.0.15-1_all.deb ...
Unpacking fonts-cantarell (0.0.15-1) ...
Selecting previously unselected package gir1.2-gdm-1.0.
Preparing to unpack .../gir1.2-gdm-1.0_3.10.0.1-0ubuntu3_i386.deb ...
Unpacking gir1.2-gdm-1.0 (3.10.0.1-0ubuntu3) ...
Selecting previously unselected package gnome-settings-daemon.
Preparing to unpack .../gnome-settings-daemon_3.8.6.1-0ubuntu11_i386.deb ...
Unpacking gnome-settings-daemon (3.8.6.1-0ubuntu11) ...
Selecting previously unselected package gir1.2-cogl-1.0.
Preparing to unpack .../gir1.2-cogl-1.0_1.16.2-1_i386.deb ...
Unpacking gir1.2-cogl-1.0 (1.16.2-1) ...
Selecting previously unselected package gir1.2-coglpango-1.0.
Preparing to unpack .../gir1.2-coglpango-1.0_1.16.2-1_i386.deb ...
Unpacking gir1.2-coglpango-1.0 (1.16.2-1) ...
Selecting previously unselected package gir1.2-json-1.0.
Preparing to unpack .../gir1.2-json-1.0_0.16.2-1ubuntu1_i386.deb ...
Unpacking gir1.2-json-1.0 (0.16.2-1ubuntu1) ...
Selecting previously unselected package gir1.2-clutter-1.0.
Preparing to unpack .../gir1.2-clutter-1.0_1.16.4-0ubuntu2_i386.deb ...
Unpacking gir1.2-clutter-1.0 (1.16.4-0ubuntu2) ...
Selecting previously unselected package gir1.2-gdesktopenums-3.0.
Preparing to unpack .../gir1.2-gdesktopenums-3.0_3.10.1-0ubuntu1_i386.deb ...
Unpacking gir1.2-gdesktopenums-3.0 (3.10.1-0ubuntu1) ...
Selecting previously unselected package mutter-common.
Preparing to unpack .../mutter-common_3.10.4-0ubuntu2_all.deb ...
Unpacking mutter-common (3.10.4-0ubuntu2) ...
Selecting previously unselected package libmutter0c.
Preparing to unpack .../libmutter0c_3.10.4-0ubuntu2_i386.deb ...
Unpacking libmutter0c (3.10.4-0ubuntu2) ...
Selecting previously unselected package gir1.2-mutter-3.0.
Preparing to unpack .../gir1.2-mutter-3.0_3.10.4-0ubuntu2_i386.deb ...
Unpacking gir1.2-mutter-3.0 (3.10.4-0ubuntu2) ...
Selecting previously unselected package gir1.2-telepathyglib-0.12.
Preparing to unpack .../gir1.2-telepathyglib-0.12_0.22.1-1ubuntu2_i386.deb ...
Unpacking gir1.2-telepathyglib-0.12 (0.22.1-1ubuntu2) ...
Selecting previously unselected package gnome-icon-theme-full.
Preparing to unpack .../gnome-icon-theme-full_3.10.0-0ubuntu2_all.deb ...
Unpacking gnome-icon-theme-full (3.10.0-0ubuntu2) ...
Selecting previously unselected package libmozjs-24-0.
Preparing to unpack .../libmozjs-24-0_24.2.0-1_i386.deb ...
Unpacking libmozjs-24-0 (24.2.0-1) ...
Selecting previously unselected package libgjs0e.
Preparing to unpack .../libgjs0e_1.39.91-0ubuntu1_i386.deb ...
Unpacking libgjs0e (1.39.91-0ubuntu1) ...
Selecting previously unselected package gir1.2-accountsservice-1.0.
Preparing to unpack .../gir1.2-accountsservice-1.0_0.6.35-0ubuntu7_i386.deb ...
Unpacking gir1.2-accountsservice-1.0 (0.6.35-0ubuntu7) ...
Selecting previously unselected package gir1.2-caribou-1.0.
Preparing to unpack .../gir1.2-caribou-1.0_0.4.13-0ubuntu1_i386.deb ...
Unpacking gir1.2-caribou-1.0 (0.4.13-0ubuntu1) ...
Selecting previously unselected package gir1.2-gck-1.
Preparing to unpack .../gir1.2-gck-1_3.10.1-1_i386.deb ...
Unpacking gir1.2-gck-1 (3.10.1-1) ...
Selecting previously unselected package gir1.2-gcr-3.
Preparing to unpack .../gir1.2-gcr-3_3.10.1-1_i386.deb ...
Unpacking gir1.2-gcr-3 (3.10.1-1) ...
Selecting previously unselected package gir1.2-xkl-1.0.
Preparing to unpack .../gir1.2-xkl-1.0_5.4-0ubuntu1_i386.deb ...
Unpacking gir1.2-xkl-1.0 (5.4-0ubuntu1) ...
Selecting previously unselected package gir1.2-gkbd-3.0.
Preparing to unpack .../gir1.2-gkbd-3.0_3.6.0-0ubuntu2_i386.deb ...
Unpacking gir1.2-gkbd-3.0 (3.6.0-0ubuntu2) ...
Selecting previously unselected package gir1.2-gnomedesktop-3.0.
Preparing to unpack .../gir1.2-gnomedesktop-3.0_3.8.4-0ubuntu3_i386.deb ...
Unpacking gir1.2-gnomedesktop-3.0 (3.8.4-0ubuntu3) ...
Selecting previously unselected package gir1.2-nmgtk-1.0.
Preparing to unpack .../gir1.2-nmgtk-1.0_0.9.8.8-0ubuntu4_i386.deb ...
Unpacking gir1.2-nmgtk-1.0 (0.9.8.8-0ubuntu4) ...
Selecting previously unselected package gir1.2-polkit-1.0.
Preparing to unpack .../gir1.2-polkit-1.0_0.105-4ubuntu2_i386.deb ...
Unpacking gir1.2-polkit-1.0 (0.105-4ubuntu2) ...
Selecting previously unselected package gir1.2-telepathylogger-0.2.
Preparing to unpack .../gir1.2-telepathylogger-0.2_0.8.0-3_i386.deb ...
Unpacking gir1.2-telepathylogger-0.2 (0.8.0-3) ...
Selecting previously unselected package gir1.2-upowerglib-1.0.
Preparing to unpack .../gir1.2-upowerglib-1.0_0.9.23-2ubuntu1_i386.deb ...
Unpacking gir1.2-upowerglib-1.0 (0.9.23-2ubuntu1) ...
Selecting previously unselected package gjs.
Preparing to unpack .../gjs_1.39.91-0ubuntu1_i386.deb ...
Unpacking gjs (1.39.91-0ubuntu1) ...
Selecting previously unselected package gnome-shell-common.
Preparing to unpack .../gnome-shell-common_3.10.4-0ubuntu5_all.deb ...
Unpacking gnome-shell-common (3.10.4-0ubuntu5) ...
Selecting previously unselected package gnome-shell.
Preparing to unpack .../gnome-shell_3.10.4-0ubuntu5_i386.deb ...
Unpacking gnome-shell (3.10.4-0ubuntu5) ...
Selecting previously unselected package gnome-session.
Preparing to unpack .../gnome-session_3.9.90-0ubuntu12_all.deb ...
Unpacking gnome-session (3.9.90-0ubuntu12) ...
Selecting previously unselected package mutter.
Preparing to unpack .../mutter_3.10.4-0ubuntu2_i386.deb ...
Unpacking mutter (3.10.4-0ubuntu2) ...
Selecting previously unselected package gdm.
Preparing to unpack .../gdm_3.10.0.1-0ubuntu3_i386.deb ...
Unpacking gdm (3.10.0.1-0ubuntu3) ...
Selecting previously unselected package gir1.2-clutter-gst-2.0.
Preparing to unpack .../gir1.2-clutter-gst-2.0_2.0.8-1build1_i386.deb ...
Unpacking gir1.2-clutter-gst-2.0 (2.0.8-1build1) ...
Selecting previously unselected package gir1.2-evince-3.0.
Preparing to unpack .../gir1.2-evince-3.0_3.10.3-0ubuntu10_i386.deb ...
Unpacking gir1.2-evince-3.0 (3.10.3-0ubuntu10) ...
Selecting previously unselected package gir1.2-gtkclutter-1.0.
Preparing to unpack .../gir1.2-gtkclutter-1.0_1.4.4-3ubuntu2_i386.deb ...
Unpacking gir1.2-gtkclutter-1.0 (1.4.4-3ubuntu2) ...
Selecting previously unselected package gir1.2-gtop-2.0.
Preparing to unpack .../gir1.2-gtop-2.0_2.28.5-2_i386.deb ...
Unpacking gir1.2-gtop-2.0 (2.28.5-2) ...
Selecting previously unselected package gir1.2-rest-0.7.
Preparing to unpack .../gir1.2-rest-0.7_0.7.90-0ubuntu1_i386.deb ...
Unpacking gir1.2-rest-0.7 (0.7.90-0ubuntu1) ...
Selecting previously unselected package libiptcdata0.
Preparing to unpack .../libiptcdata0_1.0.4-3ubuntu3_i386.deb ...
Unpacking libiptcdata0 (1.0.4-3ubuntu3) ...
Selecting previously unselected package libtracker-sparql-0.16-0.
Preparing to unpack .../libtracker-sparql-0.16-0_0.16.2-1ubuntu4_i386.deb ...
Unpacking libtracker-sparql-0.16-0 (0.16.2-1ubuntu4) ...
Selecting previously unselected package libtracker-extract-0.16-0.
Preparing to unpack .../libtracker-extract-0.16-0_0.16.2-1ubuntu4_i386.deb ...
Unpacking libtracker-extract-0.16-0 (0.16.2-1ubuntu4) ...
Selecting previously unselected package libtracker-miner-0.16-0.
Preparing to unpack .../libtracker-miner-0.16-0_0.16.2-1ubuntu4_i386.deb ...
Unpacking libtracker-miner-0.16-0 (0.16.2-1ubuntu4) ...
Selecting previously unselected package gir1.2-tracker-0.16.
Preparing to unpack .../gir1.2-tracker-0.16_0.16.2-1ubuntu4_i386.deb ...
Unpacking gir1.2-tracker-0.16 (0.16.2-1ubuntu4) ...
Selecting previously unselected package libzapojit-0.0-0.
Preparing to unpack .../libzapojit-0.0-0_0.0.3-1ubuntu1_i386.deb ...
Unpacking libzapojit-0.0-0 (0.0.3-1ubuntu1) ...
Selecting previously unselected package gir1.2-zpj-0.0.
Preparing to unpack .../gir1.2-zpj-0.0_0.0.3-1ubuntu1_i386.deb ...
Unpacking gir1.2-zpj-0.0 (0.0.3-1ubuntu1) ...
Selecting previously unselected package gnome-backgrounds.
Preparing to unpack .../gnome-backgrounds_3.12.0-1_all.deb ...
Unpacking gnome-backgrounds (3.12.0-1) ...
Selecting previously unselected package gnome-color-manager.
Preparing to unpack .../gnome-color-manager_3.8.3-1ubuntu1_i386.deb ...
Unpacking gnome-color-manager (3.8.3-1ubuntu1) ...
Selecting previously unselected package gnome-control-center-data.
Preparing to unpack .../gnome-control-center-data_1%3a3.6.3-0ubuntu56_all.deb ...
Unpacking gnome-control-center-data (1:3.6.3-0ubuntu56) ...
Selecting previously unselected package gnome-control-center.
Preparing to unpack .../gnome-control-center_1%3a3.6.3-0ubuntu56_i386.deb ...
Unpacking gnome-control-center (1:3.6.3-0ubuntu56) ...
Selecting previously unselected package tracker.
Preparing to unpack .../tracker_0.16.2-1ubuntu4_i386.deb ...
Unpacking tracker (0.16.2-1ubuntu4) ...
Selecting previously unselected package libgupnp-av-1.0-2.
Preparing to unpack .../libgupnp-av-1.0-2_0.12.5-1ubuntu1_i386.deb ...
Unpacking libgupnp-av-1.0-2 (0.12.5-1ubuntu1) ...
Selecting previously unselected package grilo-plugins-0.2:i386.
Preparing to unpack .../grilo-plugins-0.2_0.2.12-2_i386.deb ...
Unpacking grilo-plugins-0.2:i386 (0.2.12-2) ...
Selecting previously unselected package gnome-online-miners.
Preparing to unpack .../gnome-online-miners_3.10.3-0ubuntu3_i386.deb ...
Unpacking gnome-online-miners (3.10.3-0ubuntu3) ...
Selecting previously unselected package gnome-documents.
Preparing to unpack .../gnome-documents_3.10.2-0ubuntu1_i386.deb ...
Unpacking gnome-documents (3.10.2-0ubuntu1) ...
Selecting previously unselected package gnome-icon-theme-extras.
Preparing to unpack .../gnome-icon-theme-extras_3.12.0-1ubuntu1_all.deb ...
Unpacking gnome-icon-theme-extras (3.12.0-1ubuntu1) ...
Selecting previously unselected package gnome-online-accounts.
Preparing to unpack .../gnome-online-accounts_3.10.3-0ubuntu1_i386.deb ...
Unpacking gnome-online-accounts (3.10.3-0ubuntu1) ...
Selecting previously unselected package gnome-shell-extensions.
Preparing to unpack .../gnome-shell-extensions_3.10.1-0ubuntu2_all.deb ...
Unpacking gnome-shell-extensions (3.10.1-0ubuntu2) ...
Selecting previously unselected package gnome-tweak-tool.
Preparing to unpack .../gnome-tweak-tool_3.10.1-2ubuntu1_all.deb ...
Unpacking gnome-tweak-tool (3.10.1-2ubuntu1) ...
Selecting previously unselected package gtk2-engines-pixbuf:i386.
Preparing to unpack .../gtk2-engines-pixbuf_2.24.23-0ubuntu1_i386.deb ...
Unpacking gtk2-engines-pixbuf:i386 (2.24.23-0ubuntu1) ...
Selecting previously unselected package gvfs-backends-goa.
Preparing to unpack .../gvfs-backends-goa_1.20.1-1ubuntu1_i386.deb ...
Unpacking gvfs-backends-goa (1.20.1-1ubuntu1) ...
Selecting previously unselected package libencode-locale-perl.
Preparing to unpack .../libencode-locale-perl_1.03-1_all.deb ...
Unpacking libencode-locale-perl (1.03-1) ...
Selecting previously unselected package liberror-perl.
Preparing to unpack .../liberror-perl_0.17-1.1_all.deb ...
Unpacking liberror-perl (0.17-1.1) ...
Selecting previously unselected package libhttp-date-perl.
Preparing to unpack .../libhttp-date-perl_6.02-1_all.deb ...
Unpacking libhttp-date-perl (6.02-1) ...
Selecting previously unselected package libfile-listing-perl.
Preparing to unpack .../libfile-listing-perl_6.04-1_all.deb ...
Unpacking libfile-listing-perl (6.04-1) ...
Selecting previously unselected package libfont-afm-perl.
Preparing to unpack .../libfont-afm-perl_1.20-1_all.deb ...
Unpacking libfont-afm-perl (1.20-1) ...
Selecting previously unselected package libgsf-1-common.
Preparing to unpack .../libgsf-1-common_1.14.27-2ubuntu2_all.deb ...
Unpacking libgsf-1-common (1.14.27-2ubuntu2) ...
Selecting previously unselected package libgsf-1-114.
Preparing to unpack .../libgsf-1-114_1.14.27-2ubuntu2_i386.deb ...
Unpacking libgsf-1-114 (1.14.27-2ubuntu2) ...
Selecting previously unselected package libhtml-tagset-perl.
Preparing to unpack .../libhtml-tagset-perl_3.20-2_all.deb ...
Unpacking libhtml-tagset-perl (3.20-2) ...
Selecting previously unselected package libhtml-parser-perl.
Preparing to unpack .../libhtml-parser-perl_3.71-1build1_i386.deb ...
Unpacking libhtml-parser-perl (3.71-1build1) ...
Selecting previously unselected package libio-html-perl.
Preparing to unpack .../libio-html-perl_1.00-1_all.deb ...
Unpacking libio-html-perl (1.00-1) ...
Selecting previously unselected package liblwp-mediatypes-perl.
Preparing to unpack .../liblwp-mediatypes-perl_6.02-1_all.deb ...
Unpacking liblwp-mediatypes-perl (6.02-1) ...
Selecting previously unselected package libhttp-message-perl.
Preparing to unpack .../libhttp-message-perl_6.06-1_all.deb ...
Unpacking libhttp-message-perl (6.06-1) ...
Selecting previously unselected package libhtml-form-perl.
Preparing to unpack .../libhtml-form-perl_6.03-1_all.deb ...
Unpacking libhtml-form-perl (6.03-1) ...
Selecting previously unselected package libhtml-tree-perl.
Preparing to unpack .../libhtml-tree-perl_5.03-1_all.deb ...
Unpacking libhtml-tree-perl (5.03-1) ...
Selecting previously unselected package libhtml-format-perl.
Preparing to unpack .../libhtml-format-perl_2.11-1_all.deb ...
Unpacking libhtml-format-perl (2.11-1) ...
Selecting previously unselected package libhttp-cookies-perl.
Preparing to unpack .../libhttp-cookies-perl_6.00-2_all.deb ...
Unpacking libhttp-cookies-perl (6.00-2) ...
Selecting previously unselected package libhttp-daemon-perl.
Preparing to unpack .../libhttp-daemon-perl_6.01-1_all.deb ...
Unpacking libhttp-daemon-perl (6.01-1) ...
Selecting previously unselected package libhttp-negotiate-perl.
Preparing to unpack .../libhttp-negotiate-perl_6.00-2_all.deb ...
Unpacking libhttp-negotiate-perl (6.00-2) ...
Selecting previously unselected package libnet-http-perl.
Preparing to unpack .../libnet-http-perl_6.06-1_all.deb ...
Unpacking libnet-http-perl (6.06-1) ...
Selecting previously unselected package libwww-robotrules-perl.
Preparing to unpack .../libwww-robotrules-perl_6.01-1_all.deb ...
Unpacking libwww-robotrules-perl (6.01-1) ...
Selecting previously unselected package libwww-perl.
Preparing to unpack .../libwww-perl_6.05-2_all.deb ...
Unpacking libwww-perl (6.05-2) ...
Selecting previously unselected package liblwp-protocol-https-perl.
Preparing to unpack .../liblwp-protocol-https-perl_6.04-2_all.deb ...
Unpacking liblwp-protocol-https-perl (6.04-2) ...
Selecting previously unselected package libnetaddr-ip-perl.
Preparing to unpack .../libnetaddr-ip-perl_4.071+dfsg-1_i386.deb ...
Unpacking libnetaddr-ip-perl (4.071+dfsg-1) ...
Selecting previously unselected package libmail-spf-perl.
Preparing to unpack .../libmail-spf-perl_2.9.0-2_all.deb ...
Unpacking libmail-spf-perl (2.9.0-2) ...
Selecting previously unselected package libreoffice-style-tango.
Preparing to unpack .../libreoffice-style-tango_1%3a4.2.3~rc3-0ubuntu2_all.deb ...
Unpacking libreoffice-style-tango (1:4.2.3~rc3-0ubuntu2) ...
Selecting previously unselected package libsys-hostname-long-perl.
Preparing to unpack .../libsys-hostname-long-perl_1.4-3_all.deb ...
Unpacking libsys-hostname-long-perl (1.4-3) ...
Selecting previously unselected package libxml2-utils.
Preparing to unpack .../libxml2-utils_2.9.1+dfsg1-3ubuntu4_i386.deb ...
Unpacking libxml2-utils (2.9.1+dfsg1-3ubuntu4) ...
Selecting previously unselected package mcp-account-manager-goa.
Preparing to unpack .../mcp-account-manager-goa_3.8.6-0ubuntu9_i386.deb ...
Unpacking mcp-account-manager-goa (3.8.6-0ubuntu9) ...
Selecting previously unselected package notification-daemon.
Preparing to unpack .../notification-daemon_0.7.6-1_i386.deb ...
Unpacking notification-daemon (0.7.6-1) ...
Selecting previously unselected package plymouth-theme-ubuntu-gnome-logo.
Preparing to unpack .../plymouth-theme-ubuntu-gnome-logo_14.04.1_all.deb ...
Unpacking plymouth-theme-ubuntu-gnome-logo (14.04.1) ...
Selecting previously unselected package plymouth-theme-ubuntu-gnome-text.
Preparing to unpack .../plymouth-theme-ubuntu-gnome-text_14.04.1_all.deb ...
Unpacking plymouth-theme-ubuntu-gnome-text (14.04.1) ...
Preparing to unpack .../software-properties-common_0.92.37_all.deb ...
Unpacking software-properties-common (0.92.37) over (0.92.36) ...
Preparing to unpack .../software-properties-gtk_0.92.37_all.deb ...
Unpacking software-properties-gtk (0.92.37) over (0.92.36) ...
Preparing to unpack .../python3-software-properties_0.92.37_all.deb ...
Unpacking python3-software-properties (0.92.37) over (0.92.36) ...
Selecting previously unselected package re2c.
Preparing to unpack .../re2c_0.13.5-1build2_i386.deb ...
Unpacking re2c (0.13.5-1build2) ...
Selecting previously unselected package spamassassin.
Preparing to unpack .../spamassassin_3.4.0-1ubuntu1_all.deb ...
Unpacking spamassassin (3.4.0-1ubuntu1) ...
Selecting previously unselected package sa-compile.
Preparing to unpack .../sa-compile_3.4.0-1ubuntu1_all.deb ...
Unpacking sa-compile (3.4.0-1ubuntu1) ...
Selecting previously unselected package spamc.
Preparing to unpack .../spamc_3.4.0-1ubuntu1_i386.deb ...
Unpacking spamc (3.4.0-1ubuntu1) ...
Selecting previously unselected package tracker-extract.
Preparing to unpack .../tracker-extract_0.16.2-1ubuntu4_i386.deb ...
Unpacking tracker-extract (0.16.2-1ubuntu4) ...
Selecting previously unselected package tracker-miner-fs.
Preparing to unpack .../tracker-miner-fs_0.16.2-1ubuntu4_i386.deb ...
Unpacking tracker-miner-fs (0.16.2-1ubuntu4) ...
Selecting previously unselected package tracker-utils.
Preparing to unpack .../tracker-utils_0.16.2-1ubuntu4_i386.deb ...
Unpacking tracker-utils (0.16.2-1ubuntu4) ...
Selecting previously unselected package ubuntu-gnome-default-settings.
Preparing to unpack .../ubuntu-gnome-default-settings_14.04.1_all.deb ...
Unpacking ubuntu-gnome-default-settings (14.04.1) ...
Selecting previously unselected package gnome-sushi.
Preparing to unpack .../gnome-sushi_3.11.90-0ubuntu1_i386.deb ...
Unpacking gnome-sushi (3.11.90-0ubuntu1) ...
Selecting previously unselected package itstool.
Preparing to unpack .../itstool_2.0.2-2_all.deb ...
Unpacking itstool (2.0.2-2) ...
Selecting previously unselected package xsltproc.
Preparing to unpack .../xsltproc_1.1.28-2build1_i386.deb ...
Unpacking xsltproc (1.1.28-2build1) ...
Selecting previously unselected package yelp-tools.
Preparing to unpack .../yelp-tools_3.10.0-1_all.deb ...
Unpacking yelp-tools (3.10.0-1) ...
Selecting previously unselected package zsync.
Preparing to unpack .../zsync_0.6.2-1ubuntu1_i386.deb ...
Unpacking zsync (0.6.2-1ubuntu1) ...
Selecting previously unselected package ubuntu-gnome-desktop.
Preparing to unpack .../ubuntu-gnome-desktop_0.32_i386.deb ...
Unpacking ubuntu-gnome-desktop (0.32) ...
Selecting previously unselected package ubuntu-gnome-wallpapers-trusty.
Preparing to unpack .../ubuntu-gnome-wallpapers-trusty_14.04.1_all.deb ...
Unpacking ubuntu-gnome-wallpapers-trusty (14.04.1) ...
Selecting previously unselected package ubuntu-gnome-wallpapers.
Preparing to unpack .../ubuntu-gnome-wallpapers_14.04.1_all.deb ...
Unpacking ubuntu-gnome-wallpapers (14.04.1) ...
Selecting previously unselected package xserver-xephyr.
Preparing to unpack .../xserver-xephyr_2%3a1.15.1-0ubuntu2_i386.deb ...
Unpacking xserver-xephyr (2:1.15.1-0ubuntu2) ...
Selecting previously unselected package evolution-indicator.
Preparing to unpack .../evolution-indicator_0.2.20-0ubuntu15_i386.deb ...
Unpacking evolution-indicator (0.2.20-0ubuntu15) ...
Selecting previously unselected package unoconv.
Preparing to unpack .../archives/unoconv_0.6-6_all.deb ...
Unpacking unoconv (0.6-6) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for libglib2.0-0:i386 (2.40.0-2) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for fontconfig (2.11.0-0ubuntu4) ...
Processing triggers for gnome-icon-theme (3.10.0-0ubuntu2) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Setting up libgtkhtml-4.0-common (4.6.6-2ubuntu1) ...
Setting up libgtkhtml-4.0-0 (4.6.6-2ubuntu1) ...
Setting up libgtkhtml-editor-4.0-0 (4.6.6-2ubuntu1) ...
Setting up libytnef0:i386 (1.5-6) ...
Setting up libevolution (3.10.4-0ubuntu1) ...
Setting up evolution-common (3.10.4-0ubuntu1) ...
Setting up evolution (3.10.4-0ubuntu1) ...
Setting up gnome-themes-standard-data (3.10.0-1ubuntu2) ...
Setting up gnome-themes-standard:i386 (3.10.0-1ubuntu2) ...
Setting up libcaribou-common (0.4.13-0ubuntu1) ...
Setting up libcaribou0:i386 (0.4.13-0ubuntu1) ...
Setting up libcolord-gtk1:i386 (0.1.25-1.1) ...
Setting up libgdm1 (3.10.0.1-0ubuntu3) ...
Setting up libgif4:i386 (4.1.6-11) ...
Setting up libgoa-backend-1.0-1:i386 (3.10.3-0ubuntu1) ...
Setting up libgrilo-0.2-1:i386 (0.2.10-1) ...
Setting up libimdi0:i386 (1.5.1-5ubuntu1) ...
Setting up libmediaart-1.0-0:i386 (0.4.0-1ubuntu1) ...
Setting up libpst4:i386 (0.6.59-1build1) ...
Setting up libxcb-xf86dri0:i386 (1.10-2ubuntu1) ...
Setting up libxcb-xv0:i386 (1.10-2ubuntu1) ...
Setting up libicc2:i386 (2.12+argyll1.5.1-5ubuntu1) ...
Setting up libmusicbrainz5-0:i386 (5.0.1-2) ...
Setting up libnss-myhostname:i386 (0.3-6) ...
First installation detected...
Checking NSS setup...
Setting up libxcb-keysyms1:i386 (0.3.9-1ubuntu1) ...
Setting up python-cloudfiles (1.7.11-2build1) ...
Setting up argyll (1.5.1-5ubuntu1) ...
Setting up dconf-editor (0.20.0-1) ...
Setting up deja-dup-backend-cloudfiles (30.0-0ubuntu4) ...
Setting up python-urllib3 (1.7.1-1build1) ...
Setting up python-requests (2.2.1-1) ...
Setting up python-boto (2.20.1-2ubuntu2) ...
Setting up deja-dup-backend-s3 (30.0-0ubuntu4) ...
Setting up evolution-plugins (3.10.4-0ubuntu1) ...
Setting up fonts-cantarell (0.0.15-1) ...
Setting up gir1.2-gdm-1.0 (3.10.0.1-0ubuntu3) ...
Setting up gnome-settings-daemon (3.8.6.1-0ubuntu11) ...
Setting up gir1.2-cogl-1.0 (1.16.2-1) ...
Setting up gir1.2-coglpango-1.0 (1.16.2-1) ...
Setting up gir1.2-json-1.0 (0.16.2-1ubuntu1) ...
Setting up gir1.2-clutter-1.0 (1.16.4-0ubuntu2) ...
Setting up gir1.2-gdesktopenums-3.0 (3.10.1-0ubuntu1) ...
Setting up mutter-common (3.10.4-0ubuntu2) ...
Setting up libmutter0c (3.10.4-0ubuntu2) ...
Setting up gir1.2-mutter-3.0 (3.10.4-0ubuntu2) ...
Setting up gir1.2-telepathyglib-0.12 (0.22.1-1ubuntu2) ...
Setting up gnome-icon-theme-full (3.10.0-0ubuntu2) ...
update-alternatives: using /usr/share/icons/gnome/scalable/places/ubuntu-logo.svg to provide /usr/share/icons/gnome/scalable/places/start-here.svg (start-here.svg) in auto mode
update-alternatives: warning: skip creation of /usr/share/icons/gnome/256x256/places/start-here.png because associated file /usr/share/icons/gnome/256x256/places/ubuntu-logo.png (of link group start-here.svg) doesn't exist
update-alternatives: warning: skip creation of /usr/share/icons/gnome/48x48/places/start-here.png because associated file /usr/share/icons/gnome/48x48/places/ubuntu-logo.png (of link group start-here.svg) doesn't exist
Setting up libmozjs-24-0 (24.2.0-1) ...
Setting up libgjs0e (1.39.91-0ubuntu1) ...
Setting up gir1.2-accountsservice-1.0 (0.6.35-0ubuntu7) ...
Setting up gir1.2-caribou-1.0 (0.4.13-0ubuntu1) ...
Setting up gir1.2-gck-1 (3.10.1-1) ...
Setting up gir1.2-gcr-3 (3.10.1-1) ...
Setting up gir1.2-xkl-1.0 (5.4-0ubuntu1) ...
Setting up gir1.2-gkbd-3.0 (3.6.0-0ubuntu2) ...
Setting up gir1.2-gnomedesktop-3.0 (3.8.4-0ubuntu3) ...
Setting up gir1.2-nmgtk-1.0 (0.9.8.8-0ubuntu4) ...
Setting up gir1.2-polkit-1.0 (0.105-4ubuntu2) ...
Setting up gir1.2-telepathylogger-0.2 (0.8.0-3) ...
Setting up gir1.2-upowerglib-1.0 (0.9.23-2ubuntu1) ...
Setting up gjs (1.39.91-0ubuntu1) ...
Setting up gnome-shell-common (3.10.4-0ubuntu5) ...
Setting up gnome-shell (3.10.4-0ubuntu5) ...
Setting up gnome-session (3.9.90-0ubuntu12) ...
Setting up mutter (3.10.4-0ubuntu2) ...
update-alternatives: using /usr/bin/mutter to provide /usr/bin/x-window-manager (x-window-manager) in auto mode
Setting up gdm (3.10.0.1-0ubuntu3) ...
Setting up gir1.2-clutter-gst-2.0 (2.0.8-1build1) ...
Setting up gir1.2-evince-3.0 (3.10.3-0ubuntu10) ...
Setting up gir1.2-gtkclutter-1.0 (1.4.4-3ubuntu2) ...
Setting up gir1.2-gtop-2.0 (2.28.5-2) ...
Setting up gir1.2-rest-0.7 (0.7.90-0ubuntu1) ...
Setting up libiptcdata0 (1.0.4-3ubuntu3) ...
Setting up libtracker-sparql-0.16-0 (0.16.2-1ubuntu4) ...
Setting up libtracker-extract-0.16-0 (0.16.2-1ubuntu4) ...
Setting up libtracker-miner-0.16-0 (0.16.2-1ubuntu4) ...
Setting up gir1.2-tracker-0.16 (0.16.2-1ubuntu4) ...
Setting up libzapojit-0.0-0 (0.0.3-1ubuntu1) ...
Setting up gir1.2-zpj-0.0 (0.0.3-1ubuntu1) ...
Setting up gnome-backgrounds (3.12.0-1) ...
Setting up gnome-color-manager (3.8.3-1ubuntu1) ...
Setting up gnome-control-center-data (1:3.6.3-0ubuntu56) ...
Setting up gnome-control-center (1:3.6.3-0ubuntu56) ...
Setting up tracker (0.16.2-1ubuntu4) ...
Setting up libgupnp-av-1.0-2 (0.12.5-1ubuntu1) ...
Setting up grilo-plugins-0.2:i386 (0.2.12-2) ...
Setting up gnome-online-miners (3.10.3-0ubuntu3) ...
Setting up gnome-documents (3.10.2-0ubuntu1) ...
Setting up gnome-icon-theme-extras (3.12.0-1ubuntu1) ...
Setting up gnome-online-accounts (3.10.3-0ubuntu1) ...
Setting up gnome-shell-extensions (3.10.1-0ubuntu2) ...
Setting up gnome-tweak-tool (3.10.1-2ubuntu1) ...
Setting up gtk2-engines-pixbuf:i386 (2.24.23-0ubuntu1) ...
Setting up gvfs-backends-goa (1.20.1-1ubuntu1) ...
Setting up libencode-locale-perl (1.03-1) ...
Setting up liberror-perl (0.17-1.1) ...
Setting up libhttp-date-perl (6.02-1) ...
Setting up libfile-listing-perl (6.04-1) ...
Setting up libfont-afm-perl (1.20-1) ...
Setting up libgsf-1-common (1.14.27-2ubuntu2) ...
Setting up libgsf-1-114 (1.14.27-2ubuntu2) ...
Setting up libhtml-tagset-perl (3.20-2) ...
Setting up libhtml-parser-perl (3.71-1build1) ...
Setting up libio-html-perl (1.00-1) ...
Setting up liblwp-mediatypes-perl (6.02-1) ...
Setting up libhttp-message-perl (6.06-1) ...
Setting up libhtml-form-perl (6.03-1) ...
Setting up libhtml-tree-perl (5.03-1) ...
Setting up libhtml-format-perl (2.11-1) ...
Setting up libhttp-cookies-perl (6.00-2) ...
Setting up libhttp-daemon-perl (6.01-1) ...
Setting up libhttp-negotiate-perl (6.00-2) ...
Setting up libnet-http-perl (6.06-1) ...
Setting up libwww-robotrules-perl (6.01-1) ...
Setting up libnetaddr-ip-perl (4.071+dfsg-1) ...
Setting up libmail-spf-perl (2.9.0-2) ...
Setting up libreoffice-style-tango (1:4.2.3~rc3-0ubuntu2) ...
Setting up libsys-hostname-long-perl (1.4-3) ...
Setting up libxml2-utils (2.9.1+dfsg1-3ubuntu4) ...
Setting up mcp-account-manager-goa (3.8.6-0ubuntu9) ...
Setting up notification-daemon (0.7.6-1) ...
Setting up plymouth-theme-ubuntu-gnome-logo (14.04.1) ...
update-alternatives: using /lib/plymouth/themes/ubuntu-gnome-logo/ubuntu-gnome-logo.plymouth to provide /lib/plymouth/themes/default.plymouth (default.plymouth) in auto mode
update-initramfs: deferring update (trigger activated)
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04 LTS (14.04) on /dev/sda1
Found Ubuntu 14.04 LTS (14.04) on /dev/sda10
Found Ubuntu 14.04 LTS (14.04) on /dev/sda11
Found Ubuntu 14.04 LTS (14.04) on /dev/sda13
Found Ubuntu 13.10 (13.10) on /dev/sda14
Found Ubuntu 14.04 LTS (14.04) on /dev/sda15
Found Ubuntu Utopic Unicorn (development branch) (14.10) on /dev/sda16
Found Ubuntu 13.10 (13.10) on /dev/sda18
Found Ubuntu 12.04.4 LTS (12.04) on /dev/sda2
done
Setting up plymouth-theme-ubuntu-gnome-text (14.04.1) ...
update-alternatives: using /lib/plymouth/themes/ubuntu-gnome-text/ubuntu-gnome-text.plymouth to provide /lib/plymouth/themes/text.plymouth (text.plymouth) in auto mode
update-initramfs: deferring update (trigger activated)
Setting up python3-software-properties (0.92.37) ...
Setting up software-properties-common (0.92.37) ...
Setting up software-properties-gtk (0.92.37) ...
Setting up re2c (0.13.5-1build2) ...
Setting up spamc (3.4.0-1ubuntu1) ...
Setting up tracker-extract (0.16.2-1ubuntu4) ...
Setting up tracker-miner-fs (0.16.2-1ubuntu4) ...
procps stop/waiting
Setting up tracker-utils (0.16.2-1ubuntu4) ...
Setting up ubuntu-gnome-default-settings (14.04.1) ...
Setting up gnome-sushi (3.11.90-0ubuntu1) ...
Setting up itstool (2.0.2-2) ...
Setting up xsltproc (1.1.28-2build1) ...
Setting up yelp-tools (3.10.0-1) ...
Setting up zsync (0.6.2-1ubuntu1) ...
Setting up ubuntu-gnome-wallpapers-trusty (14.04.1) ...
Setting up ubuntu-gnome-wallpapers (14.04.1) ...
Setting up xserver-xephyr (2:1.15.1-0ubuntu2) ...
Setting up evolution-indicator (0.2.20-0ubuntu15) ...
Setting up unoconv (0.6-6) ...
Processing triggers for ureadahead (0.100.0-16) ...
Setting up ubuntu-gnome-desktop (0.32) ...
Setting up libwww-perl (6.05-2) ...
Setting up liblwp-protocol-https-perl (6.04-2) ...
Setting up spamassassin (3.4.0-1ubuntu1) ...
Adding system user `debian-spamd' (UID 117) ...
Adding new group `debian-spamd' (GID 126) ...
Adding new user `debian-spamd' (UID 117) with group `debian-spamd' ...
Creating home directory `/var/lib/spamassassin' ...
SpamAssassin Mail Filter Daemon: disabled, see /etc/default/spamassassin
Processing triggers for ureadahead (0.100.0-16) ...
Setting up sa-compile (3.4.0-1ubuntu1) ...
Running sa-compile (may take a long time)
SpamAssassin Mail Filter Daemon: disabled, see /etc/default/spamassassin
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Processing triggers for initramfs-tools (0.103ubuntu4) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-24-generic
Log ended: 2014-05-05  09:10:43
```

---

### Post by kansasnoob on 2014-05-05
No surprise here:

```
lance@lance-desktop:~$ sudo apt-get autoremove
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

So that's a fail, time to reboot and see what login options I'm offered.

---

### Post by kansasnoob on 2014-05-05
GNOME, GNOME Classic, and Ubuntu are all bootable after that but not surprisingly that renders the Unity DE almost worthless.

Now I'm going to properly remove the Ubuntu bits:

```
lance@lance-desktop:~$ sudo apt-get remove account-plugin-facebook account-plugin-flickr account-plugin-google account-plugin-twitter activity-log-manager activity-log-manager-control-center adium-theme-ubuntu appmenu-qt appmenu-qt5 bamfdaemon branding-ubuntu checkbox-gui checkbox-ng checkbox-ng-service compiz compiz-core compiz-gnome compiz-plugins-default dmz-cursor-theme doc-base ethtool example-content friends friends-dispatcher friends-facebook friends-twitter geoclue-ubuntu-geoip gir1.2-accounts-1.0 gir1.2-appindicator3-0.1 gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2 gir1.2-messagingmenu-1.0 gir1.2-signon-1.0 gnome-power-manager gnome-screensaver gnomine gsettings-ubuntu-schemas gstreamer0.10-plugins-base-apps gstreamer0.10-tools gstreamer1.0-plugins-base-apps gstreamer1.0-tools gtk2-engines-murrine gtk3-engines-unico hud indicator-applet indicator-appmenu indicator-bluetooth indicator-datetime indicator-keyboard indicator-messages indicator-power indicator-printers indicator-session indicator-sound landscape-client-ui-install language-selector-gnome libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-qt5-1 libaudio2 libbamf3-2 libcolumbus1 libcolumbus1-common libcompizconfig0 libdbusmenu-qt2 libdbusmenu-qt5 libdecoration0 libfreerdp-plugins-standard libfreerdp1 libfriends0 libgee2 libglew1.10 libglewmx1.10 libgsettings-qt1 libhud2 liblightdm-gobject-1-0 libmetacity-private0a libmysqlclient18 libnux-4.0-0 libnux-4.0-common liboxideqt-qmlplugin liboxideqtcore0 libpanel-applet-4-0 libpocketsphinx1 libprotobuf8 libqt4-dbus libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns libqt5core5a libqt5dbus5 libqt5feedback5 libqt5gui5 libqt5multimedia5 libqt5network5 libqt5opengl5 libqt5organizer5 libqt5positioning5 libqt5printsupport5 libqt5qml-graphicaleffects libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5svg5 libqt5test5 libqt5webkit5 libqt5webkit5-qmlwebkitplugin libqt5widgets5 libqt5xml5 libqtassistantclient4 libqtcore4 libqtdbus4 libqtgui4 libqtwebkit4 libreoffice-style-human libsignon-extension1 libsignon-plugins-common1 libsignon-qt5-1 libsphinxbase1 libssh-4 libthumbnailer0 libtimezonemap1 libufe-xidgetter0 libunity-action-qt1 libunity-core-6.0-9 libunity-gtk2-parser0 libunity-gtk3-parser0 libunity-misc4 libunity-webapps0 libunityvoice1 libupstart1 liburl-dispatcher1 libuuid-perl libvncserver0 libwhoopsie-preferences0 libwnck-common libwnck22 libx86-1 libxcb-randr0 libxcb-render-util0 libxcb-xkb1 libyaml-tiny-perl light-themes lightdm metacity-common mysql-common notify-osd notify-osd-icons nux-tools onboard onboard-data overlay-scrollbar overlay-scrollbar-gtk2 overlay-scrollbar-gtk3 pkg-config plainbox-provider-checkbox plainbox-provider-resource-generic plainbox-secure-policy plymouth-theme-ubuntu-logo pm-utils python-gconf python-qt4 python-qt4-dbus python-sip python3-checkbox-ng python3-checkbox-support python3-feedparser python3-lxml python3-plainbox python3-pyparsing python3-requests python3-urllib3 qdbus qt-at-spi qtchooser qtcore4-l10n qtdeclarative5-accounts-plugin qtdeclarative5-dialogs-plugin qtdeclarative5-localstorage-plugin qtdeclarative5-privatewidgets-plugin qtdeclarative5-qtfeedback-plugin qtdeclarative5-qtquick2-plugin qtdeclarative5-ubuntu-ui-extras-browser-plugin qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-unity-action-plugin qtdeclarative5-window-plugin remmina remmina-common remmina-plugin-rdp remmina-plugin-vnc signon-keyring-extension signon-plugin-oauth2 signon-ui signond sni-qt sphinx-voxforge-hmm-en sphinx-voxforge-lm-en telepathy-indicator thunderbird thunderbird-gnome-support totem-mozilla ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-session ubuntu-settings ubuntu-sounds ubuntu-sso-client-qt ubuntu-ui-toolkit-theme ubuntu-wallpapers ubuntu-wallpapers-trusty ubuntuone-client-data unity unity-asset-pool unity-control-center unity-control-center-signon unity-greeter unity-gtk-module-common unity-gtk2-module unity-gtk3-module unity-lens-applications unity-lens-files unity-lens-friends unity-lens-music unity-lens-photos unity-lens-video unity-scope-audacious unity-scope-calculator unity-scope-chromiumbookmarks unity-scope-clementine unity-scope-colourlovers unity-scope-devhelp unity-scope-firefoxbookmarks unity-scope-gdrive unity-scope-gmusicbrowser unity-scope-gourmet unity-scope-guayadeque unity-scope-home unity-scope-manpages unity-scope-musicstores unity-scope-musique unity-scope-openclipart unity-scope-texdoc unity-scope-tomboy unity-scope-video-remote unity-scope-virtualbox unity-scope-yelp unity-scope-zotero unity-scopes-master-default unity-scopes-runner unity-services unity-settings-daemon unity-voice-service unity-webapps-common unity-webapps-qml unity-webapps-service vbetool webaccounts-extension-common webapp-container webbrowser-app whoopsie-preferences xcursor-themes xul-ext-unity xul-ext-webaccounts xul-ext-websites-integration
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'libqt4-sql-mysql' is not installed, so not removed
Package 'ubuntu-desktop' is not installed, so not removed
Package 'indicator-applet' is not installed, so not removed
Package 'libpanel-applet-4-0' is not installed, so not removed
Package 'libmysqlclient18' is not installed, so not removed
Package 'mysql-common' is not installed, so not removed
The following packages will be REMOVED:
  account-plugin-aim account-plugin-facebook account-plugin-flickr
  account-plugin-google account-plugin-jabber account-plugin-salut
  account-plugin-twitter account-plugin-windows-live account-plugin-yahoo
  activity-log-manager activity-log-manager-control-center adium-theme-ubuntu
  appmenu-qt appmenu-qt5 bamfdaemon branding-ubuntu checkbox-gui checkbox-ng
  checkbox-ng-service compiz compiz-core compiz-gnome compiz-plugins-default
  dmz-cursor-theme doc-base ethtool example-content friends friends-dispatcher
  friends-facebook friends-twitter geoclue-ubuntu-geoip gir1.2-accounts-1.0
  gir1.2-appindicator3-0.1 gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2
  gir1.2-edataserver-1.2 gir1.2-messagingmenu-1.0 gir1.2-signon-1.0
  gnome-power-manager gnome-screensaver gnomine gsettings-ubuntu-schemas
  gstreamer0.10-plugins-base-apps gstreamer0.10-tools
  gstreamer1.0-plugins-base-apps gstreamer1.0-tools gtk2-engines-murrine
  gtk3-engines-unico hud indicator-appmenu indicator-bluetooth
  indicator-datetime indicator-keyboard indicator-messages indicator-power
  indicator-printers indicator-session indicator-sound
  landscape-client-ui-install language-selector-gnome libaccount-plugin-1.0-0
  libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-qt5-1
  libaudio2 libbamf3-2 libcolumbus1 libcolumbus1-common libcompizconfig0
  libdbusmenu-qt2 libdbusmenu-qt5 libdecoration0 libfreerdp-plugins-standard
  libfreerdp1 libfriends0 libgee2 libglew1.10 libglewmx1.10 libgsettings-qt1
  libhud2 liblightdm-gobject-1-0 libmetacity-private0a libnux-4.0-0
  libnux-4.0-common liboxideqt-qmlplugin liboxideqtcore0 libpocketsphinx1
  libprotobuf8 libqt4-dbus libqt4-declarative libqt4-designer libqt4-help
  libqt4-network libqt4-opengl libqt4-script libqt4-scripttools libqt4-sql
  libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns
  libqt5core5a libqt5dbus5 libqt5feedback5 libqt5gui5 libqt5multimedia5
  libqt5network5 libqt5opengl5 libqt5organizer5 libqt5positioning5
  libqt5printsupport5 libqt5qml-graphicaleffects libqt5qml5 libqt5quick5
  libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5svg5 libqt5test5
  libqt5webkit5 libqt5webkit5-qmlwebkitplugin libqt5widgets5 libqt5xml5
  libqtassistantclient4 libqtcore4 libqtdbus4 libqtgui4 libqtwebkit4
  libreoffice-style-human libsignon-extension1 libsignon-plugins-common1
  libsignon-qt5-1 libsphinxbase1 libssh-4 libthumbnailer0 libtimezonemap1
  libufe-xidgetter0 libunity-action-qt1 libunity-core-6.0-9
  libunity-gtk2-parser0 libunity-gtk3-parser0 libunity-misc4 libunity-webapps0
  libunityvoice1 libupstart1 liburl-dispatcher1 libuuid-perl libvncserver0
  libwhoopsie-preferences0 libwnck-common libwnck22 libx86-1 libxcb-randr0
  libxcb-render-util0 libxcb-xkb1 libyaml-tiny-perl light-themes lightdm
  mcp-account-manager-uoa metacity-common notify-osd notify-osd-icons
  nux-tools onboard onboard-data overlay-scrollbar overlay-scrollbar-gtk2
  overlay-scrollbar-gtk3 pkg-config plainbox-provider-checkbox
  plainbox-provider-resource-generic plainbox-secure-policy
  plymouth-theme-ubuntu-logo pm-utils python-gconf python-qt4 python-qt4-dbus
  python-sip python3-checkbox-ng python3-checkbox-support python3-feedparser
  python3-lxml python3-plainbox python3-pyparsing python3-requests
  python3-urllib3 qdbus qt-at-spi qtchooser qtcore4-l10n
  qtdeclarative5-accounts-plugin qtdeclarative5-dialogs-plugin
  qtdeclarative5-localstorage-plugin qtdeclarative5-privatewidgets-plugin
  qtdeclarative5-qtfeedback-plugin qtdeclarative5-qtquick2-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-unity-action-plugin
  qtdeclarative5-window-plugin remmina remmina-common remmina-plugin-rdp
  remmina-plugin-vnc signon-keyring-extension signon-plugin-oauth2
  signon-plugin-password signon-ui signond sni-qt sphinx-voxforge-hmm-en
  sphinx-voxforge-lm-en telepathy-indicator thunderbird
  thunderbird-gnome-support thunderbird-locale-en thunderbird-locale-en-us
  totem-mozilla ubuntu-artwork ubuntu-docs ubuntu-mono ubuntu-session
  ubuntu-settings ubuntu-sounds ubuntu-sso-client-qt ubuntu-ui-toolkit-theme
  ubuntu-wallpapers ubuntu-wallpapers-trusty ubuntuone-client-data unity
  unity-asset-pool unity-control-center unity-control-center-signon
  unity-greeter unity-gtk-module-common unity-gtk2-module unity-gtk3-module
  unity-lens-applications unity-lens-files unity-lens-friends unity-lens-music
  unity-lens-photos unity-lens-video unity-scope-audacious
  unity-scope-calculator unity-scope-chromiumbookmarks unity-scope-clementine
  unity-scope-colourlovers unity-scope-devhelp unity-scope-firefoxbookmarks
  unity-scope-gdrive unity-scope-gmusicbrowser unity-scope-gourmet
  unity-scope-guayadeque unity-scope-home unity-scope-manpages
  unity-scope-musicstores unity-scope-musique unity-scope-openclipart
  unity-scope-texdoc unity-scope-tomboy unity-scope-video-remote
  unity-scope-virtualbox unity-scope-yelp unity-scope-zotero
  unity-scopes-master-default unity-scopes-runner unity-services
  unity-settings-daemon unity-voice-service unity-webapps-common
  unity-webapps-qml unity-webapps-service vbetool webaccounts-extension-common
  webapp-container webbrowser-app whoopsie-preferences xcursor-themes
  xul-ext-unity xul-ext-webaccounts xul-ext-websites-integration
0 upgraded, 0 newly installed, 285 to remove and 0 not upgraded.
After this operation, 549 MB disk space will be freed.
Do you want to continue? [Y/n] 

```

Stay tuned :)

---

### Post by kansasnoob on 2014-05-05
After completeing that I ran:

```
lance@lance-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

The applicable bits of /var/log/apt/history.log:

```
Start-Date: 2014-05-05  09:47:24
Commandline: apt-get remove account-plugin-facebook account-plugin-flickr account-plugin-google account-plugin-twitter activity-log-manager activity-log-manager-control-center adium-theme-ubuntu appmenu-qt appmenu-qt5 bamfdaemon branding-ubuntu checkbox-gui checkbox-ng checkbox-ng-service compiz compiz-core compiz-gnome compiz-plugins-default dmz-cursor-theme doc-base ethtool example-content friends friends-dispatcher friends-facebook friends-twitter geoclue-ubuntu-geoip gir1.2-accounts-1.0 gir1.2-appindicator3-0.1 gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2 gir1.2-messagingmenu-1.0 gir1.2-signon-1.0 gnome-power-manager gnome-screensaver gnomine gsettings-ubuntu-schemas gstreamer0.10-plugins-base-apps gstreamer0.10-tools gstreamer1.0-plugins-base-apps gstreamer1.0-tools gtk2-engines-murrine gtk3-engines-unico hud indicator-applet indicator-appmenu indicator-bluetooth indicator-datetime indicator-keyboard indicator-messages indicator-power indicator-printers indicator-session indicator-sound landscape-client-ui-install language-selector-gnome libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-qt5-1 libaudio2 libbamf3-2 libcolumbus1 libcolumbus1-common libcompizconfig0 libdbusmenu-qt2 libdbusmenu-qt5 libdecoration0 libfreerdp-plugins-standard libfreerdp1 libfriends0 libgee2 libglew1.10 libglewmx1.10 libgsettings-qt1 libhud2 liblightdm-gobject-1-0 libmetacity-private0a libmysqlclient18 libnux-4.0-0 libnux-4.0-common liboxideqt-qmlplugin liboxideqtcore0 libpanel-applet-4-0 libpocketsphinx1 libprotobuf8 libqt4-dbus libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns libqt5core5a libqt5dbus5 libqt5feedback5 libqt5gui5 libqt5multimedia5 libqt5network5 libqt5opengl5 libqt5organizer5 libqt5positioning5 libqt5printsupport5 libqt5qml-graphicaleffects libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5svg5 libqt5test5 libqt5webkit5 libqt5webkit5-qmlwebkitplugin libqt5widgets5 libqt5xml5 libqtassistantclient4 libqtcore4 libqtdbus4 libqtgui4 libqtwebkit4 libreoffice-style-human libsignon-extension1 libsignon-plugins-common1 libsignon-qt5-1 libsphinxbase1 libssh-4 libthumbnailer0 libtimezonemap1 libufe-xidgetter0 libunity-action-qt1 libunity-core-6.0-9 libunity-gtk2-parser0 libunity-gtk3-parser0 libunity-misc4 libunity-webapps0 libunityvoice1 libupstart1 liburl-dispatcher1 libuuid-perl libvncserver0 libwhoopsie-preferences0 libwnck-common libwnck22 libx86-1 libxcb-randr0 libxcb-render-util0 libxcb-xkb1 libyaml-tiny-perl light-themes lightdm metacity-common mysql-common notify-osd notify-osd-icons nux-tools onboard onboard-data overlay-scrollbar overlay-scrollbar-gtk2 overlay-scrollbar-gtk3 pkg-config plainbox-provider-checkbox plainbox-provider-resource-generic plainbox-secure-policy plymouth-theme-ubuntu-logo pm-utils python-gconf python-qt4 python-qt4-dbus python-sip python3-checkbox-ng python3-checkbox-support python3-feedparser python3-lxml python3-plainbox python3-pyparsing python3-requests python3-urllib3 qdbus qt-at-spi qtchooser qtcore4-l10n qtdeclarative5-accounts-plugin qtdeclarative5-dialogs-plugin qtdeclarative5-localstorage-plugin qtdeclarative5-privatewidgets-plugin qtdeclarative5-qtfeedback-plugin qtdeclarative5-qtquick2-plugin qtdeclarative5-ubuntu-ui-extras-browser-plugin qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-unity-action-plugin qtdeclarative5-window-plugin remmina remmina-common remmina-plugin-rdp remmina-plugin-vnc signon-keyring-extension signon-plugin-oauth2 signon-ui signond sni-qt sphinx-voxforge-hmm-en sphinx-voxforge-lm-en telepathy-indicator thunderbird thunderbird-gnome-support totem-mozilla ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-session ubuntu-settings ubuntu-sounds ubuntu-sso-client-qt ubuntu-ui-toolkit-theme ubuntu-wallpapers ubuntu-wallpapers-trusty ubuntuone-client-data unity unity-asset-pool unity-control-center unity-control-center-signon unity-greeter unity-gtk-module-common unity-gtk2-module unity-gtk3-module unity-lens-applications unity-lens-files unity-lens-friends unity-lens-music unity-lens-photos unity-lens-video unity-scope-audacious unity-scope-calculator unity-scope-chromiumbookmarks unity-scope-clementine unity-scope-colourlovers unity-scope-devhelp unity-scope-firefoxbookmarks unity-scope-gdrive unity-scope-gmusicbrowser unity-scope-gourmet unity-scope-guayadeque unity-scope-home unity-scope-manpages unity-scope-musicstores unity-scope-musique unity-scope-openclipart unity-scope-texdoc unity-scope-tomboy unity-scope-video-remote unity-scope-virtualbox unity-scope-yelp unity-scope-zotero unity-scopes-master-default unity-scopes-runner unity-services unity-settings-daemon unity-voice-service unity-webapps-common unity-webapps-qml unity-webapps-service vbetool webaccounts-extension-common webapp-container webbrowser-app whoopsie-preferences xcursor-themes xul-ext-unity xul-ext-webaccounts xul-ext-websites-integration
Remove: unity-settings-daemon:i386 (14.04.0+14.04.20140414-0ubuntu1), unity-gtk3-module:i386 (0.0.0+14.04.20140403-0ubuntu1), doc-base:i386 (0.10.5), unity-scope-yelp:i386 (0.1+13.10.20130723-0ubuntu1), libpocketsphinx1:i386 (0.8.0+real-0ubuntu6), checkbox-ng:i386 (0.3-2), libqtcore4:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), friends:i386 (0.2.0+14.04.20140217.1-0ubuntu1), unity-scope-gdrive:i386 (0.9+13.10.20130723-0ubuntu1), geoclue-ubuntu-geoip:i386 (1.0.2+14.04.20131125-0ubuntu2), thunderbird-locale-en:i386 (24.5.0+build1-0ubuntu0.14.04.1), libdecoration0:i386 (0.9.11+14.04.20140409-0ubuntu1), signon-plugin-password:i386 (8.56+14.04.20140307-0ubuntu2), libqt4-svg:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), unity-scope-home:i386 (6.8.2+14.04.20131029.1-0ubuntu1), libqt5sql5-sqlite:i386 (5.2.1+dfsg-1ubuntu14), libqt5svg5:i386 (5.2.1-1), libqt4-opengl:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), notify-osd:i386 (0.9.35+14.04.20140213-0ubuntu1), qtcore4-l10n:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), friends-facebook:i386 (0.2.0+14.04.20140217.1-0ubuntu1), libqt4-scripttools:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), unity-control-center:i386 (14.04.3+14.04.20140410-0ubuntu1), libqt4-help:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), nux-tools:i386 (4.0.6+14.04.20140409-0ubuntu1), gir1.2-messagingmenu-1.0:i386 (13.10.1+14.04.20140410-0ubuntu1), qtdeclarative5-ubuntu-ui-toolkit-plugin:i386 (0.1.46+14.04.20140408.1-0ubuntu1), plainbox-secure-policy:i386 (0.5.3-2), unity-scope-musicstores:i386 (6.9.0+13.10.20131011-0ubuntu1), qtdeclarative5-accounts-plugin:i386 (0.4+14.04.20140317-0ubuntu1), indicator-printers:i386 (0.1.7+14.04.20140313-0ubuntu1), unity-scope-texdoc:i386 (0.1+14.04.20140328-0ubuntu1), unity-scope-video-remote:i386 (0.3.15+13.10.20130920-0ubuntu1), remmina-plugin-vnc:i386 (1.0.0-4ubuntu3), liboxideqt-qmlplugin:i386 (1.0.0~bzr501-0ubuntu2), overlay-scrollbar-gtk2:i386 (0.2.16+r359+14.04.20131129-0ubuntu1), overlay-scrollbar-gtk3:i386 (0.2.16+r359+14.04.20131129-0ubuntu1), indicator-datetime:i386 (13.10.0+14.04.20140415.3-0ubuntu1), qtdeclarative5-window-plugin:i386 (5.2.1-3ubuntu15), libqt5sql5:i386 (5.2.1+dfsg-1ubuntu14), gnomine:i386 (3.10.1-0ubuntu1), compiz:i386 (0.9.11+14.04.20140409-0ubuntu1), unity-scopes-runner:i386 (7.1.4+14.04.20140210-0ubuntu1), onboard-data:i386 (1.0.0-0ubuntu4), python3-checkbox-support:i386 (0.2-1), libqt5qml5:i386 (5.2.1-3ubuntu15), indicator-power:i386 (12.10.6+14.04.20140411-0ubuntu1), gstreamer1.0-plugins-base-apps:i386 (1.2.3-1), gstreamer1.0-tools:i386 (1.2.3-1), libxcb-randr0:i386 (1.10-2ubuntu1), python3-feedparser:i386 (5.1.3-2), thunderbird:i386 (24.5.0+build1-0ubuntu0.14.04.1), whoopsie-preferences:i386 (0.12), qdbus:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), libmetacity-private0a:i386 (2.34.13-0ubuntu4), libaccounts-qt5-1:i386 (1.11+14.04.20140410.1-0ubuntu1), account-plugin-yahoo:i386 (3.8.6-0ubuntu9), ubuntu-session:i386 (3.9.90-0ubuntu12), libsignon-qt5-1:i386 (8.56+14.04.20140307-0ubuntu2), libqt4-designer:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), libqtassistantclient4:i386 (4.6.3-6), unity-webapps-common:i386 (2.4.17+14.04.20140416-0ubuntu1), unity-lens-video:i386 (0.3.15+13.10.20130920-0ubuntu1), friends-dispatcher:i386 (0.2.0+14.04.20140217.1-0ubuntu1), libunity-webapps0:i386 (2.5.0~+14.04.20140409-0ubuntu1), activity-log-manager-control-center:i386 (0.9.7-0ubuntu14), unity-webapps-qml:i386 (0.1+14.04.20140408-0ubuntu1), checkbox-gui:i386 (0.17.6-0ubuntu6), example-content:i386 (48), appmenu-qt5:i386 (0.3.0+14.04.20140415-0ubuntu1), libqt5network5:i386 (5.2.1+dfsg-1ubuntu14), libtimezonemap1:i386 (0.4.1), indicator-sound:i386 (12.10.2+14.04.20140401-0ubuntu1), libglew1.10:i386 (1.10.0-3), libhud2:i386 (13.10.1+14.04.20140402-0ubuntu1), account-plugin-jabber:i386 (3.8.6-0ubuntu9), ubuntu-wallpapers-trusty:i386 (14.04.0.1-0ubuntu1), notify-osd-icons:i386 (0.8+14.04.20131204-0ubuntu1), qt-at-spi:i386 (0.3.1-4fakesync1), libqt5feedback5:i386 (5.0~git20130529-0ubuntu3), liburl-dispatcher1:i386 (0.1+14.04.20140403-0ubuntu1), mcp-account-manager-uoa:i386 (3.8.6-0ubuntu9), unity-scope-gourmet:i386 (0.1+13.10.20130723-0ubuntu1), unity:i386 (7.2.0+14.04.20140423-0ubuntu1.2), libprotobuf8:i386 (2.5.0-9ubuntu1), libqt5quick5:i386 (5.2.1-3ubuntu15), qtdeclarative5-dialogs-plugin:i386 (5.2.1-3ubuntu15), libqt5widgets5:i386 (5.2.1+dfsg-1ubuntu14), libunity-core-6.0-9:i386 (7.2.0+14.04.20140423-0ubuntu1.2), libqt5multimedia5:i386 (5.2.1-0ubuntu5), python-qt4-dbus:i386 (4.10.4+dfsg-1ubuntu1), lightdm:i386 (1.10.0-0ubuntu3), libqt4-dbus:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), language-selector-gnome:i386 (0.129), libunity-misc4:i386 (4.0.5+14.04.20140115-0ubuntu1), liblightdm-gobject-1-0:i386 (1.10.0-0ubuntu3), libqt5xml5:i386 (5.2.1+dfsg-1ubuntu14), gir1.2-ebookcontacts-1.2:i386 (3.10.4-0ubuntu1), gstreamer0.10-tools:i386 (0.10.36-1.2ubuntu3), unity-scope-firefoxbookmarks:i386 (0.1+13.10.20130809.1-0ubuntu1), indicator-messages:i386 (13.10.1+14.04.20140410-0ubuntu1), unity-webapps-service:i386 (2.5.0~+14.04.20140409-0ubuntu1), webaccounts-extension-common:i386 (0.5-0ubuntu2), unity-services:i386 (7.2.0+14.04.20140423-0ubuntu1.2), compiz-gnome:i386 (0.9.11+14.04.20140409-0ubuntu1), unity-scope-colourlovers:i386 (0.1+13.10.20130723-0ubuntu1), dmz-cursor-theme:i386 (0.4.4ubuntu1), libqt5organizer5:i386 (5.0~git20140203~e0c5eebe-0ubuntu2), unity-scope-clementine:i386 (0.1+13.10.20130723-0ubuntu1), unity-scope-virtualbox:i386 (0.1+13.10.20130723-0ubuntu1), telepathy-indicator:i386 (0.3.1+14.04.20140411-0ubuntu1), unity-scopes-master-default:i386 (6.8.2+14.04.20131029.1-0ubuntu1), plymouth-theme-ubuntu-logo:i386 (0.8.8-0ubuntu17), python-qt4:i386 (4.10.4+dfsg-1ubuntu1), unity-lens-applications:i386 (7.1.0+13.10.20131011-0ubuntu2), libqtdbus4:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), unity-lens-music:i386 (6.9.0+13.10.20131011-0ubuntu1), unity-scope-openclipart:i386 (0.1+13.10.20130723-0ubuntu1), libqt5qml-graphicaleffects:i386 (5.2.1-1), libqt5opengl5:i386 (5.2.1+dfsg-1ubuntu14), unity-gtk-module-common:i386 (0.0.0+14.04.20140403-0ubuntu1), indicator-appmenu:i386 (13.01.0+14.04.20140404-0ubuntu1), libaccount-plugin-google:i386 (0.11+14.04.20140409.1-0ubuntu1), sphinx-voxforge-lm-en:i386 (0.1.1~daily20130301-0ubuntu1), libfreerdp-plugins-standard:i386 (1.0.2-2ubuntu1), remmina:i386 (1.0.0-4ubuntu3), unity-scope-gmusicbrowser:i386 (0.1+13.10.20130723-0ubuntu1), unity-gtk2-module:i386 (0.0.0+14.04.20140403-0ubuntu1), ethtool:i386 (3.13-1), libnux-4.0-common:i386 (4.0.6+14.04.20140409-0ubuntu1), unity-scope-devhelp:i386 (0.1+14.04.20140328-0ubuntu1), appmenu-qt:i386 (0.2.7+14.04.20140305-0ubuntu1), ubuntu-wallpapers:i386 (14.04.0.1-0ubuntu1), gtk3-engines-unico:i386 (1.0.3+14.04.20140109-0ubuntu1), libunity-action-qt1:i386 (1.1.0+14.04.20140304-0ubuntu1), totem-mozilla:i386 (3.10.1-1ubuntu4), libfreerdp1:i386 (1.0.2-2ubuntu1), libcompizconfig0:i386 (0.9.11+14.04.20140409-0ubuntu1), qtchooser:i386 (39-g4717841-3), activity-log-manager:i386 (0.9.7-0ubuntu14), libsphinxbase1:i386 (0.8-0ubuntu10), libaccount-plugin-generic-oauth:i386 (0.11+14.04.20140409.1-0ubuntu1), gsettings-ubuntu-schemas:i386 (0.0.1+14.04.20140401-0ubuntu1), libqt4-network:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), unity-scope-guayadeque:i386 (0.1+13.10.20130927.1-0ubuntu1), unity-scope-tomboy:i386 (0.1+13.10.20130723-0ubuntu1), xul-ext-webaccounts:i386 (0.5-0ubuntu2), account-plugin-google:i386 (0.11+14.04.20140409.1-0ubuntu1), libqt4-script:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), gir1.2-accounts-1.0:i386 (1.15+14.04.20131126.2-0ubuntu3), plainbox-provider-checkbox:i386 (0.4-1), pm-utils:i386 (1.4.1-13), account-plugin-salut:i386 (3.8.6-0ubuntu9), python3-urllib3:i386 (1.7.1-1build1), xul-ext-unity:i386 (3.0.0+14.04.20140416-0ubuntu1), libwnck22:i386 (2.30.7-0ubuntu4), qtdeclarative5-ubuntu-ui-extras-browser-plugin:i386 (0.23+14.04.20140422-0ubuntu1), gir1.2-appindicator3-0.1:i386 (12.10.1+13.10.20130920-0ubuntu4), libqtwebkit4:i386 (2.3.2-0ubuntu7), unity-lens-friends:i386 (0.1.3+14.04.20140317-0ubuntu1), libaccount-plugin-1.0-0:i386 (0.1.7~+14.04.20140211.2-0ubuntu4), libupstart1:i386 (1.12.1-0ubuntu4), metacity-common:i386 (2.34.13-0ubuntu4), libgee2:i386 (0.6.8-1ubuntu1), qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets:i386 (0.23+14.04.20140422-0ubuntu1), indicator-keyboard:i386 (0.0.0+14.04.20140410.1-0ubuntu1), unity-scope-audacious:i386 (0.1+13.10.20130927.1-0ubuntu1), unity-scope-zotero:i386 (0.1+13.10.20130723-0ubuntu1), bamfdaemon:i386 (0.5.1+14.04.20140409-0ubuntu1), gnome-screensaver:i386 (3.6.1-0ubuntu13), account-plugin-flickr:i386 (0.11+14.04.20140409.1-0ubuntu1), landscape-client-ui-install:i386 (14.01-0ubuntu3), libufe-xidgetter0:i386 (3.0.0+14.04.20140416-0ubuntu1), signon-keyring-extension:i386 (0.6+14.04.20140307-0ubuntu1), libqt5webkit5-qmlwebkitplugin:i386 (5.1.1-1ubuntu8), signond:i386 (8.56+14.04.20140307-0ubuntu2), libuuid-perl:i386 (0.05-1), libfriends0:i386 (0.1.2+14.04.20131108.1-0ubuntu1), libwnck-common:i386 (2.30.7-0ubuntu4), gir1.2-edataserver-1.2:i386 (3.10.4-0ubuntu1), ubuntuone-client-data:i386 (13.05-0ubuntu1), unity-control-center-signon:i386 (0.1.7~+14.04.20140211.2-0ubuntu4), libx86-1:i386 (1.1+ds1-10), libsignon-extension1:i386 (8.56+14.04.20140307-0ubuntu2), libqt5printsupport5:i386 (5.2.1+dfsg-1ubuntu14), signon-ui:i386 (0.16+14.04.20140304.is.0.15+14.04.20140313-0ubuntu1), indicator-bluetooth:i386 (0.0.6+14.04.20140207-0ubuntu2), libqt5test5:i386 (5.2.1+dfsg-1ubuntu14), checkbox-ng-service:i386 (0.3-2), qtdeclarative5-unity-action-plugin:i386 (1.1.0+14.04.20140304-0ubuntu1), indicator-session:i386 (12.10.5+14.04.20140410-0ubuntu1), libcolumbus1-common:i386 (1.1.0+14.04.20140325.3-0ubuntu1), unity-greeter:i386 (14.04.9-0ubuntu1), onboard:i386 (1.0.0-0ubuntu4), plainbox-provider-resource-generic:i386 (0.3-1), sphinx-voxforge-hmm-en:i386 (0.1.1~daily20130301-0ubuntu1), libwhoopsie-preferences0:i386 (0.12), compiz-core:i386 (0.9.11+14.04.20140409-0ubuntu1), libvncserver0:i386 (0.9.9+dfsg-1ubuntu1), ubuntu-docs:i386 (14.04.3), remmina-common:i386 (1.0.0-4ubuntu3), webbrowser-app:i386 (0.23+14.04.20140422-0ubuntu1), libsignon-plugins-common1:i386 (8.56+14.04.20140307-0ubuntu2), libqt4-xmlpatterns:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), libunityvoice1:i386 (0.1+14.04.20140304-0ubuntu1), libqt5gui5:i386 (5.2.1+dfsg-1ubuntu14), vbetool:i386 (1.1-3), qtdeclarative5-localstorage-plugin:i386 (5.2.1-3ubuntu15), remmina-plugin-rdp:i386 (1.0.0-4ubuntu3), unity-lens-photos:i386 (1.0+14.04.20140318-0ubuntu1), unity-voice-service:i386 (0.1+14.04.20140304-0ubuntu1), branding-ubuntu:i386 (0.8), libqtgui4:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), libqt5core5a:i386 (5.2.1+dfsg-1ubuntu14), sni-qt:i386 (0.2.6-0ubuntu1), friends-twitter:i386 (0.2.0+14.04.20140217.1-0ubuntu1), hud:i386 (13.10.1+14.04.20140402-0ubuntu1), ubuntu-ui-toolkit-theme:i386 (0.1.46+14.04.20140408.1-0ubuntu1), python3-plainbox:i386 (0.5.3-2), libqt4-declarative:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), python3-requests:i386 (2.2.1-1), libgsettings-qt1:i386 (0.1+14.04.20140408-0ubuntu1), compiz-plugins-default:i386 (0.9.11+14.04.20140409-0ubuntu1), libqt5positioning5:i386 (5.2.1-1ubuntu2), gir1.2-signon-1.0:i386 (1.10daily13.06.25-0ubuntu2), account-plugin-windows-live:i386 (0.11+14.04.20140409.1-0ubuntu1), ubuntu-sso-client-qt:i386 (13.10-0ubuntu6), python3-lxml:i386 (3.3.3-1), xcursor-themes:i386 (1.0.3-1), unity-asset-pool:i386 (0.8.24daily13.06.10-0ubuntu1), python-sip:i386 (4.15.5-1build1), libqt4-test:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), qtdeclarative5-privatewidgets-plugin:i386 (5.2.1-3ubuntu15), pkg-config:i386 (0.26-1ubuntu4), python3-checkbox-ng:i386 (0.3-2), thunderbird-gnome-support:i386 (24.5.0+build1-0ubuntu0.14.04.1), light-themes:i386 (14.04+14.04.20140410-0ubuntu1), unity-scope-calculator:i386 (0.1+14.04.20140328-0ubuntu1), gnome-power-manager:i386 (3.8.2-1ubuntu2), libreoffice-style-human:i386 (4.2.3~rc3-0ubuntu2), ubuntu-mono:i386 (14.04+14.04.20140410-0ubuntu1), libcolumbus1:i386 (1.1.0+14.04.20140325.3-0ubuntu1), libbamf3-2:i386 (0.5.1+14.04.20140409-0ubuntu1), unity-scope-chromiumbookmarks:i386 (0.1+13.10.20130723-0ubuntu1), libaudio2:i386 (1.9.4-1), unity-scope-musique:i386 (0.1+13.10.20130723-0ubuntu1), libqt4-xml:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), libqt5dbus5:i386 (5.2.1+dfsg-1ubuntu14), libxcb-xkb1:i386 (1.10-2ubuntu1), libnux-4.0-0:i386 (4.0.6+14.04.20140409-0ubuntu1), adium-theme-ubuntu:i386 (0.3.4-0ubuntu1), account-plugin-facebook:i386 (0.11+14.04.20140409.1-0ubuntu1), unity-scope-manpages:i386 (3.0+14.04.20140324-0ubuntu1), qtdeclarative5-qtquick2-plugin:i386 (5.2.1-3ubuntu15), account-plugin-twitter:i386 (0.11+14.04.20140409.1-0ubuntu1), libthumbnailer0:i386 (1.1+14.04.20140401.1-0ubuntu1), gir1.2-ebook-1.2:i386 (3.10.4-0ubuntu1), ubuntu-settings:i386 (14.04.5), python3-pyparsing:i386 (2.0.1+dfsg1-1build1), libglewmx1.10:i386 (1.10.0-3), libxcb-render-util0:i386 (0.3.8-1.1ubuntu1), gstreamer0.10-plugins-base-apps:i386 (0.10.36-1.1ubuntu2), signon-plugin-oauth2:i386 (0.19+14.04.20140305-0ubuntu2), libssh-4:i386 (0.6.1-0ubuntu3), libunity-gtk3-parser0:i386 (0.0.0+14.04.20140403-0ubuntu1), overlay-scrollbar:i386 (0.2.16+r359+14.04.20131129-0ubuntu1), libunity-gtk2-parser0:i386 (0.0.0+14.04.20140403-0ubuntu1), libqt5sensors5:i386 (5.2.1+dfsg-2ubuntu2), libyaml-tiny-perl:i386 (1.56-1), libqt4-sql:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), libdbusmenu-qt2:i386 (0.9.3+14.04.20140314-0ubuntu1), libdbusmenu-qt5:i386 (0.9.3+14.04.20140314-0ubuntu1), thunderbird-locale-en-us:i386 (24.5.0+build1-0ubuntu0.14.04.1), unity-lens-files:i386 (7.1.0+13.10.20130920-0ubuntu1), xul-ext-websites-integration:i386 (2.3.6+13.10.20130920.1-0ubuntu1), account-plugin-aim:i386 (3.8.6-0ubuntu9), gtk2-engines-murrine:i386 (0.98.2-0ubuntu2), webapp-container:i386 (0.23+14.04.20140422-0ubuntu1), ubuntu-artwork:i386 (14.04+14.04.20140410-0ubuntu1), libqt4-sql-sqlite:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), libqt5webkit5:i386 (5.1.1-1ubuntu8), qtdeclarative5-qtfeedback-plugin:i386 (5.0~git20130529-0ubuntu3), liboxideqtcore0:i386 (1.0.0~bzr501-0ubuntu2), python-gconf:i386 (2.28.1+dfsg-1ubuntu2), ubuntu-sounds:i386 (0.13)
End-Date: 2014-05-05  09:52:19
```

And /var/log/apt/term.log:

```
Log started: 2014-05-05  09:47:24
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 179854 files and directories currently installed.)
Removing account-plugin-aim (3.8.6-0ubuntu9) ...
Removing friends-facebook (0.2.0+14.04.20140217.1-0ubuntu1) ...
Removing account-plugin-facebook (0.11+14.04.20140409.1-0ubuntu1) ...
Removing account-plugin-flickr (0.11+14.04.20140409.1-0ubuntu1) ...
Removing unity-scope-gdrive (0.9+13.10.20130723-0ubuntu1) ...
Removing account-plugin-google (0.11+14.04.20140409.1-0ubuntu1) ...
Removing account-plugin-jabber (3.8.6-0ubuntu9) ...
Removing account-plugin-salut (3.8.6-0ubuntu9) ...
Removing friends-twitter (0.2.0+14.04.20140217.1-0ubuntu1) ...
Removing account-plugin-twitter (0.11+14.04.20140409.1-0ubuntu1) ...
Removing account-plugin-windows-live (0.11+14.04.20140409.1-0ubuntu1) ...
Removing account-plugin-yahoo (3.8.6-0ubuntu9) ...
Removing activity-log-manager-control-center (0.9.7-0ubuntu14) ...
Removing activity-log-manager (0.9.7-0ubuntu14) ...
Removing ubuntu-artwork (1:14.04+14.04.20140410-0ubuntu1) ...
Removing adium-theme-ubuntu (0.3.4-0ubuntu1) ...
Removing appmenu-qt (0.2.7+14.04.20140305-0ubuntu1) ...
Removing appmenu-qt5 (0.3.0+14.04.20140415-0ubuntu1) ...
Removing unity (7.2.0+14.04.20140423-0ubuntu1.2) ...
Removing bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Removing branding-ubuntu (0.8) ...
Removing 'diversion of /usr/share/aisleriot/pixmaps/slot.svg to /usr/share/aisleriot/pixmaps/slot.svg.unbranded by branding-ubuntu'
Removing 'diversion of /usr/share/aisleriot/pixmaps/baize.png to /usr/share/aisleriot/pixmaps/baize.png.unbranded by branding-ubuntu'
Removing 'diversion of /usr/share/aisleriot/cards/bonded.svg to /usr/share/aisleriot/cards/bonded.svg.unbranded by branding-ubuntu'
Removing 'diversion of /usr/share/gnome-mahjongg/themes/postmodern.svg to /usr/share/gnome-mahjongg/themes/postmodern.svg.unbranded by branding-ubuntu'
Removing checkbox-gui (0.17.6-0ubuntu6) ...
Removing checkbox-ng-service (0.3-2) ...
Removing checkbox-ng (0.3-2) ...
Removing compiz (1:0.9.11+14.04.20140409-0ubuntu1) ...
Removing compiz-gnome (1:0.9.11+14.04.20140409-0ubuntu1) ...
Removing libcompizconfig0 (1:0.9.11+14.04.20140409-0ubuntu1) ...
Removing compiz-plugins-default (1:0.9.11+14.04.20140409-0ubuntu1) ...
Removing compiz-core (1:0.9.11+14.04.20140409-0ubuntu1) ...
Removing dmz-cursor-theme (0.4.4ubuntu1) ...
update-alternatives: using /usr/share/icons/Adwaita/cursor.theme to provide /usr/share/icons/default/index.theme (x-cursor-theme) in auto mode
Removing doc-base (0.10.5) ...
Removing ethtool (1:3.13-1) ...
Removing example-content (48) ...
Removing unity-lens-friends (0.1.3+14.04.20140317-0ubuntu1) ...
Removing friends (0.2.0+14.04.20140217.1-0ubuntu1) ...
Removing libfriends0:i386 (0.1.2+14.04.20131108.1-0ubuntu1) ...
Removing friends-dispatcher (0.2.0+14.04.20140217.1-0ubuntu1) ...
Removing unity-webapps-common (2.4.17+14.04.20140416-0ubuntu1) ...
Removing xul-ext-unity (3.0.0+14.04.20140416-0ubuntu1) ...
Removing xul-ext-websites-integration (2.3.6+13.10.20130920.1-0ubuntu1) ...
Removing unity-lens-photos (1.0+14.04.20140318-0ubuntu1) ...
Removing gir1.2-accounts-1.0 (1.15+14.04.20131126.2-0ubuntu3) ...
Removing gir1.2-appindicator3-0.1 (12.10.1+13.10.20130920-0ubuntu4) ...
Removing gir1.2-ebook-1.2 (3.10.4-0ubuntu1) ...
Removing gir1.2-ebookcontacts-1.2 (3.10.4-0ubuntu1) ...
Removing gir1.2-edataserver-1.2 (3.10.4-0ubuntu1) ...
Removing gir1.2-messagingmenu-1.0 (13.10.1+14.04.20140410-0ubuntu1) ...
Removing gir1.2-signon-1.0 (1.10daily13.06.25-0ubuntu2) ...
Removing gnome-power-manager (3.8.2-1ubuntu2) ...
Removing gnome-screensaver (3.6.1-0ubuntu13) ...
Removing gnomine (1:3.10.1-0ubuntu1) ...
Removing xul-ext-webaccounts (0.5-0ubuntu2) ...
Removing webaccounts-extension-common (0.5-0ubuntu2) ...
Removing unity-control-center-signon (0.1.7~+14.04.20140211.2-0ubuntu4) ...
Removing unity-control-center (14.04.3+14.04.20140410-0ubuntu1) ...
Removing ubuntu-session (3.9.90-0ubuntu12) ...
Removing unity-settings-daemon (14.04.0+14.04.20140414-0ubuntu1) ...
Removing indicator-sound (12.10.2+14.04.20140401-0ubuntu1) ...
Removing gsettings-ubuntu-schemas (0.0.1+14.04.20140401-0ubuntu1) ...
Removing gstreamer0.10-plugins-base-apps (0.10.36-1.1ubuntu2) ...
Removing gstreamer0.10-tools (0.10.36-1.2ubuntu3) ...
Removing gstreamer1.0-plugins-base-apps (1.2.3-1) ...
Removing gstreamer1.0-tools (1.2.3-1) ...
Removing light-themes (14.04+14.04.20140410-0ubuntu1) ...
Removing gtk2-engines-murrine:i386 (0.98.2-0ubuntu2) ...
Removing gtk3-engines-unico:i386 (1.0.3+14.04.20140109-0ubuntu1) ...
Removing hud (13.10.1+14.04.20140402-0ubuntu1) ...
Removing indicator-appmenu (13.01.0+14.04.20140404-0ubuntu1) ...
Removing indicator-datetime (13.10.0+14.04.20140415.3-0ubuntu1) ...
Removing indicator-keyboard (0.0.0+14.04.20140410.1-0ubuntu1) ...
dpkg: warning: while removing indicator-keyboard, directory '/usr/lib/python2.7/dist-packages/indicator_keyboard/tests' not empty so not removed
Removing indicator-messages (13.10.1+14.04.20140410-0ubuntu1) ...
Removing indicator-power (12.10.6+14.04.20140411-0ubuntu1) ...
Removing indicator-printers (0.1.7+14.04.20140313-0ubuntu1) ...
Removing indicator-session (12.10.5+14.04.20140410-0ubuntu1) ...
Removing landscape-client-ui-install (14.01-0ubuntu3) ...
Removing language-selector-gnome (0.129) ...
Removing mcp-account-manager-uoa (3.8.6-0ubuntu9) ...
Removing libaccount-plugin-google (0.11+14.04.20140409.1-0ubuntu1) ...
Removing libaccount-plugin-generic-oauth (0.11+14.04.20140409.1-0ubuntu1) ...
Removing signon-plugin-oauth2 (0.19+14.04.20140305-0ubuntu2) ...
Removing signon-ui (0.16+14.04.20140304.is.0.15+14.04.20140313-0ubuntu1) ...
Removing sni-qt:i386 (0.2.6-0ubuntu1) ...
Removing qt-at-spi:i386 (0.3.1-4fakesync1) ...
Removing libbamf3-2:i386 (0.5.1+14.04.20140409-0ubuntu1) ...
Removing unity-lens-applications (7.1.0+13.10.20131011-0ubuntu2) ...
Removing libcolumbus1:i386 (1.1.0+14.04.20140325.3-0ubuntu1) ...
Removing libcolumbus1-common (1.1.0+14.04.20140325.3-0ubuntu1) ...
Removing libdbusmenu-qt2:i386 (0.9.3+14.04.20140314-0ubuntu1) ...
Removing libdbusmenu-qt5:i386 (0.9.3+14.04.20140314-0ubuntu1) ...
Removing libdecoration0 (1:0.9.11+14.04.20140409-0ubuntu1) ...
Removing remmina-plugin-rdp (1.0.0-4ubuntu3) ...
Removing libfreerdp-plugins-standard:i386 (1.0.2-2ubuntu1) ...
Removing libfreerdp1:i386 (1.0.2-2ubuntu1) ...
Removing unity-scope-video-remote (0.3.15+13.10.20130920-0ubuntu1) ...
Removing unity-scope-musicstores (6.9.0+13.10.20131011-0ubuntu1) ...
Removing libunity-core-6.0-9 (7.2.0+14.04.20140423-0ubuntu1.2) ...
Removing libnux-4.0-0 (4.0.6+14.04.20140409-0ubuntu1) ...
Removing libglew1.10:i386 (1.10.0-3) ...
Removing libglewmx1.10:i386 (1.10.0-3) ...
Removing libgsettings-qt1:i386 (0.1+14.04.20140408-0ubuntu1) ...
Removing unity-greeter (14.04.9-0ubuntu1) ...
Removing liblightdm-gobject-1-0 (1.10.0-0ubuntu3) ...
Removing libmetacity-private0a (1:2.34.13-0ubuntu4) ...
Removing libnux-4.0-common (4.0.6+14.04.20140409-0ubuntu1) ...
Removing libunityvoice1:i386 (0.1+14.04.20140304-0ubuntu1) ...
Removing unity-voice-service:i386 (0.1+14.04.20140304-0ubuntu1) ...
Removing libpocketsphinx1 (0.8.0+real-0ubuntu6) ...
Removing libprotobuf8:i386 (2.5.0-9ubuntu1) ...
Removing ubuntu-sso-client-qt (13.10-0ubuntu6) ...
Removing python-qt4 (4.10.4+dfsg-1ubuntu1) ...
Removing libqt4-dbus:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-designer:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-help:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqtwebkit4:i386 (2.3.2-0ubuntu7) ...
Removing libqtassistantclient4:i386 (4.6.3-6) ...
Removing libqt4-opengl:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-scripttools:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-sql-sqlite:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-svg:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-test:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing qdbus (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing signon-plugin-password (8.56+14.04.20140307-0ubuntu2) ...
Removing signon-keyring-extension (0.6+14.04.20140307-0ubuntu1) ...
Removing qtdeclarative5-localstorage-plugin:i386 (5.2.1-3ubuntu15) ...
Removing libqt5test5:i386 (5.2.1+dfsg-1ubuntu14) ...
Removing python-qt4-dbus (4.10.4+dfsg-1ubuntu1) ...
Removing libreoffice-style-human (1:4.2.3~rc3-0ubuntu2) ...
Removing libsphinxbase1 (0.8-0ubuntu10) ...
Removing remmina-plugin-vnc (1.0.0-4ubuntu3) ...
Removing remmina (1.0.0-4ubuntu3) ...
Removing libssh-4:i386 (0.6.1-0ubuntu3) ...
Removing libtimezonemap1 (0.4.1) ...
Removing libufe-xidgetter0 (3.0.0+14.04.20140416-0ubuntu1) ...
Removing unity-gtk2-module:i386 (0.0.0+14.04.20140403-0ubuntu1) ...
Removing libunity-gtk2-parser0:i386 (0.0.0+14.04.20140403-0ubuntu1) ...
Removing unity-gtk3-module:i386 (0.0.0+14.04.20140403-0ubuntu1) ...
Removing libunity-gtk3-parser0:i386 (0.0.0+14.04.20140403-0ubuntu1) ...
Removing libunity-misc4 (4.0.5+14.04.20140115-0ubuntu1) ...
Removing unity-services (7.2.0+14.04.20140423-0ubuntu1.2) ...
Removing libupstart1:i386 (1.12.1-0ubuntu4) ...
Removing libuuid-perl (0.05-1) ...
Removing libvncserver0:i386 (0.9.9+dfsg-1ubuntu1) ...
Removing whoopsie-preferences (0.12) ...
Removing libwhoopsie-preferences0 (0.12) ...
Removing libwnck22 (1:2.30.7-0ubuntu4) ...
Removing libwnck-common (1:2.30.7-0ubuntu4) ...
Removing vbetool (1.1-3) ...
Removing libx86-1:i386 (1.1+ds1-10) ...
Removing libyaml-tiny-perl (1.56-1) ...
Removing lightdm (1.10.0-0ubuntu3) ...
Removing metacity-common (1:2.34.13-0ubuntu4) ...
Removing notify-osd (0.9.35+14.04.20140213-0ubuntu1) ...
Removing notify-osd-icons (0.8+14.04.20131204-0ubuntu1) ...
Removing nux-tools (4.0.6+14.04.20140409-0ubuntu1) ...
Removing onboard-data (1.0.0-0ubuntu4) ...
Removing onboard (1.0.0-0ubuntu4) ...
Removing pkg-config (0.26-1ubuntu4) ...
Removing plainbox-provider-checkbox (0.4-1) ...
Removing plainbox-provider-resource-generic (0.3-1) ...
Removing python3-checkbox-ng (0.3-2) ...
Removing python3-plainbox (0.5.3-2) ...
Removing plainbox-secure-policy (0.5.3-2) ...
Removing plymouth-theme-ubuntu-logo (0.8.8-0ubuntu17) ...
update-initramfs: deferring update (trigger activated)
Removing pm-utils (1.4.1-13) ...
Removing python-gconf (2.28.1+dfsg-1ubuntu2) ...
Removing python-sip (4.15.5-1build1) ...
Removing python3-checkbox-support (0.2-1) ...
Removing unity-scope-openclipart (0.1+13.10.20130723-0ubuntu1) ...
Removing python3-feedparser (5.1.3-2) ...
Removing unity-scope-devhelp (0.1+14.04.20140328-0ubuntu1) ...
Removing python3-lxml (3.3.3-1) ...
Removing python3-pyparsing (2.0.1+dfsg1-1build1) ...
Removing python3-requests (2.2.1-1) ...
Removing python3-urllib3 (1.7.1-1build1) ...
Removing qtchooser (39-g4717841-3) ...
Removing remmina-common (1.0.0-4ubuntu3) ...
Removing sphinx-voxforge-hmm-en (0.1.1~daily20130301-0ubuntu1) ...
Removing sphinx-voxforge-lm-en (0.1.1~daily20130301-0ubuntu1) ...
Removing telepathy-indicator (0.3.1+14.04.20140411-0ubuntu1) ...
Removing thunderbird-locale-en-us (1:24.5.0+build1-0ubuntu0.14.04.1) ...
Removing thunderbird-locale-en (1:24.5.0+build1-0ubuntu0.14.04.1) ...
Removing thunderbird-gnome-support (1:24.5.0+build1-0ubuntu0.14.04.1) ...
Removing thunderbird (1:24.5.0+build1-0ubuntu0.14.04.1) ...
Removing totem-mozilla (3.10.1-1ubuntu4) ...
Removing ubuntu-docs (14.04.3) ...
Removing ubuntu-mono (14.04+14.04.20140410-0ubuntu1) ...
Removing ubuntu-settings (14.04.5) ...
Removing ubuntu-sounds (0.13) ...
Removing ubuntu-wallpapers (14.04.0.1-0ubuntu1) ...
Removing ubuntu-wallpapers-trusty (14.04.0.1-0ubuntu1) ...
Removing ubuntuone-client-data (13.05-0ubuntu1) ...
Removing unity-asset-pool (0.8.24daily13.06.10-0ubuntu1) ...
Removing unity-gtk-module-common (0.0.0+14.04.20140403-0ubuntu1) ...
Removing unity-lens-files (7.1.0+13.10.20130920-0ubuntu1) ...
Removing unity-lens-video (0.3.15+13.10.20130920-0ubuntu1) ...
Removing unity-lens-music (6.9.0+13.10.20131011-0ubuntu1) ...
Removing unity-scope-audacious (0.1+13.10.20130927.1-0ubuntu1) ...
Removing unity-scope-calculator (0.1+14.04.20140328-0ubuntu1) ...
Removing unity-scope-chromiumbookmarks (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scope-clementine (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scope-colourlovers (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scope-firefoxbookmarks (0.1+13.10.20130809.1-0ubuntu1) ...
Removing unity-scope-gmusicbrowser (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scope-gourmet (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scope-guayadeque (0.1+13.10.20130927.1-0ubuntu1) ...
Removing unity-scope-home (6.8.2+14.04.20131029.1-0ubuntu1) ...
Removing unity-scope-manpages (3.0+14.04.20140324-0ubuntu1) ...
Removing unity-scope-musique (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scope-texdoc (0.1+14.04.20140328-0ubuntu1) ...
Removing unity-scope-tomboy (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scope-virtualbox (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scope-yelp (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scope-zotero (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scopes-master-default (6.8.2+14.04.20131029.1-0ubuntu1) ...
Removing unity-scopes-runner (7.1.4+14.04.20140210-0ubuntu1) ...
Removing xcursor-themes (1.0.3-1) ...
Removing indicator-bluetooth (0.0.6+14.04.20140207-0ubuntu2) ...
Removing libaccount-plugin-1.0-0 (0.1.7~+14.04.20140211.2-0ubuntu4) ...
Removing libgee2:i386 (0.6.8-1ubuntu1) ...
Removing signond (8.56+14.04.20140307-0ubuntu2) ...
Removing libsignon-plugins-common1 (8.56+14.04.20140307-0ubuntu2) ...
Removing libsignon-extension1 (8.56+14.04.20140307-0ubuntu2) ...
Removing liburl-dispatcher1:i386 (0.1+14.04.20140403-0ubuntu1) ...
Removing overlay-scrollbar-gtk2:i386 (0.2.16+r359+14.04.20131129-0ubuntu1) ...
Removing overlay-scrollbar-gtk3:i386 (0.2.16+r359+14.04.20131129-0ubuntu1) ...
Removing libqt4-declarative:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-script:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-sql:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-xmlpatterns:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing overlay-scrollbar (0.2.16+r359+14.04.20131129-0ubuntu1) ...
Removing libunity-webapps0 (2.5.0~+14.04.20140409-0ubuntu1) ...
Removing unity-webapps-service (2.5.0~+14.04.20140409-0ubuntu1) ...
Removing geoclue-ubuntu-geoip (1.0.2+14.04.20131125-0ubuntu2) ...
Removing webapp-container (0.23+14.04.20140422-0ubuntu1) ...
Removing unity-webapps-qml (0.1+14.04.20140408-0ubuntu1) ...
Removing qtdeclarative5-accounts-plugin (0.4+14.04.20140317-0ubuntu1) ...
Removing libaccounts-qt5-1 (1.11+14.04.20140410.1-0ubuntu1) ...
Removing libqtgui4:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libaudio2:i386 (1.9.4-1) ...
Removing webbrowser-app (0.23+14.04.20140422-0ubuntu1) ...
Removing qtdeclarative5-ubuntu-ui-extras-browser-plugin:i386 (0.23+14.04.20140422-0ubuntu1) ...
Removing qtdeclarative5-ubuntu-ui-toolkit-plugin:i386 (0.1.46+14.04.20140408.1-0ubuntu1) ...
Removing qtdeclarative5-unity-action-plugin:i386 (1.1.0+14.04.20140304-0ubuntu1) ...
Removing libunity-action-qt1:i386 (1.1.0+14.04.20140304-0ubuntu1) ...
Removing libhud2:i386 (13.10.1+14.04.20140402-0ubuntu1) ...
Removing liboxideqt-qmlplugin:i386 (1.0.0~bzr501-0ubuntu2) ...
Removing liboxideqtcore0:i386 (1.0.0~bzr501-0ubuntu2) ...
Removing libqt4-network:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqtdbus4:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libqt4-xml:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing qtdeclarative5-dialogs-plugin:i386 (5.2.1-3ubuntu15) ...
Removing qtdeclarative5-privatewidgets-plugin:i386 (5.2.1-3ubuntu15) ...
Removing libsignon-qt5-1 (8.56+14.04.20140307-0ubuntu2) ...
Removing qtdeclarative5-qtfeedback-plugin:i386 (5.0~git20130529-0ubuntu3) ...
Removing libqt5feedback5:i386 (5.0~git20130529-0ubuntu3) ...
Removing libqt5webkit5-qmlwebkitplugin:i386 (5.1.1-1ubuntu8) ...
Removing libqt5webkit5:i386 (5.1.1-1ubuntu8) ...
Removing libqt5multimedia5:i386 (5.2.1-0ubuntu5) ...
Removing qtdeclarative5-window-plugin:i386 (5.2.1-3ubuntu15) ...
Removing libqt5opengl5:i386 (5.2.1+dfsg-1ubuntu14) ...
Removing libqt5organizer5:i386 (5.0~git20140203~e0c5eebe-0ubuntu2) ...
Removing libqt5positioning5:i386 (5.2.1-1ubuntu2) ...
Removing libqt5printsupport5:i386 (5.2.1+dfsg-1ubuntu14) ...
Removing libqt5qml-graphicaleffects:i386 (5.2.1-1) ...
Removing qtdeclarative5-qtquick2-plugin:i386 (5.2.1-3ubuntu15) ...
Removing libqt5sensors5:i386 (5.2.1+dfsg-2ubuntu2) ...
Removing libqt5sql5-sqlite:i386 (5.2.1+dfsg-1ubuntu14) ...
Removing libqt5sql5:i386 (5.2.1+dfsg-1ubuntu14) ...
Removing libqt5svg5:i386 (5.2.1-1) ...
Removing libqt5xml5:i386 (5.2.1+dfsg-1ubuntu14) ...
Removing libqtcore4:i386 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing libthumbnailer0:i386 (1.1+14.04.20140401.1-0ubuntu1) ...
Removing qtcore4-l10n (4:4.8.5+git192-g085f851+dfsg-2ubuntu4) ...
Removing qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets (0.23+14.04.20140422-0ubuntu1) ...
Removing ubuntu-ui-toolkit-theme (0.1.46+14.04.20140408.1-0ubuntu1) ...
Removing libqt5widgets5:i386 (5.2.1+dfsg-1ubuntu14) ...
Removing libqt5quick5:i386 (5.2.1-3ubuntu15) ...
Removing libqt5qml5:i386 (5.2.1-3ubuntu15) ...
Removing libqt5gui5:i386 (5.2.1+dfsg-1ubuntu14) ...
Removing libqt5network5:i386 (5.2.1+dfsg-1ubuntu14) ...
Removing libxcb-randr0:i386 (1.10-2ubuntu1) ...
Removing libxcb-render-util0:i386 (0.3.8-1.1ubuntu1) ...
Removing libxcb-xkb1:i386 (1.10-2ubuntu1) ...
Removing libqt5dbus5:i386 (5.2.1+dfsg-1ubuntu14) ...
Removing libqt5core5a:i386 (5.2.1+dfsg-1ubuntu14) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for libglib2.0-0:i386 (2.40.0-2) ...
Processing triggers for initramfs-tools (0.103ubuntu4) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-24-generic
Log ended: 2014-05-05  09:52:19
```

Time for another reboot.

---

### Post by kansasnoob on 2014-05-05
Seems to work fine and missing recommends are not a concern:

[ATTACH=CONFIG]252889[/ATTACH]

I'll try to write up a conclusion later.

---

### Post by kansasnoob on 2014-05-06
Still playing. **[COLOR="#FF0000"]DO NOT even consider using the "^" to remove a DE[/COLOR]**, I ran "apt-get remove unbuntu-desktop^" and it litterally wants to remove even the kernel and other key components of the Ubuntu base:

```
Reading package lists...
Building dependency tree...
Reading state information...
Package 'oxideqt-codecs' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  gcc-4.9-base:i386 iw:i386 libc6:i386 libgcc1:i386 libnl-3-200:i386
  libnl-genl-3-200:i386 libssl1.0.0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gcc-4.9-base:i386 iw:i386 libc6:i386 libgcc1:i386 libnl-3-200:i386
  libnl-genl-3-200:i386
Suggested packages:
  glibc-doc:i386 locales:i386
The following packages will be REMOVED:
  account-plugin-aim account-plugin-facebook account-plugin-flickr
  account-plugin-google account-plugin-jabber account-plugin-salut
  account-plugin-twitter account-plugin-windows-live account-plugin-yahoo acl
  acpi-support acpid activity-log-manager activity-log-manager-control-center
  adium-theme-ubuntu aisleriot alsa-base alsa-utils anacron apg
  app-install-data app-install-data-partner appmenu-qt appmenu-qt5 apport
  apport-gtk apport-symptoms apt-xapian-index aptdaemon aptdaemon-data apturl
  apturl-common argyll aspell aspell-en at-spi2-core avahi-autoipd
  avahi-daemon avahi-utils bamfdaemon baobab bc binutils bluez bluez-alsa
  bluez-cups branding-ubuntu brasero brasero-cdrkit brasero-common brltty
  checkbox-gui checkbox-ng checkbox-ng-service cheese cheese-common colord
  compiz compiz-core compiz-gnome compiz-plugins-default cpp cpp-4.8
  cracklib-runtime crda cups cups-browsed cups-bsd cups-client cups-common
  cups-core-drivers cups-daemon cups-filters cups-filters-core-drivers
  cups-pk-helper cups-ppdc cups-server-common dbus-x11 dc dconf-cli
  dconf-editor dconf-gsettings-backend dconf-service deja-dup
  deja-dup-backend-cloudfiles deja-dup-backend-gvfs deja-dup-backend-s3
  desktop-file-utils dialog dictionaries-common diffstat dmz-cursor-theme
  dnsmasq-base doc-base duplicity dvd+rw-tools empathy empathy-common enchant
  eog espeak-data ethtool evince evince-common evolution evolution-common
  evolution-data-server evolution-data-server-common
  evolution-data-server-online-accounts evolution-indicator evolution-plugins
  example-content file-roller firefox flashplugin-installer folks-common
  fontconfig fontconfig-config fonts-cantarell fonts-dejavu-core fonts-droid
  fonts-freefont-ttf fonts-kacst fonts-kacst-one fonts-khmeros-core fonts-lao
  fonts-liberation fonts-lklug-sinhala fonts-nanum fonts-opensymbol
  fonts-sil-abyssinica fonts-sil-padauk fonts-takao-pgothic fonts-thai-tlwg
  fonts-tibetan-machine fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma
  fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee
  fonts-tlwg-typewriter fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush
  fonts-tlwg-waree foomatic-db-compressed-ppds friends friends-dispatcher
  friends-facebook friends-twitter gcc gcc-4.8 gconf-service
  gconf-service-backend gconf2 gconf2-common gcr gdb gdisk gdm gedit
  gedit-common genisoimage geoclue geoclue-ubuntu-geoip gettext ghostscript
  ghostscript-x gir1.2-accounts-1.0 gir1.2-appindicator3-0.1 gir1.2-atk-1.0
  gir1.2-atspi-2.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-ebook-1.2
  gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2 gir1.2-evince-3.0
  gir1.2-freedesktop gir1.2-gcr-3 gir1.2-gdata-0.0 gir1.2-gdkpixbuf-2.0
  gir1.2-gdm-1.0 gir1.2-gkbd-3.0 gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0
  gir1.2-gnomedesktop-3.0 gir1.2-gnomekeyring-1.0 gir1.2-goa-1.0
  gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gir1.2-gtk-3.0
  gir1.2-gtkclutter-1.0 gir1.2-gtksource-3.0 gir1.2-gtop-2.0 gir1.2-gudev-1.0
  gir1.2-ibus-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-json-1.0
  gir1.2-messagingmenu-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0
  gir1.2-nmgtk-1.0 gir1.2-notify-0.7 gir1.2-packagekitglib-1.0
  gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-polkit-1.0 gir1.2-rb-3.0
  gir1.2-rest-0.7 gir1.2-secret-1 gir1.2-signon-1.0 gir1.2-soup-2.4
  gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-totem-1.0
  gir1.2-totem-plparser-1.0 gir1.2-tracker-0.16 gir1.2-udisks-2.0
  gir1.2-unity-5.0 gir1.2-upowerglib-1.0 gir1.2-vte-2.90 gir1.2-webkit-3.0
  gir1.2-wnck-3.0 gir1.2-xkl-1.0 gir1.2-zpj-0.0 gjs gkbd-capplet
  glib-networking glib-networking-common glib-networking-services
  gnome-accessibility-themes gnome-bluetooth gnome-calculator
  gnome-color-manager gnome-contacts gnome-control-center
  gnome-control-center-shared-data gnome-desktop3-data gnome-disk-utility
  gnome-documents gnome-font-viewer gnome-icon-theme gnome-icon-theme-extras
  gnome-icon-theme-full gnome-icon-theme-symbolic gnome-keyring gnome-mahjongg
  gnome-menus gnome-mines gnome-online-accounts gnome-online-miners gnome-orca
  gnome-power-manager gnome-screensaver gnome-screenshot gnome-session
  gnome-session-bin gnome-session-canberra gnome-session-common
  gnome-settings-daemon gnome-settings-daemon-schemas gnome-shell
  gnome-shell-common gnome-shell-extensions gnome-sudoku gnome-sushi
  gnome-system-log gnome-system-monitor gnome-terminal gnome-terminal-data
  gnome-themes-standard gnome-tweak-tool gnome-user-guide gnome-user-share
  gnome-video-effects gnomine grilo-plugins-0.2 growisofs grub-common
  grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common
  gsettings-desktop-schemas gsettings-ubuntu-schemas gsfonts
  gstreamer0.10-alsa gstreamer0.10-fluendo-mp3 gstreamer0.10-nice
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly gstreamer0.10-pulseaudio gstreamer0.10-tools
  gstreamer0.10-x gstreamer1.0-alsa gstreamer1.0-clutter
  gstreamer1.0-fluendo-mp3 gstreamer1.0-libav gstreamer1.0-nice
  gstreamer1.0-plugins-bad gstreamer1.0-plugins-bad-faad
  gstreamer1.0-plugins-bad-videoparsers gstreamer1.0-plugins-base
  gstreamer1.0-plugins-base-apps gstreamer1.0-plugins-good
  gstreamer1.0-plugins-ugly gstreamer1.0-pulseaudio gstreamer1.0-tools
  gstreamer1.0-x gtk2-engines-murrine gtk2-engines-pixbuf gtk3-engines-unico
  gucharmap guile-2.0-libs gvfs gvfs-backends gvfs-backends-goa gvfs-bin
  gvfs-common gvfs-daemons gvfs-fuse gvfs-libs hardening-includes
  hicolor-icon-theme hplip hplip-data hud humanity-icon-theme hunspell-en-us
  hwdata hyphen-en-us ibus ibus-gtk ibus-gtk3 ibus-pinyin ibus-table im-config
  indicator-application indicator-appmenu indicator-bluetooth
  indicator-datetime indicator-keyboard indicator-messages indicator-power
  indicator-printers indicator-session indicator-sound inputattach
  intel-gpu-tools intltool-debian iproute iputils-arping itstool iw
  kerneloops-daemon landscape-client-ui-install language-selector-gnome
  laptop-detect libaa1 libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth
  libaccount-plugin-google libaccounts-glib0 libaccounts-qt5-1
  libappindicator3-1 libapt-pkg-perl libarchive-zip-perl libarchive13
  libart-2.0-2 libasan0 libasound2 libasound2-data libasound2-plugins
  libaspell15 libasprintf-dev libass4 libassuan0 libasyncns0 libatasmart4
  libatk-adaptor libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatkmm-1.6-1
  libatomic1 libatspi2.0-0 libaudio2 libauthen-sasl-perl libautodie-perl
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core7
  libavahi-glib1 libavahi-gobject0 libavc1394-0 libavcodec54 libavformat54
  libbamf3-2 libbluetooth3 libboost-date-time1.54.0 libboost-system1.54.0
  libbrasero-media3-1 libbrlapi0.6 libburn4 libc-dev-bin libc6-dbg libc6-dev
  libcaca0 libcairo-gobject2 libcairo-perl libcairo2 libcairomm-1.0-1
  libcamel-1.2-45 libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0
  libcanberra-gtk3-module libcanberra-pulse libcanberra0 libcaribou0
  libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdparanoia0 libcdr-0.0-0
  libcheese-gtk23 libcheese7 libchromaprint0 libclass-accessor-perl
  libclone-perl libcloog-isl4 libclucene-contribs1 libclucene-core1
  libclutter-1.0-0 libclutter-1.0-common libclutter-gst-2.0-0
  libclutter-gtk-1.0-0 libcmis-0.4-4 libcogl-common libcogl-pango15 libcogl15
  libcolamd2.8.0 libcolord-gtk1 libcolord1 libcolorhug1 libcolumbus1
  libcolumbus1-common libcompizconfig0 libcrack2 libcroco3
  libcrypt-passwdmd5-perl libcups2 libcupscgi1 libcupsfilters1 libcupsimage2
  libcupsmime1 libcupsppdc1 libcurl3 libdaemon0 libdatrie1 libdbusmenu-glib4
  libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdbusmenu-qt2 libdbusmenu-qt5
  libdc1394-22 libdconf1 libdecoration0 libdee-1.0-4 libdigest-hmac-perl
  libdjvulibre-text libdjvulibre21 libdmapsharing-3.0-2 libdotconf0
  libdpkg-perl libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdv4
  libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16
  libedata-book-1.2-20 libedata-cal-1.2-23 libedataserver-1.2-18 libegl1-mesa
  libegl1-mesa-drivers libelfg0 libemail-valid-perl libenchant1c2a libespeak1
  libevdocument3-4 libevent-2.0-5 libevolution libevview3-3 libexempi3
  libexif12 libexiv2-12 libexttextcat-2.0-0 libexttextcat-data
  libfarstream-0.1-0 libfarstream-0.2-2 libfftw3-double3 libfftw3-single3
  libfile-basedir-perl libfile-copy-recursive-perl libfile-desktopentry-perl
  libfile-fcntllock-perl libfile-listing-perl libfile-mimeinfo-perl libflac8
  libflite1 libfluidsynth1 libfolks-eds25 libfolks-telepathy25 libfolks25
  libfontconfig1 libfontembed1 libfontenc1 libframe6
  libfreerdp-plugins-standard libfreerdp1 libfreetype6 libfriends0 libfs6
  libgail-3-0 libgail-common libgail18 libgbm1 libgc1c2 libgcc-4.8-dev
  libgconf-2-4 libgcr-ui-3-1 libgd3 libgdata-common libgdata13
  libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgdm1 libgee-0.8-2 libgee2
  libgeis1 libgeoclue0 libgettextpo-dev libgettextpo0 libgexiv2-2 libgjs0e
  libgl1-mesa-dri libgl1-mesa-glx libglamor0 libglapi-mesa libgles2-mesa
  libglew1.10 libglewmx1.10 libglib2.0-bin libglibmm-2.4-1c2a libglu1-mesa
  libgmime-2.6-0 libgmp10 libgnome-bluetooth11 libgnome-control-center1
  libgnome-desktop-3-7 libgnome-keyring-common libgnome-keyring0
  libgnome-menu-3-0 libgnomekbd-common libgnomekbd8 libgoa-1.0-0b
  libgoa-1.0-common libgoa-backend-1.0-1 libgomp1 libgpgme11 libgphoto2-6
  libgphoto2-l10n libgphoto2-port10 libgpm2 libgpod-common libgpod4 libgrail6
  libgraphite2-3 libgrilo-0.2-1 libgrip0 libgs9 libgs9-common libgsettings-qt1
  libgssdp-1.0-3 libgstreamer-plugins-bad0.10-0 libgstreamer-plugins-bad1.0-0
  libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base1.0-0
  libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer1.0-0
  libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk2-perl libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libgtkglext1 libgtkhtml-4.0-0
  libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgtkmm-3.0-1
  libgtksourceview-3.0-1 libgtksourceview-3.0-common libgtop2-7
  libgtop2-common libgucharmap-2-90-7 libgudev-1.0-0 libgupnp-1.0-4
  libgupnp-av-1.0-2 libgupnp-igd-1.0-4 libgusb2 libgutenprint2 libgweather-3-6
  libgweather-common libgxps2 libharfbuzz-icu0 libharfbuzz0b libhpmud0
  libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tree-perl
  libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libhud2 libhunspell-1.3-0
  libhyphen0 libibus-1.0-5 libical1 libice6 libicu52 libido3-0.1-0
  libiec61883-0 libieee1284-3 libijs-0.35 libimobiledevice4 libindicator3-7
  libio-pty-perl libio-socket-inet6-perl libio-socket-ssl-perl
  libio-string-perl libipc-run-perl libipc-system-simple-perl libisl10
  libisofs6 libitm1 libiw30 libjack-jackd2-0 libjasper1
  libjavascriptcoregtk-3.0-0 libjbig0 libjbig2dec0 libjpeg-turbo8 libjpeg8
  libjson-glib-1.0-0 libjson-glib-1.0-common libjte1 libkpathsea6
  liblangtag-common liblangtag1 liblcms2-2 libldb1 liblightdm-gobject-1-0
  liblircclient0 liblist-moreutils-perl libllvm3.4 liblouis-data liblouis2
  libltdl7 liblua5.2-0 liblwp-protocol-https-perl liblzo2-2 libmail-spf-perl
  libmailtools-perl libmbim-glib0 libmeanwhile1 libmediaart-1.0-0
  libmessaging-menu0 libmetacity-private0a libmhash2 libminiupnpc8
  libmission-control-plugins0 libmm-glib0 libmnl0 libmozjs-24-0 libmpc3
  libmpfr4 libmspub-0.0-0 libmtdev1 libmtp-common libmtp-runtime libmtp9
  libmusicbrainz5-0 libmutter0c libmythes-1.2-0 libnatpmp1
  libnautilus-extension1a libneon27-gnutls libnet-dns-perl
  libnet-domain-tld-perl libnet-ip-perl libnet-libidn-perl
  libnet-smtp-ssl-perl libnet-ssleay-perl libnetfilter-conntrack3 libnettle4
  libnice10 libnl-3-200 libnl-genl-3-200 libnl-route-3-200 libnm-glib-vpn1
  libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin libnotify4
  libnspr4 libnspr4-0d libnss-mdns libnss3 libnss3-1d libnss3-nssdb libntdb1
  libnux-4.0-0 libnux-4.0-common liboauth0 libofa0 libogg0 libopencc1
  libopencv-calib3d2.4 libopencv-contrib2.4 libopencv-core2.4
  libopencv-features2d2.4 libopencv-flann2.4 libopencv-highgui2.4
  libopencv-imgproc2.4 libopencv-legacy2.4 libopencv-ml2.4
  libopencv-objdetect2.4 libopencv-video2.4 libopenobex1 libopenvg1-mesa
  liborc-0.4-0 liborcus-0.6-0 liboxideqt-qmlplugin liboxideqtcore0
  libp11-kit-gnome-keyring libpackagekit-glib2-16 libpam-gnome-keyring
  libpango-1.0-0 libpango-perl libpango1.0-0 libpangocairo-1.0-0
  libpangoft2-1.0-0 libpangomm-1.4-1 libpangox-1.0-0 libpangoxft-1.0-0
  libpaper-utils libpaper1 libparse-debianchangelog-perl libpciaccess0
  libpcsclite1 libpeas-1.0-0 libpeas-common libperl5.18 libperlio-gzip-perl
  libpixman-1-0 libplist1 libpocketsphinx1 libpolkit-agent-1-0
  libpolkit-backend-1-0 libpoppler-glib8 libpoppler44 libportaudio2
  libprotobuf8 libproxy1 libproxy1-plugin-gsettings
  libproxy1-plugin-networkmanager libpulse-mainloop-glib0 libpulse0
  libpulsedsp libpurple-bin libpurple0 libpwquality-common libpwquality1
  libpython-stdlib libpython2.7 libpython2.7-minimal libpython2.7-stdlib
  libpython3.4 libpyzy-1.0-0 libqmi-glib0 libqpdf13 libqt4-dbus
  libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl
  libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-sqlite libqt4-svg
  libqt4-test libqt4-xml libqt4-xmlpatterns libqt5core5a libqt5dbus5
  libqt5feedback5 libqt5gui5 libqt5multimedia5 libqt5network5 libqt5opengl5
  libqt5organizer5 libqt5positioning5 libqt5printsupport5
  libqt5qml-graphicaleffects libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5
  libqt5sql5-sqlite libqt5svg5 libqt5test5 libqt5webkit5
  libqt5webkit5-qmlwebkitplugin libqt5widgets5 libqt5xml5
  libqtassistantclient4 libqtcore4 libqtdbus4 libqtgui4 libqtwebkit4
  libquadmath0 libraptor2-0 librasqal3 libraw1394-11 libraw9 librdf0
  libreadline5 libreoffice-avmedia-backend-gstreamer libreoffice-base-core
  libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress
  libreoffice-math libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-presentation-minimizer libreoffice-style-human
  libreoffice-writer librest-0.7-0 librhythmbox-core8 librsvg2-2
  librsvg2-common librsync1 libsamplerate0 libsane libsane-common
  libsane-hpaio libsbc1 libschroedinger-1.0-0 libsecret-1-0 libsecret-common
  libsensors4 libsgutils2-2 libshout3 libsigc++-2.0-0c2a libsignon-extension1
  libsignon-glib1 libsignon-plugins-common1 libsignon-qt5-1 libslv2-9 libsm6
  libsmbclient libsndfile1 libsnmp-base libsnmp30 libsocket6-perl libsonic0
  libsoup-gnome2.4-1 libsoup2.4-1 libspandsp2 libspectre1 libspeechd2
  libspeex1 libspeexdsp1 libsphinxbase1 libspice-server1 libssh-4
  libstartup-notification0 libsub-identify-perl libsub-name-perl
  libsystemd-journal0 libt1-5 libtag1-vanilla libtag1c2a libtalloc2 libtcl8.6
  libtdb1 libtelepathy-farstream3 libtelepathy-glib0 libtelepathy-logger3
  libtevent0 libtext-levenshtein-perl libthai-data libthai0 libtheora0
  libthumbnailer0 libtiff5 libtimedate-perl libtimezonemap1 libtk8.6
  libtotem-plparser18 libtotem0 libtracker-extract-0.16-0
  libtracker-miner-0.16-0 libtracker-sparql-0.16-0 libtsan0 libtxc-dxtn-s2tc0
  libudisks2-0 libufe-xidgetter0 libunistring0 libunity-action-qt1
  libunity-control-center1 libunity-core-6.0-9 libunity-gtk2-parser0
  libunity-gtk3-parser0 libunity-misc4 libunity-protocol-private0
  libunity-scopes-json-def-desktop libunity-webapps0 libunity9 libunityvoice1
  libupower-glib1 libupstart1 liburi-perl liburl-dispatcher1 libusbmuxd2
  libutempter0 libuuid-perl libv4l-0 libv4lconvert0 libvisio-0.0-0
  libvisual-0.4-0 libvisual-0.4-plugins libvncserver0 libvorbis0a
  libvorbisenc2 libvorbisfile3 libvpx1 libvte-2.90-9 libvte-2.90-common
  libwacom-common libwacom2 libwavpack1 libwayland-client0 libwayland-cursor0
  libwayland-egl1-mesa libwayland-server0 libwbclient0 libwebkitgtk-3.0-0
  libwebkitgtk-3.0-common libwebp5 libwebpmux1 libwhoopsie-preferences0
  libwhoopsie0 libwmf0.2-7 libwmf0.2-7-gtk libwnck-3-0 libwnck-3-common
  libwnck-common libwnck22 libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwrap0
  libwww-perl libwww-robotrules-perl libx11-xcb1 libx86-1 libxapian22
  libxatracker2 libxaw7 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-icccm4
  libxcb-image0 libxcb-present0 libxcb-randr0 libxcb-render-util0
  libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-sync1 libxcb-util0
  libxcb-xfixes0 libxcb-xkb1 libxcomposite1 libxcursor1 libxdamage1 libxfixes3
  libxfont1 libxft2 libxi6 libxinerama1 libxkbcommon0 libxkbfile1
  libxklavier16 libxmu6 libxp6 libxpm4 libxrandr2 libxrender1 libxres1
  libxshmfence1 libxslt1.1 libxss1 libxt6 libxtst6 libxv1 libxvmc1
  libxxf86dga1 libxxf86vm1 libyajl2 libyaml-tiny-perl libyelp0
  libzapojit-0.0-0 libzbar0 libzeitgeist-1.0-1 libzeitgeist-2.0-0 libzephyr4
  light-themes lightdm lintian linux-generic
  linux-image-extra-3.13.0-24-generic linux-image-generic linux-libc-dev
  linux-sound-base lp-solve make manpages-dev mcp-account-manager-goa
  mcp-account-manager-uoa media-player-info memtest86+ metacity-common
  mobile-broadband-provider-info modemmanager mousetweaks mscompress mtools
  mutter mutter-common myspell-en-au myspell-en-gb myspell-en-za mythes-en-us
  nautilus nautilus-data nautilus-sendto nautilus-sendto-empathy
  nautilus-share network-manager network-manager-gnome network-manager-pptp
  network-manager-pptp-gnome notification-daemon notify-osd notify-osd-icons
  nux-tools obex-data-server obexd-client onboard onboard-data oneconf
  oneconf-common openoffice.org-hyphenation openprinting-ppds
  overlay-scrollbar overlay-scrollbar-gtk2 overlay-scrollbar-gtk3 p11-kit
  p11-kit-modules patch patchutils pcmciautils pkg-config
  plainbox-provider-checkbox plainbox-provider-resource-generic
  plainbox-secure-policy plymouth-label plymouth-theme-ubuntu-gnome-logo
  plymouth-theme-ubuntu-logo pm-utils policykit-1 policykit-1-gnome
  policykit-desktop-privileges poppler-data poppler-utils pptp-linux
  printer-driver-c2esp printer-driver-foo2zjs printer-driver-foo2zjs-common
  printer-driver-gutenprint printer-driver-hpcups printer-driver-min12xxw
  printer-driver-pnm2ppa printer-driver-postscript-hp printer-driver-ptouch
  printer-driver-pxljr printer-driver-sag-gdi printer-driver-splix pulseaudio
  pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils python
  python-apt python-aptdaemon python-aptdaemon.gtk3widgets python-boto
  python-cairo python-chardet python-cloudfiles python-commandnotfound
  python-crypto python-cups python-cupshelpers python-dbus python-dbus-dev
  python-debian python-debtagshw python-defer python-dirspec python-gconf
  python-gdbm python-gi python-gi-cairo python-gnomekeyring python-gobject
  python-gobject-2 python-gtk2 python-httplib2 python-ibus python-imaging
  python-ldb python-libxml2 python-lockfile python-lxml python-minimal
  python-notify python-ntdb python-oauthlib python-oneconf python-openssl
  python-pam python-pexpect python-pil python-piston-mini-client
  python-pkg-resources python-pycurl python-qt4 python-qt4-dbus
  python-renderpm python-reportlab python-reportlab-accel python-requests
  python-samba python-serial python-sip python-six python-smbc python-talloc
  python-tdb python-twisted-bin python-twisted-core python-twisted-web
  python-ubuntu-sso-client python-urllib3 python-xapian python-xdg
  python-zeitgeist python-zope.interface python2.7 python2.7-minimal
  python3-apport python3-aptdaemon python3-aptdaemon.gtk3widgets
  python3-aptdaemon.pkcompat python3-brlapi python3-cairo python3-chardet
  python3-checkbox-ng python3-checkbox-support python3-crypto python3-debian
  python3-defer python3-feedparser python3-gi-cairo python3-httplib2
  python3-louis python3-lxml python3-mako python3-markupsafe python3-oauthlib
  python3-oneconf python3-piston-mini-client python3-pkg-resources
  python3-plainbox python3-problem-report python3-pyatspi python3-pycurl
  python3-pyparsing python3-requests python3-six python3-software-properties
  python3-speechd python3-uno python3-urllib3 python3-xdg python3-xkit qdbus
  qpdf qt-at-spi qtchooser qtcore4-l10n qtdeclarative5-accounts-plugin
  qtdeclarative5-dialogs-plugin qtdeclarative5-localstorage-plugin
  qtdeclarative5-privatewidgets-plugin qtdeclarative5-qtfeedback-plugin
  qtdeclarative5-qtquick2-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-unity-action-plugin
  qtdeclarative5-window-plugin remmina remmina-common remmina-plugin-rdp
  remmina-plugin-vnc rfkill rhythmbox rhythmbox-data rhythmbox-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins rtkit sa-compile samba-common
  samba-common-bin samba-libs sane-utils seahorse session-migration
  sessioninstaller shotwell shotwell-common signon-keyring-extension
  signon-plugin-oauth2 signon-plugin-password signon-ui signond simple-scan
  smbclient sni-qt software-center software-center-aptdaemon-plugins
  software-properties-common software-properties-gtk sound-theme-freedesktop
  spamassassin speech-dispatcher speech-dispatcher-audio-plugins
  sphinx-voxforge-hmm-en sphinx-voxforge-lm-en ssh-askpass-gnome ssl-cert
  synaptic syslinux syslinux-common syslinux-legacy
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev t1utils tcl tcl8.6 tcpd telepathy-gabble
  telepathy-haze telepathy-idle telepathy-indicator telepathy-logger
  telepathy-mission-control-5 telepathy-salut thunderbird
  thunderbird-gnome-support thunderbird-locale-en thunderbird-locale-en-us tk
  tk8.6 toshset totem totem-common totem-mozilla totem-plugins tracker
  tracker-extract tracker-miner-fs tracker-utils transmission-common
  transmission-gtk ttf-indic-fonts-core ttf-punjabi-fonts
  ttf-ubuntu-font-family ubuntu-artwork ubuntu-desktop ubuntu-docs
  ubuntu-drivers-common ubuntu-extras-keyring ubuntu-gnome-default-settings
  ubuntu-gnome-desktop ubuntu-mono ubuntu-release-upgrader-gtk ubuntu-session
  ubuntu-settings ubuntu-sounds ubuntu-sso-client ubuntu-sso-client-qt
  ubuntu-system-service ubuntu-ui-toolkit-theme ubuntu-wallpapers
  ubuntu-wallpapers-trusty ubuntuone-client-data udisks2 unattended-upgrades
  unity unity-asset-pool unity-control-center unity-control-center-signon
  unity-greeter unity-gtk-module-common unity-gtk2-module unity-gtk3-module
  unity-lens-applications unity-lens-files unity-lens-friends unity-lens-music
  unity-lens-photos unity-lens-video unity-scope-audacious
  unity-scope-calculator unity-scope-chromiumbookmarks unity-scope-clementine
  unity-scope-colourlovers unity-scope-devhelp unity-scope-firefoxbookmarks
  unity-scope-gdrive unity-scope-gmusicbrowser unity-scope-gourmet
  unity-scope-guayadeque unity-scope-home unity-scope-manpages
  unity-scope-musicstores unity-scope-musique unity-scope-openclipart
  unity-scope-texdoc unity-scope-tomboy unity-scope-video-remote
  unity-scope-virtualbox unity-scope-yelp unity-scope-zotero
  unity-scopes-master-default unity-scopes-runner unity-services
  unity-settings-daemon unity-voice-service unity-webapps-common
  unity-webapps-qml unity-webapps-service uno-libs3 unoconv unzip update-inetd
  update-manager update-notifier update-notifier-common upower ure
  usb-creator-common usb-creator-gtk usb-modeswitch usb-modeswitch-data
  usbmuxd vbetool vino wamerican wbritish webaccounts-extension-common
  webapp-container webbrowser-app whoopsie whoopsie-preferences wireless-regdb
  wireless-tools wodim wpasupplicant x11-apps x11-common x11-session-utils
  x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils xbitmaps
  xcursor-themes xdg-user-dirs xdg-user-dirs-gtk xdg-utils xdiagnose
  xfonts-base xfonts-encodings xfonts-mathml xfonts-scalable xfonts-utils
  xinit xinput xorg xorg-docs-core xserver-common xserver-xephyr xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-glamoregl xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware xsltproc xterm
  xul-ext-ubufox xul-ext-unity xul-ext-webaccounts
  xul-ext-websites-integration xz-utils yelp yelp-tools yelp-xsl zeitgeist
  zeitgeist-core zeitgeist-datahub zenity zenity-common zip
The following NEW packages will be installed:
  gcc-4.9-base:i386 iw:i386 libc6:i386 libgcc1:i386 libnl-3-200:i386
  libnl-genl-3-200:i386
0 upgraded, 6 newly installed, 1512 to remove and 0 not upgraded.
Need to get 4,186 kB of archives.
After this operation, 2,492 MB disk space will be freed.
Do you want to continue? [Y/n] N
Abort.
```

---

### Post by kansasnoob on 2014-05-06
This will be relevant when I sum up my conclusions:

```
lance@lance-desktop:~$ **[COLOR="#FF0000"]sudo apt-get install gnome-shell-extensions[/COLOR]** --assume-no
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0
  gir1.2-gnomedesktop-3.0 gir1.2-gtop-2.0 gir1.2-json-1.0 gir1.2-mutter-3.0
  gir1.2-nmgtk-1.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12
  gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs
  gnome-control-center gnome-control-center-data gnome-icon-theme-full
  gnome-session gnome-settings-daemon gnome-shell gnome-shell-common
  gnome-themes-standard gnome-themes-standard-data gnome-tweak-tool
  gtk2-engines-pixbuf libcaribou-common libcaribou0 libgdm1 libgjs0e
  libgoa-backend-1.0-1 libmozjs-24-0 libmutter0c libxcb-keysyms1
  libxcb-xf86dri0 libxcb-xv0 mutter-common xserver-xephyr
Suggested packages:
  desktop-base
[B]The following NEW packages will be installed:
  gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0
  gir1.2-gnomedesktop-3.0 gir1.2-gtop-2.0 gir1.2-json-1.0 gir1.2-mutter-3.0
  gir1.2-nmgtk-1.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12
  gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs
  gnome-control-center gnome-control-center-data gnome-icon-theme-full
  [COLOR="#FF0000"]gnome-session[/COLOR] gnome-settings-daemon **[COLOR="#FF0000"]gnome-shell[/COLOR]** gnome-shell-common
  gnome-shell-extensions gnome-themes-standard gnome-themes-standard-data
  gnome-tweak-tool gtk2-engines-pixbuf libcaribou-common libcaribou0 libgdm1
  libgjs0e libgoa-backend-1.0-1 libmozjs-24-0 libmutter0c libxcb-keysyms1
  libxcb-xf86dri0 libxcb-xv0 mutter-common xserver-xephyr
0 upgraded, 46 newly installed, 0 to remove and 3 not upgraded.
Need to get 20.6 MB of archives.
[COLOR="#FF0000"]After this operation, 65.0 MB of additional disk space will be used[/COLOR].[/B]
Do you want to continue? [Y/n] N
Abort.

```

---

### Post by kansasnoob on 2014-05-07
I'll discuss the situation with Ubuntu GNOME dev but I think 'mutter' and 'gnome-session' should be added as hard depends of 'gnome-shell'. Basically I'm considering the feasability of an Ubuntu/Unity user installing "gnome-shell" and/or "gnome-shell-extensions" in order to allow a second user to use GNOME Shell or GNOME Classic.

---

### Post by kansasnoob on 2014-05-07
Hopefully this gives me GNOME Shell with no extensions and no GNOME Classic:

```
lance@lance-desktop:~$ sudo apt-get install gnome-shell gnome-session mutter
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0
  gir1.2-gnomedesktop-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-nmgtk-1.0
  gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs gnome-control-center
  gnome-control-center-data gnome-icon-theme-full gnome-settings-daemon
  gnome-shell-common gnome-themes-standard gnome-themes-standard-data
  gtk2-engines-pixbuf libcaribou-common libcaribou0 libgdm1 libgjs0e
  libgoa-backend-1.0-1 libmozjs-24-0 libmutter0c libxcb-keysyms1
  libxcb-xf86dri0 libxcb-xv0 mutter-common xserver-xephyr
Suggested packages:
  desktop-base
The following NEW packages will be installed:
  gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0
  gir1.2-gnomedesktop-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-nmgtk-1.0
  gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs gnome-control-center
  gnome-control-center-data gnome-icon-theme-full gnome-session
  gnome-settings-daemon gnome-shell gnome-shell-common gnome-themes-standard
  gnome-themes-standard-data gtk2-engines-pixbuf libcaribou-common libcaribou0
  libgdm1 libgjs0e libgoa-backend-1.0-1 libmozjs-24-0 libmutter0c
  libxcb-keysyms1 libxcb-xf86dri0 libxcb-xv0 mutter mutter-common
  xserver-xephyr
0 upgraded, 44 newly installed, 0 to remove and 33 not upgraded.
Need to get 20.3 MB of archives.
After this operation, 63.0 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

Yes, that provides only the login options Ubuntu and GNOME, but I should have included 'gnome-tweak-tool':

```
lance@lance-desktop:~$ sudo apt-get install gnome-tweak-tool
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gnome-tweak-tool
0 upgraded, 1 newly installed, 0 to remove and 33 not upgraded.
Need to get 120 kB of archives.
After this operation, 980 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/universe gnome-tweak-tool all 3.10.1-2ubuntu1 [120 kB]
Fetched 120 kB in 0s (289 kB/s)          
Selecting previously unselected package gnome-tweak-tool.
(Reading database ... 171757 files and directories currently installed.)
Preparing to unpack .../gnome-tweak-tool_3.10.1-2ubuntu1_all.deb ...
Unpacking gnome-tweak-tool (3.10.1-2ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Setting up gnome-tweak-tool (3.10.1-2ubuntu1) ...

```

As expected no extensions are installed:

[ATTACH=CONFIG]252961[/ATTACH]

I also suspect that most users would want some additional themes ;)

Adding 'gnome-shell-extensions' to that adds very little and also provides the GNOME Classic session:

```
lance@lance-desktop:~$ sudo apt-get install gnome-shell-extensions
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gir1.2-gtop-2.0
The following NEW packages will be installed:
  gir1.2-gtop-2.0 gnome-shell-extensions
0 upgraded, 2 newly installed, 0 to remove and 33 not upgraded.
Need to get 131 kB of archives.
After this operation, 1,319 kB of additional disk space will be used.

```

---

### Post by kansasnoob on 2014-05-08
General conclusions regarding the initial request:

#1: Running "sudo apt-get remove ubuntu-default-settings ubuntu-desktop" tells me; "Virtual packages like 'ubuntu-default-settings' can't be removed". Reversing the order of removal makes no difference.

#2: The only difference between running "sudo apt-get install ubuntu-gnome-desktop^" and "sudo apt-get install ubuntu-gnome-desktop" is that including the "^" installs 'notification-daemon', but I think that's an important package to install.

#3: Having removed 'ubuntu-desktop' and then running "sudo apt-get autoremove" shows; 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Not part of the original request but I considered what would happen if the root user/owner runs Unity and wants to add a new user with the ability to run either GNOME Shell or GNOME Classic, and;

Installing only 'gnome-shell' fails to install 'gnome-session', 'mutter', and 'gnome-tweak-tool'.

Installing only 'gnome-shell-extensions' pulls in 'gnome-shell', 'gnome-session', and 'gnome-tweak-tool' but not 'mutter'.

So we may want to consider tweaking the dependencies for both 'gnome-shell' and 'gnome-shell-extensions'.

---

### Post by kansasnoob on 2014-05-08
OK, it is possible to convert Ubuntu Trusty into pure Ubuntu GNOME Trusty following the steps below, but consider the following first!

I'm personally NOT a fan of removing default packages from an OS, installing alternatives is cool as long as you exercise some common sense but I see no point in removing unused packages. You'll notice in [my Flashback w/Metacity notes]("http://ubuntuforums.org/showthread.php?t=2220264") that I do NOT recommend removing any packages.

If my PC is intended to be used only by me I prefer a fresh install of the OS of my choosing, but take the case of Jack & Jill; Jack installs Ubuntu on a PC he shares with Jill because he prefers the Unity DE but Jill prefers GNOME Shell - no problem - simply install 'gnome-shell-extensions' and 'mutter' which pull in the proper dependencies, then add Jill as a new user and she can choose to boot either GNOME or GNOME Classic at login.

But, if I've not dissuaded you, here's what I found to work (just because it worked for me **I can't guarantee that it'll work for you**):

**Step #1**: Go to System Settings > User Accounts, unlock, select Automatic Login = Off, and lock again!

**Step #2**: Use [ppa-purge]("http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html") for each PPA to restore package versions to their defaults. This is particularly important as regards the various gnome3 & ricotz ppa's but configuration of other non-native packages may also be effected.

**Step #3**: Install the Ubuntu GNOME meta-package:

```
sudo apt-get install ubuntu-gnome-desktop^
```

**Note**: The **[COLOR="#FF0000"]^[/COLOR]** is NOT a typo! It's useful for resolving dependencies and recommended packages, but [B][COLOR="#FF0000"]it should never be used when removing packages!
[/COLOR][/B]
**Important note**: 'gdm' must be selected as the default display manager when prompted (just use the arrow keys to select gdm, then use the Tab key to select OK):

[ATTACH=CONFIG]252985[/ATTACH]

**Step #4**: Reboot and select GNOME or GNOME Classic at login.

**Step #5**: Remove all of the default Ubuntu components, but be aware that this also removes default apps such as Thunderbird (Ubuntu GNOME uses Evolution). The command is quite long so be sure to just copy-n-paste:

```
sudo apt-get remove account-plugin-facebook account-plugin-flickr account-plugin-google account-plugin-twitter activity-log-manager activity-log-manager-control-center adium-theme-ubuntu appmenu-qt appmenu-qt5 bamfdaemon branding-ubuntu checkbox-gui checkbox-ng checkbox-ng-service compiz compiz-core compiz-gnome compiz-plugins-default dmz-cursor-theme doc-base ethtool example-content friends friends-dispatcher friends-facebook friends-twitter geoclue-ubuntu-geoip gir1.2-accounts-1.0 gir1.2-appindicator3-0.1 gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2 gir1.2-messagingmenu-1.0 gir1.2-signon-1.0 gnome-power-manager gnome-screensaver gnomine gsettings-ubuntu-schemas gstreamer0.10-plugins-base-apps gstreamer0.10-tools gstreamer1.0-plugins-base-apps gstreamer1.0-tools gtk2-engines-murrine gtk3-engines-unico hud indicator-applet indicator-appmenu indicator-bluetooth indicator-datetime indicator-keyboard indicator-messages indicator-power indicator-printers indicator-session indicator-sound landscape-client-ui-install language-selector-gnome libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-qt5-1 libaudio2 libbamf3-2 libcolumbus1 libcolumbus1-common libcompizconfig0 libdbusmenu-qt2 libdbusmenu-qt5 libdecoration0 libfreerdp-plugins-standard libfreerdp1 libfriends0 libgee2 libglew1.10 libglewmx1.10 libgsettings-qt1 libhud2 liblightdm-gobject-1-0 libmetacity-private0a libmysqlclient18 libnux-4.0-0 libnux-4.0-common liboxideqt-qmlplugin liboxideqtcore0 libpanel-applet-4-0 libpocketsphinx1 libprotobuf8 libqt4-dbus libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns libqt5core5a libqt5dbus5 libqt5feedback5 libqt5gui5 libqt5multimedia5 libqt5network5 libqt5opengl5 libqt5organizer5 libqt5positioning5 libqt5printsupport5 libqt5qml-graphicaleffects libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5svg5 libqt5test5 libqt5webkit5 libqt5webkit5-qmlwebkitplugin libqt5widgets5 libqt5xml5 libqtassistantclient4 libqtcore4 libqtdbus4 libqtgui4 libqtwebkit4 libreoffice-style-human libsignon-extension1 libsignon-plugins-common1 libsignon-qt5-1 libsphinxbase1 libssh-4 libthumbnailer0 libtimezonemap1 libufe-xidgetter0 libunity-action-qt1 libunity-core-6.0-9 libunity-gtk2-parser0 libunity-gtk3-parser0 libunity-misc4 libunity-webapps0 libunityvoice1 libupstart1 liburl-dispatcher1 libuuid-perl libvncserver0 libwhoopsie-preferences0 libwnck-common libwnck22 libx86-1 libxcb-randr0 libxcb-render-util0 libxcb-xkb1 libyaml-tiny-perl light-themes lightdm metacity-common mysql-common notify-osd notify-osd-icons nux-tools onboard onboard-data overlay-scrollbar overlay-scrollbar-gtk2 overlay-scrollbar-gtk3 pkg-config plainbox-provider-checkbox plainbox-provider-resource-generic plainbox-secure-policy plymouth-theme-ubuntu-logo pm-utils python-gconf python-qt4 python-qt4-dbus python-sip python3-checkbox-ng python3-checkbox-support python3-feedparser python3-lxml python3-plainbox python3-pyparsing python3-requests python3-urllib3 qdbus qt-at-spi qtchooser qtcore4-l10n qtdeclarative5-accounts-plugin qtdeclarative5-dialogs-plugin qtdeclarative5-localstorage-plugin qtdeclarative5-privatewidgets-plugin qtdeclarative5-qtfeedback-plugin qtdeclarative5-qtquick2-plugin qtdeclarative5-ubuntu-ui-extras-browser-plugin qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-unity-action-plugin qtdeclarative5-window-plugin remmina remmina-common remmina-plugin-rdp remmina-plugin-vnc signon-keyring-extension signon-plugin-oauth2 signon-ui signond sni-qt sphinx-voxforge-hmm-en sphinx-voxforge-lm-en telepathy-indicator thunderbird thunderbird-gnome-support totem-mozilla ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-session ubuntu-settings ubuntu-sounds ubuntu-sso-client-qt ubuntu-ui-toolkit-theme ubuntu-wallpapers ubuntu-wallpapers-trusty ubuntuone-client-data unity unity-asset-pool unity-control-center unity-control-center-signon unity-greeter unity-gtk-module-common unity-gtk2-module unity-gtk3-module unity-lens-applications unity-lens-files unity-lens-friends unity-lens-music unity-lens-photos unity-lens-video unity-scope-audacious unity-scope-calculator unity-scope-chromiumbookmarks unity-scope-clementine unity-scope-colourlovers unity-scope-devhelp unity-scope-firefoxbookmarks unity-scope-gdrive unity-scope-gmusicbrowser unity-scope-gourmet unity-scope-guayadeque unity-scope-home unity-scope-manpages unity-scope-musicstores unity-scope-musique unity-scope-openclipart unity-scope-texdoc unity-scope-tomboy unity-scope-video-remote unity-scope-virtualbox unity-scope-yelp unity-scope-zotero unity-scopes-master-default unity-scopes-runner unity-services unity-settings-daemon unity-voice-service unity-webapps-common unity-webapps-qml unity-webapps-service vbetool webaccounts-extension-common webapp-container webbrowser-app whoopsie-preferences xcursor-themes xul-ext-unity xul-ext-webaccounts xul-ext-websites-integration

```
**Step #6**: Reboot again and you should be ready to begin using Ubuntu GNOME.

---

### Post by kansasnoob on 2014-05-08
New follow-up to-do list:

#1: Does installing 'gnome-session' install 'mutter'.

#2: Follow up on this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1284417](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1284417)

#3: Try these two commands:

```
tasksel remove ubuntu-desktop 
```

```
tasksel -t remove ubuntu-desktop 
```

#4:  Can you confirm that gnome-shell does not work with only libmutter and mutter-common installed? (I believe 'mutter' itself is not needed but need to be sure).

---

### Post by kansasnoob on 2014-05-10
> **kansasnoob said:**
> New follow-up to-do list:

#1: Does installing 'gnome-session' install 'mutter'.

#2: Follow up on this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1284417](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1284417)

#3: Try these two commands:

```
tasksel remove ubuntu-desktop 
```

```
tasksel -t remove ubuntu-desktop 
```

#4:  Can you confirm that gnome-shell does not work with only libmutter and mutter-common installed? (I believe 'mutter' itself is not needed but need to be sure).

Regarding #4 I'm just checking to see what happens if I remove 'mutter' from Ubuntu GNOME:

```
lance@lance-desktop:~$ sudo apt-get remove mutter
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mutter ubuntu-gnome-desktop
0 upgraded, 0 newly installed, 2 to remove and 10 not upgraded.
After this operation, 342 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 147674 files and directories currently installed.)
Removing ubuntu-gnome-desktop (0.32) ...
Removing mutter (3.10.4-0ubuntu2) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
lance@lance-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.

```

Both the GNOME and GNOME Classic sessions still boot fine with 'mutter' removed and reinstalling only 'mutter' shows:

```
lance@lance-desktop:~$ sudo apt-get install mutter
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mutter
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
Need to get 16.8 kB of archives.
After this operation, 314 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/universe mutter i386 3.10.4-0ubuntu2 [16.8 kB]
Fetched 16.8 kB in 0s (66.0 kB/s) 
Selecting previously unselected package mutter.
(Reading database ... 147658 files and directories currently installed.)
Preparing to unpack .../mutter_3.10.4-0ubuntu2_i386.deb ...
Unpacking mutter (3.10.4-0ubuntu2) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up mutter (3.10.4-0ubuntu2) ...
update-alternatives: using /usr/bin/mutter to provide /usr/bin/x-window-manager (x-window-manager) in auto mode

```

---

### Post by kansasnoob on 2014-05-10
> **kansasnoob said:**
> New follow-up to-do list:

#1: Does installing 'gnome-session' install 'mutter'.

#2: Follow up on this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1284417](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1284417)

#3: Try these two commands:

```
tasksel remove ubuntu-desktop 
```

```
tasksel -t remove ubuntu-desktop 
```

#4:  Can you confirm that gnome-shell does not work with only libmutter and mutter-common installed? (I believe 'mutter' itself is not needed but need to be sure).

Regarding #1, no:

```
lance@lance-desktop:~$ sudo apt-get install gnome-session --assume-no
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gnome-settings-daemon
Suggested packages:
  desktop-base
The following NEW packages will be installed:
  gnome-session gnome-settings-daemon
0 upgraded, 2 newly installed, 0 to remove and 15 not upgraded.
Need to get 492 kB of archives.
After this operation, 2,775 kB of additional disk space will be used.
Do you want to continue? [Y/n] N
Abort.

```

And installing 'gnome-shell' does not install 'gnome-session' or 'mutter':

```
lance@lance-desktop:~$ sudo apt-get install gnome-shell --assume-no
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0
  gir1.2-gnomedesktop-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-nmgtk-1.0
  gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs gnome-control-center
  gnome-control-center-data gnome-icon-theme-full gnome-settings-daemon
  gnome-shell-common gnome-themes-standard gnome-themes-standard-data
  gtk2-engines-pixbuf libcaribou-common libcaribou0 libgdm1 libgjs0e
  libgoa-backend-1.0-1 libmozjs-24-0 libmutter0c libxcb-keysyms1
  libxcb-xf86dri0 libxcb-xv0 mutter-common xserver-xephyr
The following NEW packages will be installed:
  gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0
  gir1.2-gnomedesktop-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-nmgtk-1.0
  gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs gnome-control-center
  gnome-control-center-data gnome-icon-theme-full gnome-settings-daemon
  gnome-shell gnome-shell-common gnome-themes-standard
  gnome-themes-standard-data gtk2-engines-pixbuf libcaribou-common libcaribou0
  libgdm1 libgjs0e libgoa-backend-1.0-1 libmozjs-24-0 libmutter0c
  libxcb-keysyms1 libxcb-xf86dri0 libxcb-xv0 mutter-common xserver-xephyr
0 upgraded, 42 newly installed, 0 to remove and 15 not upgraded.
Need to get 20.3 MB of archives.
After this operation, 62.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] N
Abort.

```

---

### Post by kansasnoob on 2014-05-10
> **kansasnoob said:**
> New follow-up to-do list:

#1: Does installing 'gnome-session' install 'mutter'.

#2: Follow up on this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1284417](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1284417)

#3: Try these two commands:

```
tasksel remove ubuntu-desktop 
```

```
tasksel -t remove ubuntu-desktop 
```

#4:  Can you confirm that gnome-shell does not work with only libmutter and mutter-common installed? (I believe 'mutter' itself is not needed but need to be sure).

Regarding #3:

```
lance@lance-desktop:~$ sudo tasksel -t remove ubuntu-desktop
[sudo] password for lance: 
debconf-apt-progress -- apt-get -q -y install sni-qt- xfonts-mathml- libsndfile1- liblua5.2-0- python-qt4-dbus- adium-theme-ubuntu- libreoffice-math- gstreamer1.0-nice- ubuntu-artwork- libebook-contacts-1.2-0- libqtcore4- gstreamer0.10-nice- metacity-common- vino- unity-scope-devhelp- unity-services- python3-markupsafe- mcp-account-manager-uoa- liboxideqtcore0- deja-dup-backend-gvfs- libreoffice-writer- unity-scope-firefoxbookmarks- thunderbird-gnome-support- overlay-scrollbar-gtk3- unity-scope-gmusicbrowser- indicator-printers- libcurl3- gir1.2-messagingmenu-1.0- hud- libmspub-0.0-0- liboauth0- unity-scope-calculator- libreoffice-ogltrans- gir1.2-ebookcontacts-1.2- whoopsie-preferences- libaccount-plugin-google- gir1.2-networkmanager-1.0- python3-checkbox-support- unity-control-center-signon- unity-scope-chromiumbookmarks- account-plugin-jabber- libpurple0- uno-libs3- libfolks-eds25- libfriends0- dconf-cli- rhythmbox-data- onboard-data- python-sip- libgssdp-1.0-3- libpwquality-common- whoopsie- geoclue-ubuntu-geoip- account-plugin-windows-live- ubuntu-wallpapers- telepathy-salut- gnome-font-viewer- libdmapsharing-3.0-2- rhythmbox-plugin-zeitgeist- gnome-power-manager- cheese-common- libbamf3-2- remmina-plugin-vnc- nautilus-sendto-empathy- libgweather-3-6- unity-lens-photos- unity-scope-home- gir1.2-ibus-1.0- branding-ubuntu- python3-urllib3- libqt5sensors5- libcmis-0.4-4- python3-requests- libvncserver0- unity-voice-service- cheese- eog- nautilus-share- libgsettings-qt1- python3-uno- libgles2-mesa- rhythmbox- python-lockfile- libxcb-randr0- cups-pk-helper- unity-lens-music- xul-ext-webaccounts- libwpd-0.9-9- unity-scope-musicstores- libpyzy-1.0-0- libreoffice-common- libtelepathy-farstream3- libspeex1- ure- plainbox-provider-resource-generic- libgupnp-1.0-4- qtdeclarative5-window-plugin- libqtdbus4- gnome-bluetooth- gnome-screensaver- nux-tools- libqt4-scripttools- libglewmx1.10- libreoffice-base-core- libaccount-plugin-1.0-0- unity-gtk-module-common- apturl-common- unity-lens-applications- unity-gtk2-module- libwps-0.2-2- python3-pyparsing- unity-scope-texdoc- unity-scope-openclipart- signond- libcheese-gtk23- hwdata- gir1.2-rb-3.0- libunityvoice1- libflac8- libvorbis0a- gnome-user-share- friends-twitter- xdg-user-dirs-gtk- nautilus-sendto- libufe-xidgetter0- libunity-misc4- libgdata13- gnome-mahjongg- libqt5sql5-sqlite- unity-lens-friends- libcdio13- libfarstream-0.2-2- libxcb-image0- libqt5xml5- python3-checkbox-ng- libqt5sql5- xul-ext-unity- python3-plainbox- pm-utils- unity- gnomine- libxcb-xkb1- empathy- libsignon-qt5-1- unity-settings-daemon- libexttextcat-2.0-0- ubuntu-docs- checkbox-ng-service- friends- libraw1394-11- ibus-table- libqt5webkit5- gstreamer0.10-x- plainbox-secure-policy- libcamel-1.2-45- ubuntu-wallpapers-trusty- remmina- libprotobuf8- libcolamd2.8.0- gir1.2-signon-1.0- python3-feedparser- nautilus- libzeitgeist-1.0-1- webbrowser-app- gnome-control-center-shared-data- indicator-bluetooth- indicator-power- libqt4-script- libreoffice-avmedia-backend-gstreamer- libqt5qml-graphicaleffects- indicator-keyboard- libunity-core-6.0-9- libqtgui4- unity-scope-guayadeque- account-plugin-flickr- signon-keyring-extension- cracklib-runtime- telepathy-haze- qtdeclarative5-privatewidgets-plugin- libpocketsphinx1- libtelepathy-logger3- qtdeclarative5-unity-action-plugin- telepathy-idle- ubuntu-mono- librdf0- libqt5gui5- indicator-appmenu- libedata-cal-1.2-23- libqt5widgets5- python-ibus- libecal-1.2-16- libgpod-common- libwpg-0.2-2- libzephyr4- libreoffice-impress- libaccounts-qt5-1- unity-scope-colourlovers- signon-ui- unity-scope-clementine- qtdeclarative5-dialogs-plugin- rhythmbox-plugin-magnatune- libmeanwhile1- libcolumbus1-common- qtdeclarative5-localstorage-plugin- signon-plugin-oauth2- libedataserver-1.2-18- unity-asset-pool- libqt4-xml- libunity-webapps0- qt-at-spi- libclucene-contribs1- gnome-session-canberra- libasyncns0- gstreamer0.10-plugins-good- libcheese7- libreoffice-pdfimport- liblangtag-common- libqt5qml5- bamfdaemon- python3-mako- unity-scope-zotero- libunity-gtk2-parser0- libboost-date-time1.54.0- libtimezonemap1- qtdeclarative5-ubuntu-ui-toolkit-plugin- libvorbisenc2- ubuntu-system-service- rhythmbox-mozilla- gnome-system-log- libexempi3- libgnomekbd8- gnome-system-monitor- libexttextcat-data- compiz-core- notify-osd- libgdata-common- gnome-session-bin- libhud2- libpulse0- unity-scope-virtualbox- qtcore4-l10n- ubuntu-sso-client-qt- lp-solve- telepathy-mission-control-5- unity-scope-audacious- libfarstream-0.1-0- libcdio-cdda1- libqt4-dbus- compiz-plugins-default- libcompizconfig0- apg- gnome-settings-daemon-schemas- python-qt4- libxcb-render-util0- obexd-client- unity-scope-manpages- duplicity- libwhoopsie0- libqt5dbus5- liborcus-0.6-0- libqt4-declarative- libqt5positioning5- libsgutils2-2- libtheora0- gnome-screenshot- libqt4-opengl- ibus- libwacom2- geoclue- unity-scope-gdrive- libwmf0.2-7- libjack-jackd2-0- apturl- webapp-container- unity-scope-yelp- unity-greeter- xul-ext-websites-integration- gnome-video-effects- libxcb-icccm4- account-plugin-salut- libgoa-1.0-common- libqt4-test- gkbd-capplet- libqt5network5- libqt4-sql- folks-common- libebook-1.2-14- overlay-scrollbar-gtk2- unity-webapps-qml- unity-control-center- libnux-4.0-common- libaccount-plugin-generic-oauth- libsignon-plugins-common1- libqt5organizer5- libopencc1- librasqal3- account-plugin-aim- account-plugin-twitter- libgweather-common- libaudio2- libqtassistantclient4- unity-lens-files- libcdio-paranoia1- gstreamer1.0-alsa- telepathy-indicator- gir1.2-gnomekeyring-1.0- libqt4-xmlpatterns- vbetool- gir1.2-accounts-1.0- libnux-4.0-0- qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets- libqt5quick5- baobab- libqt5test5- compiz- qtdeclarative5-accounts-plugin- session-migration- libsystemd-journal0- libunity-control-center1- qtdeclarative5-ubuntu-ui-extras-browser-plugin- libebackend-1.2-7- libedata-book-1.2-20- libx86-1- libqt5webkit5-qmlwebkitplugin- signon-plugin-password- gnome-disk-utility- ubuntu-ui-toolkit-theme- gnome-terminal-data- libgnome-desktop-3-7- aisleriot- xdiagnose- unity-gtk3-module- unity-webapps-service- libfolks25- unity-scope-video-remote- libnice10- gir1.2-goa-1.0- checkbox-gui- qdbus- appmenu-qt- libsbc1- libgupnp-igd-1.0-4- remmina-plugin-rdp- libqt5printsupport5- pulseaudio-module-bluetooth- libhyphen0- friends-facebook- activity-log-manager-control-center- indicator-session- unity-scopes-runner- python3-lxml- example-content- unity-scope-musique- checkbox-ng- overlay-scrollbar- gnome-mines- libproxy1-plugin-networkmanager- ethtool- libogg0- deja-dup- seahorse- libwhoopsie-preferences0- gir1.2-edataserver-1.2- libreoffice-calc- libgee2- libqt4-network- friends-dispatcher- libgpod4- rhythmbox-plugins- libreoffice-style-human- unity-scope-tomboy- gnome-sudoku- libmission-control-plugins0- intel-gpu-tools- evolution-data-server-common- libwmf0.2-7-gtk- evolution-data-server-online-accounts- gtk3-engines-unico- libgnome-control-center1- gir1.2-secret-1- onboard- ubuntu-session- libqt5multimedia5- libqt4-svg- mousetweaks- libgtop2-7- libgtop2-common- libreoffice-gnome- rhythmbox-plugin-cdrecorder- libunity-gtk3-parser0- libgnomekbd-common- libdecoration0- libdbusmenu-qt5- libclucene-core1- libfolks-telepathy25- guile-2.0-libs- liborc-0.4-0- unity-scope-gourmet- libpwquality1- appmenu-qt5- libsignon-extension1- liblangtag1- telepathy-gabble- libsphinxbase1- activity-log-manager- libpurple-bin- libraptor2-0- libglew1.10- qtdeclarative5-qtfeedback-plugin- libmhash2- ubuntu-desktop- sphinx-voxforge-lm-en- libboost-system1.54.0- empathy-common- evolution-data-server- oxideqt-codecs- libreoffice-draw- gnome-terminal- libqt5core5a- thunderbird- webaccounts-extension-common- light-themes- ubuntu-sounds- indicator-datetime- libunity-action-qt1- libqt4-sql-sqlite- unity-lens-video- libthumbnailer0- fonts-nanum- libdbusmenu-qt2- account-plugin-google- librhythmbox-core8- plainbox-provider-checkbox- libmythes-1.2-0- libibus-1.0-5- libqt5opengl5- gnome-session-common- unity-scopes-master-default- libqtwebkit4- notify-osd-icons- gstreamer1.0-tools- libcolumbus1- liboxideqt-qmlplugin- gir1.2-gnomebluetooth-1.0- landscape-client-ui-install- gir1.2-appindicator3-0.1- libupstart1- account-plugin-yahoo- remmina-common- libcrack2- libmetacity-private0a- libreoffice-presentation-minimizer- libwacom-common- ubuntuone-client-data- sphinx-voxforge-hmm-en- libqt4-help- libssh-4- ibus-pinyin- gstreamer1.0-plugins-base-apps- wamerican- qtdeclarative5-qtquick2-plugin- gnome-desktop3-data- libgc1c2- plymouth-theme-ubuntu-logo- libcanberra-gtk0- qtchooser- libcanberra-gtk-module- libproxy1-plugin-gsettings- librsync1- libcdr-0.0-0- ibus-gtk3- libreoffice-core- compiz-gnome- unity-webapps-common- gnome-contacts- ibus-gtk- libcanberra-pulse- account-plugin-facebook- libqt5feedback5- media-player-info- libqt5svg5- libvisio-0.0-0- libreoffice-gtk- libyajl2- libgoa-1.0-0b- gir1.2-ebook-1.2- gir1.2-gst-plugins-base-1.0- gir1.2-gdata-0.0- libqt4-designer- telepathy-logger-

```

That made me really curious so I tried:

```
sudo tasksel remove ubuntu-desktop
```

Followed by:

```
sudo tasksel install ubuntu-gnome-desktop
```

Then:

```
sudo apt-get -f install
```

```
lance@lance-desktop:~$ sudo apt-get -f install
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  freepats liba52-0.7.4 libass4 libavutil52 libcdaudio1 libdca0
  libdirac-encoder0 libdirectfb-1.2-9 libdvdnav4 libdvdread4 libfaad2
  libfftw3-double3 libflite1 libgme0 libgsm1 libgstreamer-plugins-bad1.0-0
  libgtkglext1 libilmbase6 libkate1 libmad0 libmimic0 libmms0 libmodplug1
  libmp3lame0 libmpcdec6 libmpeg2-4 libmpg123-0 libofa0 libopenal-data
  libopenal1 libopencore-amrnb0 libopencore-amrwb0 libopencv-calib3d2.4
  libopencv-core2.4 libopencv-features2d2.4 libopencv-flann2.4
  libopencv-imgproc2.4 libopencv-ml2.4 libopencv-video2.4 libopenexr6
  libopenjpeg2 libopus0 libsidplay1 libsoundtouch0 libspandsp2 libsrtp0
  libswscale2 libtbb2 libts-0.0-0 libtwolame0 libva1 libvo-aacenc0
  libvo-amrwbenc0 libwildmidi-config libwildmidi1 libx264-142 libxvidcore4
  libzbar0 libzvbi-common libzvbi0 tsconf
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

Well, I did that kind of backwards, and I see some cleanup is still needed but I have a thought:

```
The following packages will be REMOVED:
  dmz-cursor-theme doc-base gsettings-ubuntu-schemas
  gstreamer0.10-plugins-base-apps gstreamer0.10-tools gtk2-engines-murrine
  indicator-messages language-selector-gnome libfreerdp1
  liblightdm-gobject-1-0 liburl-dispatcher1 libuuid-perl libwnck-common
  libwnck22 libyaml-tiny-perl lightdm pkg-config python-gconf ubuntu-settings
  xcursor-themes

```

Stay tuned :)

---

### Post by kansasnoob on 2014-05-11
OK, after reviewing some logs, I think next time I'll try (with a freshly installed and updated Ubuntu Trusty):

```
sudo apt-get install tasksel
```

```
sudo tasksel install ubuntu-gnome-desktop
```

Reboot and select GNOME as session.

```
sudo tasksel remove ubuntu-desktop
```

```
sudo apt-get autoremove
```

Then reboot again and check for missing depends and recommends.

**[COLOR="#FF0000"]This was a dumb idea!!!![/COLOR]** Don't know what I was thinking, clearly 'ubuntu-desktop' would have to be removed before installing 'ubuntu-gnome-desktop' because they do share a large number of packages.

---

### Post by kansasnoob on 2014-05-11
Time to rinse-n-repeat :D

```
lance@lance-desktop:~$ sudo tasksel -t remove ubuntu-desktop
[sudo] password for lance: 
debconf-apt-progress -- apt-get -q -y install gir1.2-ebookcontacts-1.2- libglewmx1.10- gtk3-engines-unico- libraw1394-11- gir1.2-secret-1- libtheora0- gnome-contacts- libqt5qml5- gnome-mines- unity-webapps-qml- libgupnp-igd-1.0-4- rhythmbox-data- unity-scope-gourmet- libexttextcat-2.0-0- signon-keyring-extension- gnome-system-monitor- libgoa-1.0-0b- liblangtag1- libqt4-declarative- libwpg-0.2-2- account-plugin-windows-live- gnome-terminal-data- libcolumbus1- telepathy-haze- activity-log-manager-control-center- pm-utils- libedataserver-1.2-18- libgee2- libexttextcat-data- liborcus-0.6-0- libogg0- libmetacity-private0a- qt-at-spi- unity-scope-musicstores- python-qt4-dbus- unity-control-center- libqtcore4- media-player-info- libqt5printsupport5- unity-lens-music- unity-lens-photos- libreoffice-writer- libcmis-0.4-4- unity-scope-texdoc- libthumbnailer0- liblangtag-common- gir1.2-goa-1.0- qtdeclarative5-window-plugin- libtelepathy-farstream3- libpwquality-common- metacity-common- libexempi3- libpurple0- libcdio13- libsignon-plugins-common1- python3-plainbox- unity-gtk-module-common- libfriends0- libebook-contacts-1.2-0- libqt5opengl5- libgnome-control-center1- libqt4-sql-sqlite- libqt4-dbus- qtdeclarative5-ubuntu-ui-extras-browser-plugin- python3-pyparsing- adium-theme-ubuntu- gkbd-capplet- webbrowser-app- libgnomekbd8- unity-asset-pool- indicator-printers- libwmf0.2-7-gtk- whoopsie-preferences- onboard- gir1.2-gst-plugins-base-1.0- libecal-1.2-16- libxcb-image0- xul-ext-websites-integration- landscape-client-ui-install- libqt5dbus5- unity-scopes-master-default- libqt5sensors5- ibus-pinyin- unity-lens-files- libaccount-plugin-generic-oauth- gnome-user-share- vbetool- gir1.2-networkmanager-1.0- libunity-core-6.0-9- thunderbird- gir1.2-signon-1.0- libqt5feedback5- plainbox-secure-policy- libgdata13- wamerican- libcolumbus1-common- libqtdbus4- aisleriot- libfolks-telepathy25- signon-ui- libraptor2-0- libreoffice-pdfimport- libqt5sql5-sqlite- libpyzy-1.0-0- gnome-power-manager- libyajl2- oxideqt-codecs- python-qt4- unity-scope-video-remote- telepathy-idle- librhythmbox-core8- libx86-1- activity-log-manager- gnome-disk-utility- indicator-appmenu- onboard-data- account-plugin-facebook- liboxideqtcore0- hwdata- xdiagnose- unity-webapps-common- libfolks25- libqtgui4- gir1.2-gdata-0.0- geoclue- seahorse- rhythmbox-plugin-cdrecorder- libsystemd-journal0- libqt4-scripttools- libqt5quick5- mousetweaks- unity-scope-musique- remmina-plugin-rdp- gnome-session-bin- gir1.2-ebook-1.2- gnome-font-viewer- gstreamer1.0-nice- libqt4-sql- gstreamer0.10-plugins-good- hud- ubuntuone-client-data- indicator-session- libxcb-randr0- friends-facebook- gnome-system-log- libmission-control-plugins0- libedata-book-1.2-20- libnice10- remmina- libsphinxbase1- python-lockfile- libaudio2- qtchooser- libspeex1- xul-ext-unity- gstreamer1.0-plugins-base-apps- libnux-4.0-0- account-plugin-flickr- intel-gpu-tools- python3-markupsafe- geoclue-ubuntu-geoip- account-plugin-google- gir1.2-gnomebluetooth-1.0- remmina-common- libqt5qml-graphicaleffects- pulseaudio-module-bluetooth- libcolamd2.8.0- rhythmbox-plugin-zeitgeist- libhud2- branding-ubuntu- account-plugin-twitter- account-plugin-jabber- account-plugin-yahoo- libprotobuf8- libreoffice-impress- libqt5webkit5-qmlwebkitplugin- ibus-gtk3- unity-scope-devhelp- ubuntu-ui-toolkit-theme- libwps-0.2-2- libsignon-qt5-1- eog- unity-scope-yelp- libqt5test5- libnux-4.0-common- libreoffice-gtk- gir1.2-ibus-1.0- libzephyr4- cups-pk-helper- libcompizconfig0- python3-checkbox-ng- libwacom2- libqt5positioning5- cracklib-runtime- libufe-xidgetter0- libunity-gtk3-parser0- ibus-table- libreoffice-gnome- libunity-action-qt1- account-plugin-salut- libzeitgeist-1.0-1- unity-scope-guayadeque- nux-tools- libcdio-paranoia1- gnomine- rhythmbox-mozilla- libaccount-plugin-google- unity-scope-manpages- gnome-video-effects- libqt4-xml- checkbox-ng-service- libopencc1- apg- libxcb-xkb1- libwhoopsie-preferences0- libwpd-0.9-9- ure- session-migration- libreoffice-style-human- gnome-terminal- libqt5widgets5- overlay-scrollbar-gtk3- unity-scope-gdrive- libsbc1- unity-gtk3-module- libflac8- libibus-1.0-5- qdbus- unity-scope-colourlovers- liboxideqt-qmlplugin- gir1.2-rb-3.0- unity-lens-applications- libcanberra-gtk-module- lp-solve- plainbox-provider-checkbox- baobab- libssh-4- libqt5sql5- libsgutils2-2- ubuntu-session- unity-webapps-service- liborc-0.4-0- unity-gtk2-module- libreoffice-common- libqt4-script- unity-scope-clementine- libgnome-desktop-3-7- python-ibus- fonts-nanum- unity-scope-openclipart- ubuntu-artwork- libebook-1.2-14- libpulse0- libtimezonemap1- empathy- gstreamer0.10-x- nautilus-share- libmythes-1.2-0- cheese-common- libqt4-svg- libgsettings-qt1- xfonts-mathml- libcdio-cdda1- unity-scope-zotero- gnome-screensaver- sni-qt- ubuntu-sso-client-qt- obexd-client- duplicity- empathy-common- libqt5organizer5- libproxy1-plugin-gsettings- libfolks-eds25- indicator-keyboard- libdmapsharing-3.0-2- account-plugin-aim- qtdeclarative5-dialogs-plugin- libcanberra-pulse- overlay-scrollbar-gtk2- libgupnp-1.0-4- libclucene-contribs1- librasqal3- python3-checkbox-support- python3-feedparser- evolution-data-server-common- qtdeclarative5-localstorage-plugin- qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets- libcdr-0.0-0- nautilus-sendto-empathy- libvorbisenc2- qtdeclarative5-unity-action-plugin- libqt5gui5- unity-greeter- libvorbis0a- gstreamer0.10-nice- libvncserver0- libupstart1- sphinx-voxforge-lm-en- appmenu-qt5- libmeanwhile1- unity-scope-virtualbox- libtelepathy-logger3- python3-uno- ubuntu-wallpapers-trusty- unity-control-center-signon- libgweather-3-6- unity-scope-audacious- evolution-data-server-online-accounts- ubuntu-wallpapers- telepathy-indicator- ubuntu-mono- uno-libs3- qtdeclarative5-accounts-plugin- libqt4-opengl- notify-osd-icons- libxcb-render-util0- libbamf3-2- libgtop2-common- libsndfile1- telepathy-salut- ubuntu-docs- example-content- webapp-container- bamfdaemon- unity-scopes-runner- libwmf0.2-7- libcamel-1.2-45- sphinx-voxforge-hmm-en- gnome-desktop3-data- libvisio-0.0-0- cheese- mcp-account-manager-uoa- qtdeclarative5-qtfeedback-plugin- liblua5.2-0- appmenu-qt- qtdeclarative5-qtquick2-plugin- libreoffice-math- guile-2.0-libs- libunity-gtk2-parser0- libproxy1-plugin-networkmanager- libedata-cal-1.2-23- libclucene-core1- libqt5network5- libcheese7- compiz-gnome- libreoffice-core- gnome-screenshot- webaccounts-extension-common- gnome-control-center-shared-data- libmspub-0.0-0- libgoa-1.0-common- indicator-bluetooth- deja-dup-backend-gvfs- libreoffice-avmedia-backend-gstreamer- ubuntu-desktop- libreoffice-base-core- python3-urllib3- friends-twitter- ubuntu-sounds- libgles2-mesa- libgssdp-1.0-3- friends- libgpod4- libcurl3- libgtop2-7- libjack-jackd2-0- libqt4-network- deja-dup- compiz- libqt4-xmlpatterns- libgnomekbd-common- gir1.2-edataserver-1.2- libqt5core5a- gstreamer1.0-tools- friends-dispatcher- libunity-webapps0- dconf-cli- libpwquality1- libqt5webkit5- libmhash2- libunityvoice1- folks-common- gnome-sudoku- libdecoration0- librsync1- libqt4-test- unity-scope-home- overlay-scrollbar- rhythmbox-plugins- libgpod-common- libgweather-common- remmina-plugin-vnc- apturl-common- libqt5svg5- qtdeclarative5-privatewidgets-plugin- libxcb-icccm4- ethtool- ibus- libpocketsphinx1- libqtwebkit4- signon-plugin-oauth2- rhythmbox-plugin-magnatune- libgc1c2- libfarstream-0.2-2- libqt5xml5- whoopsie- python3-lxml- unity-scope-calculator- libaccounts-qt5-1- gnome-bluetooth- gir1.2-gnomekeyring-1.0- evolution-data-server- telepathy-gabble- nautilus- libqt4-designer- vino- thunderbird-gnome-support- qtdeclarative5-ubuntu-ui-toolkit-plugin- libboost-system1.54.0- libreoffice-calc- unity-lens-video- signon-plugin-password- python3-mako- gstreamer1.0-alsa- libqt4-help- unity-scope-chromiumbookmarks- unity-settings-daemon- unity-scope-gmusicbrowser- gnome-session-common- libhyphen0- rhythmbox- qtcore4-l10n- unity-scope-firefoxbookmarks- libglew1.10- gir1.2-appindicator3-0.1- libreoffice-presentation-minimizer- libboost-date-time1.54.0- checkbox-ng- unity-services- gir1.2-accounts-1.0- libwhoopsie0- indicator-datetime- plymouth-theme-ubuntu-logo- unity-lens-friends- librdf0- liboauth0- libgdata-common- gir1.2-messagingmenu-1.0- gnome-settings-daemon-schemas- libreoffice-ogltrans- libdbusmenu-qt2- telepathy-mission-control-5- compiz-core- gnome-session-canberra- libasyncns0- unity-scope-tomboy- unity-voice-service- libunity-control-center1- indicator-power- libunity-misc4- nautilus-sendto- libsignon-extension1- unity- xul-ext-webaccounts- light-themes- ibus-gtk- libfarstream-0.1-0- libcanberra-gtk0- apturl- notify-osd- libqt5multimedia5- telepathy-logger- libreoffice-draw- python3-requests- xdg-user-dirs-gtk- compiz-plugins-default- libcheese-gtk23- libcrack2- signond- libqtassistantclient4- ubuntu-system-service- python-sip- libaccount-plugin-1.0-0- libpurple-bin- plainbox-provider-resource-generic- gnome-mahjongg- checkbox-gui- libdbusmenu-qt5- libebackend-1.2-7- libwacom-common-

```

It's hard to parse that since packages are not in alphabetical order.

---

### Post by kansasnoob on 2014-05-12
Just following up. After parsing the output of that command in post #20 and noticing that 'gnome-terminal' is removed in the process I decided to try running "tasksel remove ubuntu-desktop" in a TTY launched using Ctrl + Alt + F1:

```
Start-Date: 2014-05-11  21:40:06
Commandline: apt-get -o APT::Status-Fd=4 -o APT::Keep-Fds::=5 -o APT::Keep-Fds::=6 -q -y install gnome-terminal-data- gir1.2-accounts-1.0- libedata-cal-1.2-23- friends-dispatcher- unity-scope-gdrive- ubuntu-wallpapers-trusty- libfolks-telepathy25- account-plugin-salut- unity-gtk2-module- libwpg-0.2-2- liboxideqtcore0- fonts-nanum- libsbc1- liborcus-0.6-0- remmina-plugin-vnc- libbamf3-2- gir1.2-ebookcontacts-1.2- libdmapsharing-3.0-2- libraptor2-0- xul-ext-websites-integration- libglew1.10- plainbox-provider-resource-generic- libcrack2- qtcore4-l10n- libspeex1- onboard- qdbus- libwhoopsie0- gstreamer0.10-plugins-good- libcanberra-gtk-module- xul-ext-unity- libqt5dbus5- gir1.2-gnomebluetooth-1.0- gir1.2-gnomekeyring-1.0- gir1.2-appindicator3-0.1- unity-lens-friends- libunity-action-qt1- unity-scope-home- liborc-0.4-0- python3-urllib3- deja-dup- gir1.2-signon-1.0- libreoffice-impress- libreoffice-pdfimport- libcamel-1.2-45- libgweather-common- unity-scope-calculator- libqt4-sql-sqlite- libreoffice-core- python3-mako- cheese- libfolks-eds25- telepathy-salut- thunderbird- nux-tools- apg- libssh-4- libclucene-contribs1- unity-scope-firefoxbookmarks- qtdeclarative5-ubuntu-ui-toolkit-plugin- unity-scope-texdoc- gir1.2-goa-1.0- indicator-session- liblangtag-common- account-plugin-yahoo- libgoa-1.0-common- libcompizconfig0- libhud2- python3-pyparsing- unity-scope-manpages- libupstart1- libqt5xml5- libmetacity-private0a- libqt4-designer- qtdeclarative5-dialogs-plugin- gnome-mahjongg- libopencc1- nautilus- libqt5webkit5-qmlwebkitplugin- libcdio13- gnome-sudoku- libgupnp-1.0-4- ubuntu-mono- thunderbird-gnome-support- libunity-gtk3-parser0- libproxy1-plugin-gsettings- liboauth0- activity-log-manager- guile-2.0-libs- plainbox-secure-policy- adium-theme-ubuntu- obexd-client- libqt4-script- libqtwebkit4- cups-pk-helper- remmina-common- nautilus-sendto-empathy- unity-scope-video-remote- gnome-disk-utility- libgupnp-igd-1.0-4- libzephyr4- libvncserver0- libqt5positioning5- libtelepathy-logger3- liboxideqt-qmlplugin- gir1.2-messagingmenu-1.0- friends- gir1.2-ebook-1.2- libproxy1-plugin-networkmanager- bamfdaemon- gir1.2-rb-3.0- gnome-mines- unity-services- unity-gtk3-module- indicator-printers- libcdio-cdda1- libedataserver-1.2-18- libwmf0.2-7- libglewmx1.10- libqt5printsupport5- libtheora0- unity-control-center-signon- python3-lxml- libqt4-xmlpatterns- libqtdbus4- libclucene-core1- ure- rhythmbox-plugin-zeitgeist- hud- gstreamer0.10-x- libasyncns0- account-plugin-twitter- libgdata-common- libunity-misc4- libfolks25- python3-checkbox-support- libqt5core5a- compiz-gnome- signond- hwdata- baobab- libwpd-0.9-9- libcolumbus1- unity-scopes-master-default- libraw1394-11- account-plugin-windows-live- ubuntu-session- unity-scope-gmusicbrowser- libcmis-0.4-4- session-migration- empathy- libqt5sensors5- libexttextcat-2.0-0- libmhash2- gnomine- unity-webapps-qml- whoopsie-preferences- libqt4-help- friends-facebook- ibus- overlay-scrollbar-gtk2- notify-osd- libreoffice-base-core- plymouth-theme-ubuntu-logo- libgtop2-common- indicator-appmenu- mousetweaks- gstreamer1.0-plugins-base-apps- intel-gpu-tools- xdiagnose- deja-dup-backend-gvfs- libgc1c2- gnome-desktop3-data- ibus-gtk3- ubuntuone-client-data- unity-scope-audacious- aisleriot- libreoffice-avmedia-backend-gstreamer- libgles2-mesa- libpurple0- compiz-core- libqt4-sql- gnome-session-canberra- lp-solve- librdf0- libfriends0- gnome-power-manager- unity-gtk-module-common- light-themes- indicator-bluetooth- cracklib-runtime- libreoffice-writer- signon-ui- telepathy-logger- libsgutils2-2- friends-twitter- qtchooser- libqt5multimedia5- gtk3-engines-unico- libgtop2-7- rhythmbox-mozilla- uno-libs3- unity-greeter- libnux-4.0-0- unity-lens-video- plainbox-provider-checkbox- libcdr-0.0-0- libebook-contacts-1.2-0- unity-scope-clementine- libqt5feedback5- libaccount-plugin-generic-oauth- libsignon-qt5-1- libreoffice-style-human- gstreamer0.10-nice- landscape-client-ui-install- libmeanwhile1- seahorse- checkbox-gui- libpwquality-common- unity-lens-files- whoopsie- python3-uno- gnome-system-monitor- libedata-book-1.2-20- pulseaudio-module-bluetooth- libyajl2- ubuntu-artwork- libebackend-1.2-7- libqt5test5- libtimezonemap1- libfarstream-0.1-0- libmythes-1.2-0- unity-scope-musique- overlay-scrollbar- apturl-common- qtdeclarative5-privatewidgets-plugin- libqt5gui5- gir1.2-networkmanager-1.0- libgweather-3-6- libexempi3- dconf-cli- libsphinxbase1- unity-scope-chromiumbookmarks- gir1.2-gst-plugins-base-1.0- libcheese-gtk23- onboard-data- libboost-system1.54.0- libqt5webkit5- libdbusmenu-qt5- geoclue- libwacom2- libvisio-0.0-0- ubuntu-sso-client-qt- wamerican- python3-markupsafe- libzeitgeist-1.0-1- libgnomekbd-common- qtdeclarative5-localstorage-plugin- libcolamd2.8.0- libaccount-plugin-1.0-0- python3-feedparser- ubuntu-ui-toolkit-theme- ubuntu-desktop- libnice10- telepathy-mission-control-5- account-plugin-aim- libx86-1- libqt4-xml- libreoffice-calc- unity-scope-zotero- libqt5sql5-sqlite- unity-scope-virtualbox- libsystemd-journal0- libreoffice-ogltrans- appmenu-qt- xfonts-mathml- libsignon-plugins-common1- libaccount-plugin-google- ibus-pinyin- libwmf0.2-7-gtk- libunity-control-center1- libhyphen0- libqt5organizer5- python3-requests- libreoffice-common- gnome-terminal- libgnome-control-center1- libxcb-randr0- remmina-plugin-rdp- unity-voice-service- xdg-user-dirs-gtk- unity-scope-openclipart- libqt4-scripttools- libfarstream-0.2-2- gnome-control-center-shared-data- libxcb-icccm4- unity-lens-photos- unity-webapps-service- telepathy-idle- gir1.2-ibus-1.0- webapp-container- qtdeclarative5-ubuntu-ui-extras-browser-plugin- webbrowser-app- indicator-keyboard- eog- unity-scope-colourlovers- liblangtag1- libreoffice-gtk- xul-ext-webaccounts- compiz- unity-scope-gourmet- libgsettings-qt1- account-plugin-facebook- libwps-0.2-2- libnux-4.0-common- libunity-core-6.0-9- libgdata13- libgpod-common- unity-scope-devhelp- libgoa-1.0-0b- indicator-datetime- indicator-power- telepathy-gabble- gnome-user-share- librsync1- libsignon-extension1- appmenu-qt5- libreoffice-draw- qtdeclarative5-accounts-plugin- libufe-xidgetter0- libdbusmenu-qt2- telepathy-haze- libqt5svg5- python-qt4- unity-settings-daemon- libqt5sql5- liblua5.2-0- media-player-info- ethtool- libaccounts-qt5-1- libwacom-common- nautilus-sendto- example-content- qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets- qtdeclarative5-qtfeedback-plugin- libqt5qml-graphicaleffects- gir1.2-secret-1- signon-plugin-oauth2- libdecoration0- libexttextcat-data- libcurl3- nautilus-share- gnome-screensaver- python3-plainbox- folks-common- libcheese7- oxideqt-codecs- geoclue-ubuntu-geoip- libaudio2- libvorbis0a- libqt4-opengl- unity-scope-tomboy- libqtcore4- account-plugin-flickr- checkbox-ng- libgnome-desktop-3-7- libibus-1.0-5- libwhoopsie-preferences0- libqt5qml5- libpulse0- libvorbisenc2- account-plugin-google- ubuntu-docs- libcanberra-pulse- signon-keyring-extension- libpocketsphinx1- libmspub-0.0-0- libogg0- libpyzy-1.0-0- python-sip- libpwquality1- libxcb-xkb1- python-lockfile- mcp-account-manager-uoa- evolution-data-server-online-accounts- gir1.2-edataserver-1.2- libqt5widgets5- activity-log-manager-control-center- librhythmbox-core8- rhythmbox-plugins- libboost-date-time1.54.0- libgssdp-1.0-3- account-plugin-jabber- libgee2- branding-ubuntu- gnome-session-bin- gstreamer1.0-tools- libthumbnailer0- ubuntu-system-service- libcdio-paranoia1- gnome-system-log- compiz-plugins-default- apturl- unity- empathy-common- libjack-jackd2-0- ubuntu-wallpapers- qtdeclarative5-window-plugin- gstreamer1.0-nice- telepathy-indicator- libgpod4- rhythmbox- evolution-data-server-common- sphinx-voxforge-lm-en- libunity-gtk2-parser0- librasqal3- gnome-video-effects- gnome-settings-daemon-schemas- qt-at-spi- rhythmbox-plugin-magnatune- python-ibus- libxcb-image0- libunityvoice1- libecal-1.2-16- unity-webapps-common- gkbd-capplet- qtdeclarative5-unity-action-plugin- libebook-1.2-14- unity-lens-applications- libpurple-bin- ibus-table- libqt5quick5- libqt4-network- gnome-contacts- libqt4-declarative- libqt5network5- libgnomekbd8- vbetool- signon-plugin-password- metacity-common- libqtassistantclient4- unity-control-center- cheese-common- ubuntu-sounds- libreoffice-gnome- pm-utils- remmina- qtdeclarative5-qtquick2-plugin- libmission-control-plugins0- ibus-gtk- libqt5opengl5- evolution-data-server- gnome-font-viewer- unity-scopes-runner- libqt4-svg- webaccounts-extension-common- libflac8- libcanberra-gtk0- libunity-webapps0- unity-scope-yelp- libreoffice-math- libqt4-dbus- duplicity- unity-asset-pool- gstreamer1.0-alsa- sni-qt- libtelepathy-farstream3- gir1.2-gdata-0.0- gnome-bluetooth- libsndfile1- unity-scope-musicstores- python-qt4-dbus- checkbox-ng-service- sphinx-voxforge-hmm-en- libcolumbus1-common- libqt4-test- gnome-screenshot- vino- libreoffice-presentation-minimizer- notify-osd-icons- gnome-session-common- rhythmbox-data- libxcb-render-util0- rhythmbox-plugin-cdrecorder- libprotobuf8- python3-checkbox-ng- unity-lens-music- libqtgui4- overlay-scrollbar-gtk3- unity-scope-guayadeque-
Remove: gstreamer1.0-fluendo-mp3:i386 (0.10.23.debian-3), libreoffice-common:i386 (4.2.3~rc3-0ubuntu2), unity-settings-daemon:i386 (14.04.0+14.04.20140414-0ubuntu1), cracklib-runtime:i386 (2.9.1-1build1), gir1.2-gnomebluetooth-1.0:i386 (3.8.2.1-0ubuntu4), python3-markupsafe:i386 (0.18-1build2), unity-gtk3-module:i386 (0.0.0+14.04.20140403-0ubuntu1), libsgutils2-2:i386 (1.36-1ubuntu1), libflac8:i386 (1.3.0-2), unity-scope-yelp:i386 (0.1+13.10.20130723-0ubuntu1), libpocketsphinx1:i386 (0.8.0+real-0ubuntu6), checkbox-ng:i386 (0.3-2), libreoffice-ogltrans:i386 (4.2.3~rc3-0ubuntu2), libtelepathy-logger3:i386 (0.8.0-3), gir1.2-rb-3.0:i386 (3.0.2-0ubuntu2), folks-common:i386 (0.9.5-1ubuntu5), libqtcore4:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), friends:i386 (0.2.0+14.04.20140217.1-0ubuntu1), libpyzy-1.0-0:i386 (1.0.1-4), unity-scope-gdrive:i386 (0.9+13.10.20130723-0ubuntu1), gnome-video-effects:i386 (0.4.1-0ubuntu1), wamerican:i386 (7.1-1), apg:i386 (2.2.3.dfsg.1-2ubuntu1), libreoffice-presentation-minimizer:i386 (4.2.3~rc3-0ubuntu2), libcdio-paranoia1:i386 (0.83-4.1ubuntu1), libpurple0:i386 (2.10.9-0ubuntu3), libraw1394-11:i386 (2.1.0-1ubuntu1), geoclue-ubuntu-geoip:i386 (1.0.2+14.04.20131125-0ubuntu2), thunderbird-locale-en:i386 (24.5.0+build1-0ubuntu0.14.04.1), cheese-common:i386 (3.10.2-0ubuntu2), libdecoration0:i386 (0.9.11+14.04.20140409-0ubuntu1), signon-plugin-password:i386 (8.56+14.04.20140307-0ubuntu2), liblua5.2-0:i386 (5.2.3-1), libqt4-svg:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), libsndfile1:i386 (1.0.25-7ubuntu2), unity-scope-home:i386 (6.8.2+14.04.20131029.1-0ubuntu1), libqt5sql5-sqlite:i386 (5.2.1+dfsg-1ubuntu14), nautilus-share:i386 (0.7.3-1ubuntu5), libqt5svg5:i386 (5.2.1-1), libportaudio2:i386 (19+svn20140130-1), libqt4-opengl:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), notify-osd:i386 (0.9.35+14.04.20140213-0ubuntu1), libwps-0.2-2:i386 (0.2.9-2ubuntu1), xdg-user-dirs-gtk:i386 (0.10-1ubuntu1), qtcore4-l10n:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), xfonts-mathml:i386 (6ubuntu1), gnome-settings-daemon-schemas:i386 (3.8.6.1-0ubuntu11), ibus-gtk:i386 (1.5.5-1ubuntu3), gstreamer1.0-clutter:i386 (2.0.8-1build1), libgweather-3-6:i386 (3.10.2-0ubuntu1), friends-facebook:i386 (0.2.0+14.04.20140217.1-0ubuntu1), libqt4-scripttools:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), pulseaudio:i386 (4.0-0ubuntu11), unity-control-center:i386 (14.04.3+14.04.20140410-0ubuntu1), libqt4-help:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), update-notifier:i386 (0.154.1), libgstreamer-plugins-base1.0-0:i386 (1.2.3-1), gnome-terminal:i386 (3.6.2-0ubuntu1), nux-tools:i386 (4.0.6+14.04.20140409-0ubuntu1), xdiagnose:i386 (3.6.3build2), gir1.2-messagingmenu-1.0:i386 (13.10.1+14.04.20140410-0ubuntu1), gstreamer1.0-alsa:i386 (1.2.3-1), qtdeclarative5-ubuntu-ui-toolkit-plugin:i386 (0.1.46+14.04.20140408.1-0ubuntu1), libreoffice-impress:i386 (4.2.3~rc3-0ubuntu2), libopencv-contrib2.4:i386 (2.4.8+dfsg1-2ubuntu1), libpurple-bin:i386 (2.10.9-0ubuntu3), gnome-user-share:i386 (3.0.4-0ubuntu1), libfluidsynth1:i386 (1.1.6-2), plainbox-secure-policy:i386 (0.5.3-2), unity-scope-musicstores:i386 (6.9.0+13.10.20131011-0ubuntu1), qtdeclarative5-accounts-plugin:i386 (0.4+14.04.20140317-0ubuntu1), indicator-printers:i386 (0.1.7+14.04.20140313-0ubuntu1), libyelp0:i386 (3.10.2-0ubuntu1), unity-scope-texdoc:i386 (0.1+14.04.20140328-0ubuntu1), ure:i386 (4.2.3~rc3-0ubuntu2), libreoffice-help-en-us:i386 (4.2.3~rc3-0ubuntu1), unity-scope-video-remote:i386 (0.3.15+13.10.20130920-0ubuntu1), libebook-1.2-14:i386 (3.10.4-0ubuntu1), libgupnp-igd-1.0-4:i386 (0.2.2-1), remmina-plugin-vnc:i386 (1.0.0-4ubuntu3), gstreamer0.10-plugins-bad:i386 (0.10.23-7.2ubuntu1), liboxideqt-qmlplugin:i386 (1.0.0~bzr501-0ubuntu2), overlay-scrollbar-gtk2:i386 (0.2.16+r359+14.04.20131129-0ubuntu1), overlay-scrollbar-gtk3:i386 (0.2.16+r359+14.04.20131129-0ubuntu1), libcamel-1.2-45:i386 (3.10.4-0ubuntu1), libchromaprint0:i386 (1.1-1), indicator-datetime:i386 (13.10.0+14.04.20140415.3-0ubuntu1), telepathy-logger:i386 (0.8.0-3), brasero:i386 (3.10.0-0ubuntu1), libgoa-1.0-common:i386 (3.10.3-0ubuntu1), libfarstream-0.2-2:i386 (0.2.3-1ubuntu2), lp-solve:i386 (5.5.0.13-7build1), libavc1394-0:i386 (0.5.4-2), qtdeclarative5-window-plugin:i386 (5.2.1-3ubuntu15), telepathy-mission-control-5:i386 (5.16.1-1ubuntu3), libasyncns0:i386 (0.8-4ubuntu2), libqt5sql5:i386 (5.2.1+dfsg-1ubuntu14), zenity:i386 (3.8.0-1ubuntu1), gnomine:i386 (3.10.1-0ubuntu1), compiz:i386 (0.9.11+14.04.20140409-0ubuntu1), unity-scopes-runner:i386 (7.1.4+14.04.20140210-0ubuntu1), libgssdp-1.0-3:i386 (0.14.7-1ubuntu1), libfolks25:i386 (0.9.5-1ubuntu5), evolution-data-server:i386 (3.10.4-0ubuntu1), libreoffice-pdfimport:i386 (4.2.3~rc3-0ubuntu2), libvisio-0.0-0:i386 (0.0.31-1ubuntu2), onboard-data:i386 (1.0.0-0ubuntu4), python3-checkbox-support:i386 (0.2-1), rhythmbox-plugin-magnatune:i386 (3.0.2-0ubuntu2), speech-dispatcher-audio-plugins:i386 (0.8-5ubuntu1), gir1.2-gst-plugins-base-1.0:i386 (1.2.3-1), gstreamer0.10-pulseaudio:i386 (0.10.31-3+nmu1ubuntu5), libgstreamer-plugins-good1.0-0:i386 (1.2.3-1ubuntu2), libmhash2:i386 (0.9.9.9-4), libqt5qml5:i386 (5.2.1-3ubuntu15), libbrasero-media3-1:i386 (3.10.0-0ubuntu1), rhythmbox-plugin-cdrecorder:i386 (3.0.2-0ubuntu2), indicator-power:i386 (12.10.6+14.04.20140411-0ubuntu1), gstreamer1.0-plugins-base-apps:i386 (1.2.3-1), gstreamer1.0-tools:i386 (1.2.3-1), libexttextcat-2.0-0:i386 (3.4.3-1ubuntu1), libxcb-randr0:i386 (1.10-2ubuntu1), python3-feedparser:i386 (5.1.3-2), thunderbird:i386 (24.5.0+build1-0ubuntu0.14.04.1), whoopsie-preferences:i386 (0.12), qdbus:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), libmetacity-private0a:i386 (2.34.13-0ubuntu4), gnome-font-viewer:i386 (3.8.0-1build1), rhythmbox-mozilla:i386 (3.0.2-0ubuntu2), libmission-control-plugins0:i386 (5.16.1-1ubuntu3), python3-mako:i386 (0.9.1-1), libaccounts-qt5-1:i386 (1.11+14.04.20140410.1-0ubuntu1), libexttextcat-data:i386 (3.4.3-1ubuntu1), account-plugin-yahoo:i386 (3.8.6-0ubuntu9.1), gstreamer1.0-pulseaudio:i386 (1.2.3-1ubuntu2), gstreamer0.10-plugins-ugly:i386 (0.10.19-2ubuntu5), libpwquality1:i386 (1.2.3-1ubuntu1), ubuntu-session:i386 (3.9.90-0ubuntu12), libsignon-qt5-1:i386 (8.56+14.04.20140307-0ubuntu2), libqt4-designer:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), libqtassistantclient4:i386 (4.6.3-6), eog:i386 (3.10.2-0ubuntu5), unity-webapps-common:i386 (2.4.17+14.04.20140416-0ubuntu1), fonts-nanum:i386 (20131007-1), unity-lens-video:i386 (0.3.15+13.10.20130920-0ubuntu1), friends-dispatcher:i386 (0.2.0+14.04.20140217.1-0ubuntu1), libgtop2-7:i386 (2.28.5-2), libunity-webapps0:i386 (2.5.0~+14.04.20140409-0ubuntu1), activity-log-manager-control-center:i386 (0.9.7-0ubuntu14), unity-webapps-qml:i386 (0.1+14.04.20140408-0ubuntu1), checkbox-gui:i386 (0.17.6-0ubuntu6), example-content:i386 (48), appmenu-qt5:i386 (0.3.0+14.04.20140415-0ubuntu1), liboauth0:i386 (1.0.1-1), libqt5network5:i386 (5.2.1+dfsg-1ubuntu14), gir1.2-gdata-0.0:i386 (0.14.1-1), mousetweaks:i386 (3.8.0-2), libtimezonemap1:i386 (0.4.1), indicator-sound:i386 (12.10.2+14.04.20140401-0ubuntu1), libglew1.10:i386 (1.10.0-3), libhud2:i386 (13.10.1+14.04.20140402-0ubuntu1), account-plugin-jabber:i386 (3.8.6-0ubuntu9.1), libgstreamer-plugins-base0.10-0:i386 (0.10.36-1.1ubuntu2), baobab:i386 (3.8.2-1ubuntu1), libcurl3:i386 (7.35.0-1ubuntu2), hwdata:i386 (0.249-1), libogg0:i386 (1.3.1-1ubuntu1), ubuntu-wallpapers-trusty:i386 (14.04.0.1-0ubuntu1), gnome-session-common:i386 (3.9.90-0ubuntu12), notify-osd-icons:i386 (0.8+14.04.20131204-0ubuntu1), libopencv-objdetect2.4:i386 (2.4.8+dfsg1-2ubuntu1), qt-at-spi:i386 (0.3.1-4fakesync1), libqt5feedback5:i386 (5.0~git20130529-0ubuntu3), mcp-account-manager-uoa:i386 (3.8.6-0ubuntu9.1), cheese:i386 (3.10.2-0ubuntu2), unity-scope-gourmet:i386 (0.1+13.10.20130723-0ubuntu1), unity:i386 (7.2.0+14.04.20140423-0ubuntu1.2), libprotobuf8:i386 (2.5.0-9ubuntu1), libreoffice-math:i386 (4.2.3~rc3-0ubuntu2), gstreamer1.0-plugins-ugly:i386 (1.2.3-2build1), liborc-0.4-0:i386 (0.4.18-1ubuntu1), libqt5quick5:i386 (5.2.1-3ubuntu15), media-player-info:i386 (21-0ubuntu1), qtdeclarative5-dialogs-plugin:i386 (5.2.1-3ubuntu15), aisleriot:i386 (3.10.2-1), libqt5widgets5:i386 (5.2.1+dfsg-1ubuntu14), libreoffice-calc:i386 (4.2.3~rc3-0ubuntu2), libpwquality-common:i386 (1.2.3-1ubuntu1), libraptor2-0:i386 (2.0.13-1), libunity-core-6.0-9:i386 (7.2.0+14.04.20140423-0ubuntu1.2), libwmf0.2-7:i386 (0.2.8.4-10.3ubuntu1), libwebkitgtk-3.0-0:i386 (2.4.0-1ubuntu2), libtotem0:i386 (3.10.1-1ubuntu4), libqt5multimedia5:i386 (5.2.1-0ubuntu5), libgdata13:i386 (0.14.1-1), gnome-contacts:i386 (3.8.3-1ubuntu1), python-qt4-dbus:i386 (4.10.4+dfsg-1ubuntu1), gstreamer0.10-plugins-good:i386 (0.10.31-3+nmu1ubuntu5), libqt4-dbus:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), dconf-cli:i386 (0.20.0-1), libunity-misc4:i386 (4.0.5+14.04.20140115-0ubuntu1), libfarstream-0.1-0:i386 (0.1.2-1ubuntu3), libespeak1:i386 (1.47.11-1ubuntu1), gnome-session-bin:i386 (3.9.90-0ubuntu12), libqt5xml5:i386 (5.2.1+dfsg-1ubuntu14), gir1.2-ebookcontacts-1.2:i386 (3.10.4-0ubuntu1), unity-scope-firefoxbookmarks:i386 (0.1+13.10.20130809.1-0ubuntu1), libboost-date-time1.54.0:i386 (1.54.0-4ubuntu3), libvorbisfile3:i386 (1.3.2-1.3ubuntu1), unity-webapps-service:i386 (2.5.0~+14.04.20140409-0ubuntu1), webaccounts-extension-common:i386 (0.5-0ubuntu2), unity-services:i386 (7.2.0+14.04.20140423-0ubuntu1.2), libedata-book-1.2-20:i386 (3.10.4-0ubuntu1), compiz-gnome:i386 (0.9.11+14.04.20140409-0ubuntu1), nautilus:i386 (3.10.1-0ubuntu9), libebook-contacts-1.2-0:i386 (3.10.4-0ubuntu1), liblangtag-common:i386 (0.5.1-2), unity-scope-colourlovers:i386 (0.1+13.10.20130723-0ubuntu1), libunity-control-center1:i386 (14.04.3+14.04.20140410-0ubuntu1), libqt5organizer5:i386 (5.0~git20140203~e0c5eebe-0ubuntu2), unity-scope-clementine:i386 (0.1+13.10.20130723-0ubuntu1), session-migration:i386 (0.2.1), unity-scope-virtualbox:i386 (0.1+13.10.20130723-0ubuntu1), telepathy-indicator:i386 (0.3.1+14.04.20140411-0ubuntu1), unity-scopes-master-default:i386 (6.8.2+14.04.20131029.1-0ubuntu1), plymouth-theme-ubuntu-logo:i386 (0.8.8-0ubuntu17), python-qt4:i386 (4.10.4+dfsg-1ubuntu1), gnome-mines:i386 (3.10.1-0ubuntu1), ubuntu-release-upgrader-gtk:i386 (0.220.2), unity-lens-applications:i386 (7.1.0+13.10.20131011-0ubuntu2), rhythmbox:i386 (3.0.2-0ubuntu2), gstreamer1.0-plugins-good:i386 (1.2.3-1ubuntu2), libgdata-common:i386 (0.14.1-1), libdc1394-22:i386 (2.2.1-2ubuntu2), libqtdbus4:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), unity-lens-music:i386 (6.9.0+13.10.20131011-0ubuntu1), unity-scope-openclipart:i386 (0.1+13.10.20130723-0ubuntu1), libqt5qml-graphicaleffects:i386 (5.2.1-1), gir1.2-networkmanager-1.0:i386 (0.9.8.8-0ubuntu7), libqt5opengl5:i386 (5.2.1+dfsg-1ubuntu14), rhythmbox-data:i386 (3.0.2-0ubuntu2), unity-gtk-module-common:i386 (0.0.0+14.04.20140403-0ubuntu1), indicator-appmenu:i386 (13.01.0+14.04.20140404-0ubuntu1), libopencv-legacy2.4:i386 (2.4.8+dfsg1-2ubuntu1), libaccount-plugin-google:i386 (0.11+14.04.20140409.1-0ubuntu1), sphinx-voxforge-lm-en:i386 (0.1.1~daily20130301-0ubuntu1), gnome-mahjongg:i386 (3.10.2-0ubuntu1), libfreerdp-plugins-standard:i386 (1.0.2-2ubuntu1), remmina:i386 (1.0.0-4ubuntu3), unity-scope-gmusicbrowser:i386 (0.1+13.10.20130723-0ubuntu1), evolution-data-server-common:i386 (3.10.4-0ubuntu1), unity-gtk2-module:i386 (0.0.0+14.04.20140403-0ubuntu1), ethtool:i386 (3.13-1), libopencc1:i386 (0.4.3-2build1), libnux-4.0-common:i386 (4.0.6+14.04.20140409-0ubuntu1), nautilus-sendto:i386 (3.6.1-2ubuntu1), libexempi3:i386 (2.2.1-1ubuntu1), update-manager:i386 (0.196.12), unity-scope-devhelp:i386 (0.1+14.04.20140328-0ubuntu1), appmenu-qt:i386 (0.2.7+14.04.20140305-0ubuntu1), libwmf0.2-7-gtk:i386 (0.2.8.4-10.3ubuntu1), ubuntu-wallpapers:i386 (14.04.0.1-0ubuntu1), gtk3-engines-unico:i386 (1.0.3+14.04.20140109-0ubuntu1), libmeanwhile1:i386 (1.0.2-4.1ubuntu1), libunity-action-qt1:i386 (1.1.0+14.04.20140304-0ubuntu1), totem-mozilla:i386 (3.10.1-1ubuntu4), cups-pk-helper:i386 (0.2.5-0ubuntu1), libcompizconfig0:i386 (0.9.11+14.04.20140409-0ubuntu1), deja-dup-backend-gvfs:i386 (30.0-0ubuntu4), libcheese-gtk23:i386 (3.10.2-0ubuntu2), libiec61883-0:i386 (1.2.0-0.1ubuntu3), qtchooser:i386 (39-g4717841-3), libcanberra-pulse:i386 (0.30-0ubuntu3), activity-log-manager:i386 (0.9.7-0ubuntu14), libcanberra-gtk3-0:i386 (0.30-0ubuntu3), librdf0:i386 (1.0.17-1), libfolks-eds25:i386 (0.9.5-1ubuntu5), libsphinxbase1:i386 (0.8-0ubuntu10), libaccount-plugin-generic-oauth:i386 (0.11+14.04.20140409.1-0ubuntu1), libqt4-network:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), unity-scope-guayadeque:i386 (0.1+13.10.20130927.1-0ubuntu1), uno-libs3:i386 (4.2.3~rc3-0ubuntu2), unity-scope-tomboy:i386 (0.1+13.10.20130723-0ubuntu1), xul-ext-webaccounts:i386 (0.5-0ubuntu2), account-plugin-google:i386 (0.11+14.04.20140409.1-0ubuntu1), libqt4-script:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), gir1.2-accounts-1.0:i386 (1.15+14.04.20131126.2-0ubuntu3), vino:i386 (3.8.1-0ubuntu1), plainbox-provider-checkbox:i386 (0.4-1), pm-utils:i386 (1.4.1-13), ibus-table:i386 (1.5.0.is.1.5.0.20130419-2), libcdr-0.0-0:i386 (0.0.15-1ubuntu1), totem:i386 (3.10.1-1ubuntu4), libslv2-9:i386 (0.6.6+dfsg1-2), account-plugin-salut:i386 (3.8.6-0ubuntu9.1), python3-urllib3:i386 (1.7.1-1build1), xul-ext-unity:i386 (3.0.0+14.04.20140416-0ubuntu1), gnome-bluetooth:i386 (3.8.2.1-0ubuntu4), libgles2-mesa:i386 (10.1.0-4ubuntu5), libhyphen0:i386 (2.8.6-3ubuntu2), libpulsedsp:i386 (4.0-0ubuntu11), libgnomekbd8:i386 (3.6.0-0ubuntu2), libgnomekbd-common:i386 (3.6.0-0ubuntu2), qtdeclarative5-ubuntu-ui-extras-browser-plugin:i386 (0.23+14.04.20140422-0ubuntu1), gir1.2-appindicator3-0.1:i386 (12.10.1+13.10.20130920-0ubuntu4), libqtwebkit4:i386 (2.3.2-0ubuntu7), unity-lens-friends:i386 (0.1.3+14.04.20140317-0ubuntu1), libaccount-plugin-1.0-0:i386 (0.1.7~+14.04.20140211.2-0ubuntu4), libupstart1:i386 (1.12.1-0ubuntu4), metacity-common:i386 (2.34.13-0ubuntu4), libgee2:i386 (0.6.8-1ubuntu1), qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets:i386 (0.23+14.04.20140422-0ubuntu1), indicator-keyboard:i386 (0.0.0+14.04.20140410.1-0ubuntu1), unity-scope-audacious:i386 (0.1+13.10.20130927.1-0ubuntu1), gstreamer0.10-nice:i386 (0.1.4-1), libspeex1:i386 (1.2~rc1.1-1ubuntu1), gnome-system-log:i386 (3.8.1-1svn1), empathy:i386 (3.8.6-0ubuntu9.1), libgtop2-common:i386 (2.28.5-2), python-ibus:i386 (1.5.5-1ubuntu3), shotwell:i386 (0.18.0-0ubuntu4), unity-scope-zotero:i386 (0.1+13.10.20130723-0ubuntu1), bamfdaemon:i386 (0.5.1+14.04.20140409-0ubuntu1), ibus:i386 (1.5.5-1ubuntu3), libcolamd2.8.0:i386 (4.2.1-3ubuntu1), rhythmbox-plugin-zeitgeist:i386 (3.0.2-0ubuntu2), gnome-screensaver:i386 (3.6.1-0ubuntu13), libwpd-0.9-9:i386 (0.9.9-1), account-plugin-flickr:i386 (0.11+14.04.20140409.1-0ubuntu1), brasero-cdrkit:i386 (3.10.0-0ubuntu1), landscape-client-ui-install:i386 (14.01-0ubuntu3), libufe-xidgetter0:i386 (3.0.0+14.04.20140416-0ubuntu1), signon-keyring-extension:i386 (0.6+14.04.20140307-0ubuntu1), libcanberra-gtk3-module:i386 (0.30-0ubuntu3), libqt5webkit5-qmlwebkitplugin:i386 (5.1.1-1ubuntu8), guile-2.0-libs:i386 (2.0.9+1-1ubuntu1), signond:i386 (8.56+14.04.20140307-0ubuntu2), libgnome-desktop-3-7:i386 (3.8.4-0ubuntu3), libfriends0:i386 (0.1.2+14.04.20131108.1-0ubuntu1), librsync1:i386 (0.9.7-10), libclucene-contribs1:i386 (2.3.3.4-4build1), libreoffice-draw:i386 (4.2.3~rc3-0ubuntu2), gnome-screenshot:i386 (3.10.1-0ubuntu1), gir1.2-edataserver-1.2:i386 (3.10.4-0ubuntu1), ubuntuone-client-data:i386 (13.05-0ubuntu1), unity-control-center-signon:i386 (0.1.7~+14.04.20140211.2-0ubuntu4), totem-plugins:i386 (3.10.1-1ubuntu4), libreoffice-base-core:i386 (4.2.3~rc3-0ubuntu2), libx86-1:i386 (1.1+ds1-10), libclutter-gst-2.0-0:i386 (2.0.8-1build1), libsignon-extension1:i386 (8.56+14.04.20140307-0ubuntu2), libvorbis0a:i386 (1.3.2-1.3ubuntu1), libqt5printsupport5:i386 (5.2.1+dfsg-1ubuntu14), signon-ui:i386 (0.16+14.04.20140304.is.0.15+14.04.20140313-0ubuntu1), indicator-bluetooth:i386 (0.0.6+14.04.20140207-0ubuntu2), libibus-1.0-5:i386 (1.5.5-1ubuntu3), nautilus-sendto-empathy:i386 (3.8.6-0ubuntu9.1), gstreamer0.10-x:i386 (0.10.36-1.1ubuntu2), libcrack2:i386 (2.9.1-1build1), libgpod-common:i386 (0.8.3-4ubuntu3), libreoffice-core:i386 (4.2.3~rc3-0ubuntu2), gnome-sudoku:i386 (3.10.2-0ubuntu2), liblangtag1:i386 (0.5.1-2), libqt5test5:i386 (5.2.1+dfsg-1ubuntu14), libjack-jackd2-0:i386 (1.9.9.5+20130622git7de15e7a-1ubuntu1), gir1.2-goa-1.0:i386 (3.10.3-0ubuntu1), libcanberra0:i386 (0.30-0ubuntu3), empathy-common:i386 (3.8.6-0ubuntu9.1), checkbox-ng-service:i386 (0.3-2), qtdeclarative5-unity-action-plugin:i386 (1.1.0+14.04.20140304-0ubuntu1), indicator-session:i386 (12.10.5+14.04.20140410-0ubuntu1), libcolumbus1-common:i386 (1.1.0+14.04.20140325.3-0ubuntu1), unity-greeter:i386 (14.04.10-0ubuntu1), evolution-data-server-online-accounts:i386 (3.10.4-0ubuntu1), gstreamer1.0-plugins-bad-videoparsers:i386 (1.2.3-1ubuntu2), libebackend-1.2-7:i386 (3.10.4-0ubuntu1), onboard:i386 (1.0.0-0ubuntu4), plainbox-provider-resource-generic:i386 (0.3-1), sphinx-voxforge-hmm-en:i386 (0.1.1~daily20130301-0ubuntu1), libdmapsharing-3.0-2:i386 (2.9.24-0ubuntu1), gnome-session-canberra:i386 (0.30-0ubuntu3), libmythes-1.2-0:i386 (1.2.2-1ubuntu2), libwhoopsie-preferences0:i386 (0.12), gnome-user-guide:i386 (3.8.2-1), compiz-core:i386 (0.9.11+14.04.20140409-0ubuntu1), libvncserver0:i386 (0.9.9+dfsg-1ubuntu1), libwhoopsie0:i386 (0.2.24.5), libwacom2:i386 (0.8-1), libgupnp-1.0-4:i386 (0.20.10-1ubuntu1), libsbc1:i386 (1.1-2ubuntu2), ubuntu-docs:i386 (14.04.3), libcmis-0.4-4:i386 (0.4.1-3ubuntu4), apturl-common:i386 (0.5.2ubuntu4), libnice10:i386 (0.1.4-1), remmina-common:i386 (1.0.0-4ubuntu3), webbrowser-app:i386 (0.23+14.04.20140422-0ubuntu1), libsignon-plugins-common1:i386 (8.56+14.04.20140307-0ubuntu2), libqt4-xmlpatterns:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), libunityvoice1:i386 (0.1+14.04.20140304-0ubuntu1), libqt5gui5:i386 (5.2.1+dfsg-1ubuntu14), gir1.2-totem-1.0:i386 (3.10.1-1ubuntu4), ibus-gtk3:i386 (1.5.5-1ubuntu3), vbetool:i386 (1.1-3), libgnome-control-center1:i386 (3.6.3-0ubuntu56), gir1.2-webkit-3.0:i386 (2.4.0-1ubuntu2), qtdeclarative5-localstorage-plugin:i386 (5.2.1-3ubuntu15), libpulse0:i386 (4.0-0ubuntu11), remmina-plugin-rdp:i386 (1.0.0-4ubuntu3), unity-lens-photos:i386 (1.0+14.04.20140318-0ubuntu1), unity-voice-service:i386 (0.1+14.04.20140304-0ubuntu1), geoclue:i386 (0.12.99-3ubuntu1), branding-ubuntu:i386 (0.8), libqtgui4:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), libwacom-common:i386 (0.8-1), libqt5core5a:i386 (5.2.1+dfsg-1ubuntu14), sni-qt:i386 (0.2.6-0ubuntu1), libzephyr4:i386 (3.1.2-1), friends-twitter:i386 (0.2.0+14.04.20140217.1-0ubuntu1), libxcb-image0:i386 (0.3.9-1ubuntu2), python3-uno:i386 (4.2.3~rc3-0ubuntu2), libgc1c2:i386 (7.2d-5ubuntu2), hud:i386 (13.10.1+14.04.20140402-0ubuntu1), liborcus-0.6-0:i386 (0.5.1-7), ubuntu-ui-toolkit-theme:i386 (0.1.46+14.04.20140408.1-0ubuntu1), python3-plainbox:i386 (0.5.3-2), libqt4-declarative:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), libproxy1-plugin-networkmanager:i386 (0.4.11-0ubuntu4), obexd-client:i386 (0.46-1ubuntu7), gir1.2-gnomekeyring-1.0:i386 (3.8.0-2), gstreamer0.10-plugins-base:i386 (0.10.36-1.1ubuntu2), libgoa-1.0-0b:i386 (3.10.3-0ubuntu1), gkbd-capplet:i386 (3.6.0-0ubuntu2), libgweather-common:i386 (3.10.2-0ubuntu1), python3-requests:i386 (2.2.1-1), libgsettings-qt1:i386 (0.1+14.04.20140408-0ubuntu1), compiz-plugins-default:i386 (0.9.11+14.04.20140409-0ubuntu1), libxcb-icccm4:i386 (0.4.1-1ubuntu1), libgstreamer-plugins-bad0.10-0:i386 (0.10.23-7.2ubuntu1), libqt5positioning5:i386 (5.2.1-1ubuntu2), gir1.2-signon-1.0:i386 (1.10daily13.06.25-0ubuntu2), account-plugin-windows-live:i386 (0.11+14.04.20140409.1-0ubuntu1), whoopsie:i386 (0.2.24.5), libcdio-cdda1:i386 (0.83-4.1ubuntu1), python-lockfile:i386 (0.8-2ubuntu2), ubuntu-sso-client-qt:i386 (13.10-0ubuntu6), libopencv-highgui2.4:i386 (2.4.8+dfsg1-2ubuntu1), libshout3:i386 (2.3.1-3), telepathy-salut:i386 (0.8.1-1ubuntu3), duplicity:i386 (0.6.23-1ubuntu4), python3-lxml:i386 (3.3.3-1), libtelepathy-farstream3:i386 (0.6.1-0ubuntu1), unity-asset-pool:i386 (0.8.24daily13.06.10-0ubuntu1), libsystemd-journal0:i386 (204-5ubuntu20), libproxy1-plugin-gsettings:i386 (0.4.11-0ubuntu4), python-sip:i386 (4.15.5-1build1), libqt4-test:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), qtdeclarative5-privatewidgets-plugin:i386 (5.2.1-3ubuntu15), gstreamer0.10-alsa:i386 (0.10.36-1.1ubuntu2), libwpg-0.2-2:i386 (0.2.2-1ubuntu1), python3-checkbox-ng:i386 (0.3-2), libboost-system1.54.0:i386 (1.54.0-4ubuntu3), libcanberra-gtk0:i386 (0.30-0ubuntu3), libfolks-telepathy25:i386 (0.9.5-1ubuntu5), thunderbird-gnome-support:i386 (24.5.0+build1-0ubuntu0.14.04.1), light-themes:i386 (14.04+14.04.20140410-0ubuntu1), gstreamer1.0-plugins-bad-faad:i386 (1.2.3-1ubuntu2), libreoffice-gnome:i386 (4.2.3~rc3-0ubuntu2), libzeitgeist-1.0-1:i386 (0.3.18-1ubuntu2), libreoffice-avmedia-backend-gstreamer:i386 (4.2.3~rc3-0ubuntu2), unity-scope-calculator:i386 (0.1+14.04.20140328-0ubuntu1), libcdio13:i386 (0.83-4.1ubuntu1), ubuntu-system-service:i386 (0.2.5build1), pulseaudio-module-x11:i386 (4.0-0ubuntu11), gstreamer1.0-plugins-base:i386 (1.2.3-1), gnome-power-manager:i386 (3.8.2-1ubuntu2), gstreamer1.0-nice:i386 (0.1.4-1), mythes-en-us:i386 (4.2.1-0ubuntu1), libreoffice-style-human:i386 (4.2.3~rc3-0ubuntu2), ubuntu-mono:i386 (14.04+14.04.20140410-0ubuntu1), libcolumbus1:i386 (1.1.0+14.04.20140325.3-0ubuntu1), libbamf3-2:i386 (0.5.1+14.04.20140409-0ubuntu1), software-center:i386 (13.10-0ubuntu4.1), apturl:i386 (0.5.2ubuntu4), gir1.2-ibus-1.0:i386 (1.5.5-1ubuntu3), ibus-pinyin:i386 (1.5.0-1ubuntu1), unity-scope-chromiumbookmarks:i386 (0.1+13.10.20130723-0ubuntu1), ubuntu-desktop:i386 (1.325), libcheese7:i386 (3.10.2-0ubuntu2), libaudio2:i386 (1.9.4-1), libreoffice-writer:i386 (4.2.3~rc3-0ubuntu2), speech-dispatcher:i386 (0.8-5ubuntu1), gnome-control-center-shared-data:i386 (3.6.3-0ubuntu56), unity-scope-musique:i386 (0.1+13.10.20130723-0ubuntu1), libqt4-xml:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), pulseaudio-module-bluetooth:i386 (4.0-0ubuntu11), libvorbisenc2:i386 (1.3.2-1.3ubuntu1), libtheora0:i386 (1.1.1+dfsg.1-3.2), libqt5dbus5:i386 (5.2.1+dfsg-1ubuntu14), libecal-1.2-16:i386 (3.10.4-0ubuntu1), libclucene-core1:i386 (2.3.3.4-4build1), gstreamer1.0-x:i386 (1.2.3-1), librasqal3:i386 (0.9.32-1), libxcb-xkb1:i386 (1.10-2ubuntu1), libyajl2:i386 (2.0.4-4), gir1.2-secret-1:i386 (0.16-0ubuntu1), gstreamer1.0-libav:i386 (1.2.3-1), libnux-4.0-0:i386 (4.0.6+14.04.20140409-0ubuntu1), libpulse-mainloop-glib0:i386 (4.0-0ubuntu11), adium-theme-ubuntu:i386 (0.3.4-0ubuntu1), deja-dup:i386 (30.0-0ubuntu4), seahorse:i386 (3.10.2-0ubuntu1), account-plugin-facebook:i386 (0.11+14.04.20140409.1-0ubuntu1), unity-scope-manpages:i386 (3.0+14.04.20140324-0ubuntu1), libasound2-plugins:i386 (1.0.27-2ubuntu2), yelp:i386 (3.10.2-0ubuntu1), qtdeclarative5-qtquick2-plugin:i386 (5.2.1-3ubuntu15), gnome-desktop3-data:i386 (3.8.4-0ubuntu3), account-plugin-twitter:i386 (0.11+14.04.20140409.1-0ubuntu1), libthumbnailer0:i386 (1.1+14.04.20140401.1-0ubuntu1), libreoffice-gtk:i386 (4.2.3~rc3-0ubuntu2), gir1.2-ebook-1.2:i386 (3.10.4-0ubuntu1), libavformat54:i386 (9.13-0ubuntu0.14.04.1), libmspub-0.0-0:i386 (0.0.6-1ubuntu2), python3-pyparsing:i386 (2.0.1+dfsg1-1build1), libglewmx1.10:i386 (1.10.0-3), librhythmbox-core8:i386 (3.0.2-0ubuntu2), libxcb-render-util0:i386 (0.3.8-1.1ubuntu1), gnome-disk-utility:i386 (3.10.0-1ubuntu3), libedataserver-1.2-18:i386 (3.10.4-0ubuntu1), signon-plugin-oauth2:i386 (0.19+14.04.20140305-0ubuntu2), libssh-4:i386 (0.6.1-0ubuntu3), libunity-gtk3-parser0:i386 (0.0.0+14.04.20140403-0ubuntu1), pulseaudio-utils:i386 (4.0-0ubuntu11), overlay-scrollbar:i386 (0.2.16+r359+14.04.20131129-0ubuntu1), libavcodec54:i386 (9.13-0ubuntu0.14.04.1), libunity-gtk2-parser0:i386 (0.0.0+14.04.20140403-0ubuntu1), libqt5sensors5:i386 (5.2.1+dfsg-2ubuntu2), gnome-system-monitor:i386 (3.8.2.1-2ubuntu1), intel-gpu-tools:i386 (1.3-0ubuntu2), gvfs-backends:i386 (1.20.1-1ubuntu1), libqt4-sql:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), libdbusmenu-qt2:i386 (0.9.3+14.04.20140314-0ubuntu1), libdbusmenu-qt5:i386 (0.9.3+14.04.20140314-0ubuntu1), libedata-cal-1.2-23:i386 (3.10.4-0ubuntu1), libgpod4:i386 (0.8.3-4ubuntu3), thunderbird-locale-en-us:i386 (24.5.0+build1-0ubuntu0.14.04.1), unity-lens-files:i386 (7.1.0+13.10.20130920-0ubuntu1), telepathy-gabble:i386 (0.18.2-1), libcanberra-gtk-module:i386 (0.30-0ubuntu3), xul-ext-websites-integration:i386 (2.3.6+13.10.20130920.1-0ubuntu1), account-plugin-aim:i386 (3.8.6-0ubuntu9.1), gnome-terminal-data:i386 (3.6.2-0ubuntu1), webapp-container:i386 (0.23+14.04.20140422-0ubuntu1), telepathy-haze:i386 (0.8.0-1), ubuntu-artwork:i386 (14.04+14.04.20140410-0ubuntu1), libqt4-sql-sqlite:i386 (4.8.5+git192-g085f851+dfsg-2ubuntu4), libschroedinger-1.0-0:i386 (1.0.11-2ubuntu1), gstreamer1.0-plugins-bad:i386 (1.2.3-1ubuntu2), libqt5webkit5:i386 (5.1.1-1ubuntu8), rhythmbox-plugins:i386 (3.0.2-0ubuntu2), telepathy-idle:i386 (0.2.0-1), qtdeclarative5-qtfeedback-plugin:i386 (5.0~git20130529-0ubuntu3), liboxideqtcore0:i386 (1.0.0~bzr501-0ubuntu2), ubuntu-sounds:i386 (0.13)
End-Date: 2014-05-11  21:50:13

```

I then followed up by running "tasksel install ubuntu-gnome-desktop' in the same TTY:

```
Start-Date: 2014-05-11  22:18:44
Commandline: apt-get -o APT::Status-Fd=4 -o APT::Keep-Fds::=5 -o APT::Keep-Fds::=6 -q -y install ubuntu-gnome-desktop^
Install: libreoffice-common:i386 (4.2.3~rc3-0ubuntu2), cracklib-runtime:i386 (2.9.1-1build1), gir1.2-gnomebluetooth-1.0:i386 (3.8.2.1-0ubuntu4), python3-markupsafe:i386 (0.18-1build2), gir1.2-upowerglib-1.0:i386 (0.9.23-2ubuntu1), libtracker-extract-0.16-0:i386 (0.16.2-1ubuntu4.1), libsgutils2-2:i386 (1.36-1ubuntu1), libgtkhtml-4.0-common:i386 (4.6.6-2ubuntu1), libflac8:i386 (1.3.0-2), libreoffice-ogltrans:i386 (4.2.3~rc3-0ubuntu2), libtelepathy-logger3:i386 (0.8.0-3), gir1.2-rb-3.0:i386 (3.0.2-0ubuntu2), libpst4:i386 (0.6.59-1build1), gir1.2-telepathylogger-0.2:i386 (0.8.0-3), folks-common:i386 (0.9.5-1ubuntu5), gnome-control-center:i386 (3.6.3-0ubuntu56), libpyzy-1.0-0:i386 (1.0.1-4), gnome-video-effects:i386 (0.4.1-0ubuntu1), wamerican:i386 (7.1-1), apg:i386 (2.2.3.dfsg.1-2ubuntu1), libtracker-sparql-0.16-0:i386 (0.16.2-1ubuntu4.1), libreoffice-presentation-minimizer:i386 (4.2.3~rc3-0ubuntu2), libcdio-paranoia1:i386 (0.83-4.1ubuntu1), libpurple0:i386 (2.10.9-0ubuntu3), libraw1394-11:i386 (2.1.0-1ubuntu1), libtracker-miner-0.16-0:i386 (0.16.2-1ubuntu4.1), cheese-common:i386 (3.10.2-0ubuntu2), liblua5.2-0:i386 (5.2.3-1), mcp-account-manager-goa:i386 (3.8.6-0ubuntu9.1), gnome-sushi:i386 (3.11.90-0ubuntu1), libsndfile1:i386 (1.0.25-7ubuntu2), libsys-hostname-long-perl:i386 (1.4-3), nautilus-share:i386 (0.7.3-1ubuntu5), libportaudio2:i386 (19+svn20140130-1), libwps-0.2-2:i386 (0.2.9-2ubuntu1), ubuntu-gnome-desktop:i386 (0.32), liblwp-mediatypes-perl:i386 (6.02-1), xdg-user-dirs-gtk:i386 (0.10-1ubuntu1), xfonts-mathml:i386 (6ubuntu1), gnome-settings-daemon-schemas:i386 (3.8.6.1-0ubuntu11), evolution-indicator:i386 (0.2.20-0ubuntu15), libfont-afm-perl:i386 (1.20-1), ibus-gtk:i386 (1.5.5-1ubuntu3), gstreamer1.0-clutter:i386 (2.0.8-1build1), libgweather-3-6:i386 (3.10.2-0ubuntu1), pulseaudio:i386 (4.0-0ubuntu11), update-notifier:i386 (0.154.1), libgstreamer-plugins-base1.0-0:i386 (1.2.3-1), libhtml-form-perl:i386 (6.03-1), gnome-terminal:i386 (3.6.2-0ubuntu1), gir1.2-gcr-3:i386 (3.10.1-1), xdiagnose:i386 (3.6.3build2), gstreamer1.0-alsa:i386 (1.2.3-1), libreoffice-impress:i386 (4.2.3~rc3-0ubuntu2), libpurple-bin:i386 (2.10.9-0ubuntu3), gnome-user-share:i386 (3.0.4-0ubuntu1), gnome-control-center-data:i386 (3.6.3-0ubuntu56), libhttp-message-perl:i386 (6.06-1), libyelp0:i386 (3.10.2-0ubuntu1), ure:i386 (4.2.3~rc3-0ubuntu2), gir1.2-gdesktopenums-3.0:i386 (3.10.1-0ubuntu1), libebook-1.2-14:i386 (3.10.4-0ubuntu1), libgupnp-igd-1.0-4:i386 (0.2.2-1), gnome-documents:i386 (3.10.2-0ubuntu1), libcamel-1.2-45:i386 (3.10.4-0ubuntu1), telepathy-logger:i386 (0.8.0-3), brasero:i386 (3.10.0-0ubuntu1), libgoa-1.0-common:i386 (3.10.3-0ubuntu1), gnome-color-manager:i386 (3.8.3-1ubuntu1), libfarstream-0.2-2:i386 (0.2.3-1ubuntu2), lp-solve:i386 (5.5.0.13-7build1), evolution-common:i386 (3.10.4-0ubuntu1), libavc1394-0:i386 (0.5.4-2), telepathy-mission-control-5:i386 (5.16.1-1ubuntu3), spamc:i386 (3.4.0-1ubuntu1), tracker:i386 (0.16.2-1ubuntu4.1), libasyncns0:i386 (0.8-4ubuntu2), zenity:i386 (3.8.0-1ubuntu1), libfile-listing-perl:i386 (6.04-1), libreoffice-style-tango:i386 (4.2.3~rc3-0ubuntu2), libgssdp-1.0-3:i386 (0.14.7-1ubuntu1), libfolks25:i386 (0.9.5-1ubuntu5), evolution-data-server:i386 (3.10.4-0ubuntu1), libreoffice-pdfimport:i386 (4.2.3~rc3-0ubuntu2), gnome-themes-standard:i386 (3.10.0-1ubuntu2), libvisio-0.0-0:i386 (0.0.31-1ubuntu2), gir1.2-clutter-1.0:i386 (1.16.4-0ubuntu2), rhythmbox-plugin-magnatune:i386 (3.0.2-0ubuntu2), gir1.2-evince-3.0:i386 (3.10.3-0ubuntu10), speech-dispatcher-audio-plugins:i386 (0.8-5ubuntu1), libgrilo-0.2-1:i386 (0.2.10-1), plymouth-theme-ubuntu-gnome-text:i386 (14.04.1), gir1.2-gst-plugins-base-1.0:i386 (1.2.3-1), gstreamer0.10-pulseaudio:i386 (0.10.31-3+nmu1ubuntu5), libgstreamer-plugins-good1.0-0:i386 (1.2.3-1ubuntu2), libmhash2:i386 (0.9.9.9-4), libbrasero-media3-1:i386 (3.10.0-0ubuntu1), evolution:i386 (3.10.4-0ubuntu1), rhythmbox-plugin-cdrecorder:i386 (3.0.2-0ubuntu2), gnome-icon-theme-extras:i386 (3.12.0-1ubuntu1), libexttextcat-2.0-0:i386 (3.4.3-1ubuntu1), gnome-font-viewer:i386 (3.8.0-1build1), rhythmbox-mozilla:i386 (3.0.2-0ubuntu2), libmission-control-plugins0:i386 (5.16.1-1ubuntu3), libmozjs-24-0:i386 (24.2.0-1), python3-mako:i386 (0.9.1-1), libexttextcat-data:i386 (3.4.3-1ubuntu1), gstreamer1.0-pulseaudio:i386 (1.2.3-1ubuntu2), libpwquality1:i386 (1.2.3-1ubuntu1), libiptcdata0:i386 (1.0.4-3ubuntu3), eog:i386 (3.10.2-0ubuntu5), gnome-tweak-tool:i386 (3.10.1-2ubuntu1), gir1.2-rest-0.7:i386 (0.7.90-0ubuntu1), grilo-plugins-0.2:i386 (0.2.12-2), fonts-nanum:i386 (20131007-1), libgtop2-7:i386 (2.28.5-2), zsync:i386 (0.6.2-1ubuntu1), liboauth0:i386 (1.0.1-1), gir1.2-caribou-1.0:i386 (0.4.13-0ubuntu1), gir1.2-gdata-0.0:i386 (0.14.1-1), gir1.2-json-1.0:i386 (0.16.2-1ubuntu1), mousetweaks:i386 (3.8.0-2), libytnef0:i386 (1.5-6), libgstreamer-plugins-base0.10-0:i386 (0.10.36-1.1ubuntu2), baobab:i386 (3.8.2-1ubuntu1), libcurl3:i386 (7.35.0-1ubuntu2), hwdata:i386 (0.249-1), libogg0:i386 (1.3.1-1ubuntu1), liberror-perl:i386 (0.17-1.1), libcaribou-common:i386 (0.4.13-0ubuntu1), gnome-session-common:i386 (3.9.90-0ubuntu12), cheese:i386 (3.10.2-0ubuntu2), evolution-plugins:i386 (3.10.4-0ubuntu1), libreoffice-math:i386 (4.2.3~rc3-0ubuntu2), libgtkhtml-4.0-0:i386 (4.6.6-2ubuntu1), ubuntu-gnome-wallpapers:i386 (14.04.1), liborc-0.4-0:i386 (0.4.18-1ubuntu1), media-player-info:i386 (21-0ubuntu1), aisleriot:i386 (3.10.2-1), gir1.2-telepathyglib-0.12:i386 (0.22.1-1ubuntu2), libreoffice-calc:i386 (4.2.3~rc3-0ubuntu2), libpwquality-common:i386 (1.2.3-1ubuntu1), libraptor2-0:i386 (2.0.13-1), mutter-common:i386 (3.10.4-0ubuntu2), libwmf0.2-7:i386 (0.2.8.4-10.3ubuntu1), libwebkitgtk-3.0-0:i386 (2.4.0-1ubuntu2), libtotem0:i386 (3.10.1-1ubuntu4), libgdata13:i386 (0.14.1-1), gnome-contacts:i386 (3.8.3-1ubuntu1), gstreamer0.10-plugins-good:i386 (0.10.31-3+nmu1ubuntu5), fonts-cantarell:i386 (0.0.15-1), dconf-cli:i386 (0.20.0-1), libhttp-cookies-perl:i386 (6.00-2), gir1.2-zpj-0.0:i386 (0.0.3-1ubuntu1), libfarstream-0.1-0:i386 (0.1.2-1ubuntu3), gnome-settings-daemon:i386 (3.8.6.1-0ubuntu11), libespeak1:i386 (1.47.11-1ubuntu1), libwww-perl:i386 (6.05-2), gnome-session-bin:i386 (3.9.90-0ubuntu12), libboost-date-time1.54.0:i386 (1.54.0-4ubuntu3), libvorbisfile3:i386 (1.3.2-1.3ubuntu1), ubuntu-gnome-wallpapers-trusty:i386 (14.04.1), libedata-book-1.2-20:i386 (3.10.4-0ubuntu1), nautilus:i386 (3.10.1-0ubuntu9), libebook-contacts-1.2-0:i386 (3.10.4-0ubuntu1), liblangtag-common:i386 (0.5.1-2), libunity-control-center1:i386 (14.04.3+14.04.20140410-0ubuntu1), session-migration:i386 (0.2.1), gnome-mines:i386 (3.10.1-0ubuntu1), ubuntu-release-upgrader-gtk:i386 (0.220.2), rhythmbox:i386 (3.0.2-0ubuntu2), gstreamer1.0-plugins-good:i386 (1.2.3-1ubuntu2), libgdata-common:i386 (0.14.1-1), gir1.2-networkmanager-1.0:i386 (0.9.8.8-0ubuntu7), rhythmbox-data:i386 (3.0.2-0ubuntu2), gnome-mahjongg:i386 (3.10.2-0ubuntu1), evolution-data-server-common:i386 (3.10.4-0ubuntu1), notification-daemon:i386 (0.7.6-1), deja-dup-backend-cloudfiles:i386 (30.0-0ubuntu4), libopencc1:i386 (0.4.3-2build1), gnome-shell:i386 (3.10.4-0ubuntu5), python-cloudfiles:i386 (1.7.11-2build1), nautilus-sendto:i386 (3.6.1-2ubuntu1), libexempi3:i386 (2.2.1-1ubuntu1), update-manager:i386 (0.196.12), libwmf0.2-7-gtk:i386 (0.2.8.4-10.3ubuntu1), libmeanwhile1:i386 (1.0.2-4.1ubuntu1), libzapojit-0.0-0:i386 (0.0.3-1ubuntu1), cups-pk-helper:i386 (0.2.5-0ubuntu1), deja-dup-backend-gvfs:i386 (30.0-0ubuntu4), sa-compile:i386 (3.4.0-1ubuntu1), libcheese-gtk23:i386 (3.10.2-0ubuntu2), libiec61883-0:i386 (1.2.0-0.1ubuntu3), libcanberra-pulse:i386 (0.30-0ubuntu3), libcanberra-gtk3-0:i386 (0.30-0ubuntu3), gir1.2-gck-1:i386 (3.10.1-1), deja-dup-backend-s3:i386 (30.0-0ubuntu4), librdf0:i386 (1.0.17-1), libhttp-negotiate-perl:i386 (6.00-2), libfolks-eds25:i386 (0.9.5-1ubuntu5), uno-libs3:i386 (4.2.3~rc3-0ubuntu2), libhtml-tree-perl:i386 (5.03-1), vino:i386 (3.8.1-0ubuntu1), ibus-table:i386 (1.5.0.is.1.5.0.20130419-2), libcdr-0.0-0:i386 (0.0.15-1ubuntu1), totem:i386 (3.10.1-1ubuntu4), gnome-bluetooth:i386 (3.8.2.1-0ubuntu4), xserver-xephyr:i386 (1.15.1-0ubuntu2), gir1.2-cogl-1.0:i386 (1.16.2-1), libhyphen0:i386 (2.8.6-3ubuntu2), libpulsedsp:i386 (4.0-0ubuntu11), libgtkhtml-editor-4.0-0:i386 (4.6.6-2ubuntu1), libgnomekbd8:i386 (3.6.0-0ubuntu2), libgnomekbd-common:i386 (3.6.0-0ubuntu2), libmediaart-1.0-0:i386 (0.4.0-1ubuntu1), gstreamer0.10-nice:i386 (0.1.4-1), libspeex1:i386 (1.2~rc1.1-1ubuntu1), gnome-system-log:i386 (3.8.1-1svn1), xsltproc:i386 (1.1.28-2build1), empathy:i386 (3.8.6-0ubuntu9.1), libgtop2-common:i386 (2.28.5-2), python-ibus:i386 (1.5.5-1ubuntu3), shotwell:i386 (0.18.0-0ubuntu4), libnet-http-perl:i386 (6.06-1), ibus:i386 (1.5.5-1ubuntu3), libnss-myhostname:i386 (0.3-6), libcolamd2.8.0:i386 (4.2.1-3ubuntu1), rhythmbox-plugin-zeitgeist:i386 (3.0.2-0ubuntu2), libwpd-0.9-9:i386 (0.9.9-1), libmail-spf-perl:i386 (2.9.0-2), brasero-cdrkit:i386 (3.10.0-0ubuntu1), gtk2-engines-pixbuf:i386 (2.24.23-0ubuntu1), gnome-online-miners:i386 (3.10.3-0ubuntu3), libhtml-parser-perl:i386 (3.71-1build1), libgsf-1-common:i386 (1.14.27-2ubuntu2), re2c:i386 (0.13.5-1build2), libcanberra-gtk3-module:i386 (0.30-0ubuntu3), guile-2.0-libs:i386 (2.0.9+1-1ubuntu1), gvfs-backends-goa:i386 (1.20.1-1ubuntu1), gnome-backgrounds:i386 (3.12.0-1), libgnome-desktop-3-7:i386 (3.8.4-0ubuntu3), libxml2-utils:i386 (2.9.1+dfsg1-3ubuntu4), librsync1:i386 (0.9.7-10), libclucene-contribs1:i386 (2.3.3.4-4build1), libreoffice-draw:i386 (4.2.3~rc3-0ubuntu2), gdm:i386 (3.10.0.1-0ubuntu3), gnome-screenshot:i386 (3.10.1-0ubuntu1), itstool:i386 (2.0.2-2), ubuntu-gnome-default-settings:i386 (14.04.1), totem-plugins:i386 (3.10.1-1ubuntu4), libreoffice-base-core:i386 (4.2.3~rc3-0ubuntu2), libclutter-gst-2.0-0:i386 (2.0.8-1build1), libvorbis0a:i386 (1.3.2-1.3ubuntu1), gnome-shell-common:i386 (3.10.4-0ubuntu5), libgupnp-av-1.0-2:i386 (0.12.5-1ubuntu1), gnome-session:i386 (3.9.90-0ubuntu12), gnome-shell-extensions:i386 (3.10.1-0ubuntu2), libibus-1.0-5:i386 (1.5.5-1ubuntu3), nautilus-sendto-empathy:i386 (3.8.6-0ubuntu9.1), gstreamer0.10-x:i386 (0.10.36-1.1ubuntu2), libcrack2:i386 (2.9.1-1build1), libgpod-common:i386 (0.8.3-4ubuntu3), libreoffice-core:i386 (4.2.3~rc3-0ubuntu2), gnome-sudoku:i386 (3.10.2-0ubuntu2), liblangtag1:i386 (0.5.1-2), libjack-jackd2-0:i386 (1.9.9.5+20130622git7de15e7a-1ubuntu1), gnome-online-accounts:i386 (3.10.3-0ubuntu1), gir1.2-goa-1.0:i386 (3.10.3-0ubuntu1), libcanberra0:i386 (0.30-0ubuntu3), empathy-common:i386 (3.8.6-0ubuntu9.1), libxcb-keysyms1:i386 (0.3.9-1ubuntu1), tracker-extract:i386 (0.16.2-1ubuntu4.1), evolution-data-server-online-accounts:i386 (3.10.4-0ubuntu1), libebackend-1.2-7:i386 (3.10.4-0ubuntu1), dconf-editor:i386 (0.20.0-1), libicc2:i386 (2.12+argyll1.5.1-5ubuntu1), libdmapsharing-3.0-2:i386 (2.9.24-0ubuntu1), gnome-session-canberra:i386 (0.30-0ubuntu3), libmythes-1.2-0:i386 (1.2.2-1ubuntu2), gnome-user-guide:i386 (3.8.2-1), gnome-themes-standard-data:i386 (3.10.0-1ubuntu2), libnetaddr-ip-perl:i386 (4.071+dfsg-1), libwhoopsie0:i386 (0.2.24.5), libwacom2:i386 (0.8-1), libgupnp-1.0-4:i386 (0.20.10-1ubuntu1), libsbc1:i386 (1.1-2ubuntu2), libcmis-0.4-4:i386 (0.4.1-3ubuntu4), apturl-common:i386 (0.5.2ubuntu4), libnice10:i386 (0.1.4-1), gir1.2-totem-1.0:i386 (3.10.1-1ubuntu4), ibus-gtk3:i386 (1.5.5-1ubuntu3), libgnome-control-center1:i386 (3.6.3-0ubuntu56), gir1.2-webkit-3.0:i386 (2.4.0-1ubuntu2), gir1.2-nmgtk-1.0:i386 (0.9.8.8-0ubuntu4), libpulse0:i386 (4.0-0ubuntu11), geoclue:i386 (0.12.99-3ubuntu1), gir1.2-gdm-1.0:i386 (3.10.0.1-0ubuntu3), libwacom-common:i386 (0.8-1), gjs:i386 (1.40.1-0ubuntu0.2), libzephyr4:i386 (3.1.2-1), python-urllib3:i386 (1.7.1-1build1), libhttp-date-perl:i386 (6.02-1), libmutter0c:i386 (3.10.4-0ubuntu2), libxcb-image0:i386 (0.3.9-1ubuntu2), python3-uno:i386 (4.2.3~rc3-0ubuntu2), libgc1c2:i386 (7.2d-5ubuntu2), liborcus-0.6-0:i386 (0.5.1-7), yelp-tools:i386 (3.10.0-1), libproxy1-plugin-networkmanager:i386 (0.4.11-0ubuntu4), libcolord-gtk1:i386 (0.1.25-1.1), obexd-client:i386 (0.46-1ubuntu7), unoconv:i386 (0.6-6), libwww-robotrules-perl:i386 (6.01-1), gir1.2-gnomekeyring-1.0:i386 (3.8.0-2), gstreamer0.10-plugins-base:i386 (0.10.36-1.1ubuntu2), libgoa-1.0-0b:i386 (3.10.3-0ubuntu1), gkbd-capplet:i386 (3.6.0-0ubuntu2), gir1.2-gtop-2.0:i386 (2.28.5-2), libgweather-common:i386 (3.10.2-0ubuntu1), python-requests:i386 (2.2.1-1), libxcb-icccm4:i386 (0.4.1-1ubuntu1), gir1.2-tracker-0.16:i386 (0.16.2-1ubuntu4.1), libgoa-backend-1.0-1:i386 (3.10.3-0ubuntu1), tracker-miner-fs:i386 (0.16.2-1ubuntu4.1), whoopsie:i386 (0.2.24.5), libcdio-cdda1:i386 (0.83-4.1ubuntu1), python-lockfile:i386 (0.8-2ubuntu2), libencode-locale-perl:i386 (1.03-1), libgif4:i386 (4.1.6-11), libshout3:i386 (2.3.1-3), telepathy-salut:i386 (0.8.1-1ubuntu3), python-boto:i386 (2.20.1-2ubuntu2), tracker-utils:i386 (0.16.2-1ubuntu4.1), plymouth-theme-ubuntu-gnome-logo:i386 (14.04.1), duplicity:i386 (0.6.23-1ubuntu4), libhttp-daemon-perl:i386 (6.01-1), libtelepathy-farstream3:i386 (0.6.1-0ubuntu1), libsystemd-journal0:i386 (204-5ubuntu20), libproxy1-plugin-gsettings:i386 (0.4.11-0ubuntu4), gir1.2-mutter-3.0:i386 (3.10.4-0ubuntu2), gstreamer0.10-alsa:i386 (0.10.36-1.1ubuntu2), libwpg-0.2-2:i386 (0.2.2-1ubuntu1), libboost-system1.54.0:i386 (1.54.0-4ubuntu3), libxcb-xv0:i386 (1.10-2ubuntu1), gir1.2-gtkclutter-1.0:i386 (1.4.4-3ubuntu2), libcanberra-gtk0:i386 (0.30-0ubuntu3), libfolks-telepathy25:i386 (0.9.5-1ubuntu5), argyll:i386 (1.5.1-5ubuntu1), libreoffice-gnome:i386 (4.2.3~rc3-0ubuntu2), libmusicbrainz5-0:i386 (5.0.1-2), libzeitgeist-1.0-1:i386 (0.3.18-1ubuntu2), libreoffice-avmedia-backend-gstreamer:i386 (4.2.3~rc3-0ubuntu2), libcdio13:i386 (0.83-4.1ubuntu1), ubuntu-system-service:i386 (0.2.5build1), pulseaudio-module-x11:i386 (4.0-0ubuntu11), gstreamer1.0-plugins-base:i386 (1.2.3-1), gir1.2-clutter-gst-2.0:i386 (2.0.8-1build1), gstreamer1.0-nice:i386 (0.1.4-1), software-center:i386 (13.10-0ubuntu4.1), libhtml-format-perl:i386 (2.11-1), apturl:i386 (0.5.2ubuntu4), spamassassin:i386 (3.4.0-1ubuntu1), gir1.2-ibus-1.0:i386 (1.5.5-1ubuntu3), ibus-pinyin:i386 (1.5.0-1ubuntu1), gnome-icon-theme-full:i386 (3.10.0-0ubuntu2), libcheese7:i386 (3.10.2-0ubuntu2), libgjs0e:i386 (1.40.1-0ubuntu0.2), libreoffice-writer:i386 (4.2.3~rc3-0ubuntu2), speech-dispatcher:i386 (0.8-5ubuntu1), gnome-control-center-shared-data:i386 (3.6.3-0ubuntu56), gir1.2-accountsservice-1.0:i386 (0.6.35-0ubuntu7), gir1.2-polkit-1.0:i386 (0.105-4ubuntu2), pulseaudio-module-bluetooth:i386 (4.0-0ubuntu11), libvorbisenc2:i386 (1.3.2-1.3ubuntu1), libtheora0:i386 (1.1.1+dfsg.1-3.2), mutter:i386 (3.10.4-0ubuntu2), libcaribou0:i386 (0.4.13-0ubuntu1), libevolution:i386 (3.10.4-0ubuntu1), libecal-1.2-16:i386 (3.10.4-0ubuntu1), libclucene-core1:i386 (2.3.3.4-4build1), gstreamer1.0-x:i386 (1.2.3-1), librasqal3:i386 (0.9.32-1), libyajl2:i386 (2.0.4-4), gir1.2-secret-1:i386 (0.16-0ubuntu1), libpulse-mainloop-glib0:i386 (4.0-0ubuntu11), deja-dup:i386 (30.0-0ubuntu4), seahorse:i386 (3.10.2-0ubuntu1), libasound2-plugins:i386 (1.0.27-2ubuntu2), yelp:i386 (3.10.2-0ubuntu1), gnome-desktop3-data:i386 (3.8.4-0ubuntu3), libgdm1:i386 (3.10.0.1-0ubuntu3), libreoffice-gtk:i386 (4.2.3~rc3-0ubuntu2), libmspub-0.0-0:i386 (0.0.6-1ubuntu2), libhtml-tagset-perl:i386 (3.20-2), libimdi0:i386 (1.5.1-5ubuntu1), librhythmbox-core8:i386 (3.0.2-0ubuntu2), gnome-disk-utility:i386 (3.10.0-1ubuntu3), libedataserver-1.2-18:i386 (3.10.4-0ubuntu1), libio-html-perl:i386 (1.00-1), pulseaudio-utils:i386 (4.0-0ubuntu11), gir1.2-coglpango-1.0:i386 (1.16.2-1), gnome-system-monitor:i386 (3.8.2.1-2ubuntu1), intel-gpu-tools:i386 (1.3-0ubuntu2), gvfs-backends:i386 (1.20.1-1ubuntu1), liblwp-protocol-https-perl:i386 (6.04-2), libedata-cal-1.2-23:i386 (3.10.4-0ubuntu1), libgpod4:i386 (0.8.3-4ubuntu3), telepathy-gabble:i386 (0.18.2-1), libcanberra-gtk-module:i386 (0.30-0ubuntu3), gnome-terminal-data:i386 (3.6.2-0ubuntu1), libgsf-1-114:i386 (1.14.27-2ubuntu2), gir1.2-xkl-1.0:i386 (5.4-0ubuntu1), telepathy-haze:i386 (0.8.0-1), rhythmbox-plugins:i386 (3.0.2-0ubuntu2), gir1.2-gnomedesktop-3.0:i386 (3.8.4-0ubuntu3), telepathy-idle:i386 (0.2.0-1), libxcb-xf86dri0:i386 (1.10-2ubuntu1), gir1.2-gkbd-3.0:i386 (3.6.0-0ubuntu2)
Upgrade: nautilus-data:i386 (3.10.1-0ubuntu8, 3.10.1-0ubuntu9), software-properties-gtk:i386 (0.92.36, 0.92.37), python3-software-properties:i386 (0.92.36, 0.92.37), libnautilus-extension1a:i386 (3.10.1-0ubuntu8, 3.10.1-0ubuntu9), software-properties-common:i386 (0.92.36, 0.92.37)
End-Date: 2014-05-11  22:36:52
```

Most notably running the commands in a TTY like that does not prompt for choosing the default display manager so on reboot the system fails to boot because 'lightdm' is not removed but 'unity-greeter' is removed, so I had to launch a TTY again and run "dpkg-reconfigure gdm", select gdm, then reboot again which got me back to the login screen and I did then boot to the GNOME desktop, but there is a lot of cruft left behind:

```
lance@lance-desktop:~$ sudo apt-get -f install
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  freepats liba52-0.7.4 libass4 libavutil52 libcdaudio1 libdca0
  libdirac-encoder0 libdirectfb-1.2-9 libdvdnav4 libdvdread4 libfaad2
  libfftw3-double3 libflite1 libgme0 libgsm1 libgstreamer-plugins-bad1.0-0
  libgtkglext1 libilmbase6 libkate1 libmad0 libmimic0 libmms0 libmodplug1
  libmp3lame0 libmpcdec6 libmpeg2-4 libmpg123-0 libofa0 libopenal-data
  libopenal1 libopencore-amrnb0 libopencore-amrwb0 libopencv-calib3d2.4
  libopencv-core2.4 libopencv-features2d2.4 libopencv-flann2.4
  libopencv-imgproc2.4 libopencv-ml2.4 libopencv-video2.4 libopenexr6
  libopenjpeg2 libopus0 libsidplay1 libsoundtouch0 libspandsp2 libsrtp0
  libswscale2 libtbb2 libts-0.0-0 libtwolame0 libva1 libvo-aacenc0
  libvo-amrwbenc0 libwildmidi-config libwildmidi1 libx264-142 libxvidcore4
  libzbar0 libzvbi-common libzvbi0 tsconf
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.

```

Here are the results of "apt-get autoremove":

```
Start-Date: 2014-05-12  06:54:13
Commandline: apt-get autoremove
Remove: libopenal1:i386 (1.14-4ubuntu1), freepats:i386 (20060219-1), libgstreamer-plugins-bad1.0-0:i386 (1.2.3-1ubuntu2), libx264-142:i386 (0.142.2389+git956c8d8-2), tsconf:i386 (1.0-12), libspandsp2:i386 (0.0.6~pre21-2), libzvbi0:i386 (0.2.35-2), libzvbi-common:i386 (0.2.35-2), libilmbase6:i386 (1.0.1-6ubuntu1), libva1:i386 (1.3.0-2), libwildmidi1:i386 (0.2.3.4-2.1ubuntu3), libgtkglext1:i386 (1.2.0-3.1fakesync3), libdca0:i386 (0.0.5-6ubuntu1), libmpg123-0:i386 (1.16.0-1ubuntu1), libopencv-core2.4:i386 (2.4.8+dfsg1-2ubuntu1), libflite1:i386 (1.4-release-8), libfaad2:i386 (2.7-8), libopencv-calib3d2.4:i386 (2.4.8+dfsg1-2ubuntu1), libofa0:i386 (0.9.3-5ubuntu1), libfftw3-double3:i386 (3.3.3-7ubuntu3), libdirectfb-1.2-9:i386 (1.2.10.0-5), libopus0:i386 (1.1-0ubuntu1), libopencore-amrnb0:i386 (0.1.3-2ubuntu1), libkate1:i386 (0.4.1-1ubuntu1), libdvdread4:i386 (4.2.1-2ubuntu1), libcdaudio1:i386 (0.99.12p2-13), libavutil52:i386 (9.13-0ubuntu0.14.04.1), libvo-aacenc0:i386 (0.1.3-1), libtwolame0:i386 (0.3.13-1ubuntu1), libsidplay1:i386 (1.36.59-5ubuntu1), libmms0:i386 (0.6.2-3ubuntu2), libts-0.0-0:i386 (1.0-12), libtbb2:i386 (4.2~20130725-1.1ubuntu1), libopenal-data:i386 (1.14-4ubuntu1), libopencv-ml2.4:i386 (2.4.8+dfsg1-2ubuntu1), libopencv-features2d2.4:i386 (2.4.8+dfsg1-2ubuntu1), libwildmidi-config:i386 (0.2.3.4-2.1ubuntu3), libopencv-video2.4:i386 (2.4.8+dfsg1-2ubuntu1), libmad0:i386 (0.15.1b-8ubuntu1), libopencore-amrwb0:i386 (0.1.3-2ubuntu1), libopencv-imgproc2.4:i386 (2.4.8+dfsg1-2ubuntu1), libdvdnav4:i386 (4.2.1-3), libopenjpeg2:i386 (1.3+dfsg-4.7ubuntu1), libass4:i386 (0.10.1-3ubuntu1), libmimic0:i386 (1.0.4-2.1ubuntu1), libmp3lame0:i386 (3.99.5+repack1-3ubuntu1), libswscale2:i386 (9.13-0ubuntu0.14.04.1), libzbar0:i386 (0.10+doc-9build1), libopencv-flann2.4:i386 (2.4.8+dfsg1-2ubuntu1), libdirac-encoder0:i386 (1.0.2-6ubuntu1), libvo-amrwbenc0:i386 (0.1.3-1), libxvidcore4:i386 (1.3.2-9ubuntu1), libmpcdec6:i386 (0.1~r459-1ubuntu3), libmodplug1:i386 (0.8.8.4-4.1), libmpeg2-4:i386 (0.5.1-5ubuntu1), libgsm1:i386 (1.0.13-4), libopenexr6:i386 (1.6.1-7ubuntu1), libsoundtouch0:i386 (1.7.1-5), libgme0:i386 (0.5.5-2), liba52-0.7.4:i386 (0.7.4-17), libsrtp0:i386 (1.4.5~20130609~dfsg-1)
End-Date: 2014-05-12  06:54:54
```

And missing recommends are a mess:

[ATTACH=CONFIG]253074[/ATTACH]

---


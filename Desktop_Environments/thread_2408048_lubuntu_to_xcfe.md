---
title: "lubuntu to xcfe"
date: 2018-12-12
forum: Desktop Environments
---

### Post by bradhaack on 2018-12-12
I installed lubuntu but I'd like to switch to xcfe which is what I'm used to on my other computer (xubuntu).  I installed xubuntu-desktop with the package manager.  Can I safely uninstall lubuntu-desktop without breaking the login screen?

---

### Post by again? on 2018-12-13
> **bradhaack said:**
> I installed lubuntu but I'd like to switch to xcfe which is what I'm used to on my other computer (xubuntu).  I installed xubuntu-desktop with the package manager.  Can I safely uninstall lubuntu-desktop without breaking the login screen?
lubuntu-desktop is a [metapackage]("https://help.ubuntu.com/community/MetaPackages") and as such is merely a list of software.
All you remove is the list, not the actual packages installed by the list.

You should be able to remove individual packages like the default lubuntu text editor 
without a problem if your apps menu has too much clutter.
Use **sudo apt remove** and take note of what is to be removed.

If it wants to remove lubuntu-desktop that's ok because it's just a list of packages.
If it wants to remove xubuntu-desktop then you are removing a package required or recommended for xubuntu.

As an example if I were to install lubuntu-desktop in Xubuntu.
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] sudo apt install lubuntu-desktop**
[sudo] password for glen:         
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  abiword abiword-common abiword-plugin-grammar audacious audacious-plugins audacious-plugins-data blueman evince evince-common
  evolution-data-server-common fcitx fcitx-bin fcitx-config-common fcitx-config-gtk fcitx-config-gtk2 fcitx-data fcitx-frontend-all
  fcitx-frontend-gtk2 fcitx-frontend-gtk3 fcitx-frontend-qt4 fcitx-frontend-qt5 fcitx-module-dbus fcitx-module-kimpanel fcitx-module-lua
  fcitx-module-x11 fcitx-modules fcitx-ui-classic ffmpegthumbnailer fonts-noto-color-emoji galculator gdebi gdebi-core
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-gudev-1.0 gir1.2-udisks-2.0 gir1.2-unity-5.0 gnome-mpv gnumeric gnumeric-common
  gnumeric-doc gpicview gsettings-ubuntu-schemas gtklp guvcview hardinfo indicator-application indicator-application-gtk2 indicator-sound
  indicator-sound-gtk2 leafpad libabiword-3.0 libaudcore5 libaudgui5 libaudtag3 libcamel-1.2-61 libchamplain-0.12-0
  libchamplain-gtk-0.12-0 libcompfaceg1 libcue1 libebook-contacts-1.2-2 libedataserver-1.2-23 libevdocument3-4 libevview3-3
  libfcitx-config4 libfcitx-core0 libfcitx-gclient1 libfcitx-qt5-1 libfcitx-utils0 libffmpegthumbnailer4v5 libgettextpo0
  libgoffice-0.10-10 libgoffice-0.10-10-common libgsf-1-114 libgsf-1-common libguvcview-2.0-2 libido-0.1-0 libjpeg-turbo-progs
  liblink-grammar5 libloudmouth1-0 libmpv1 libots0 libphonenumber7 libpisock9 libpresage-data libpresage1v5 libpurple-bin libpurple0
  libsidplayfp4 libtelepathy-glib0 libtidy5 libuniconf4.6 liburl-dispatcher1 libusb-0.1-4 libwebcam0 libwv-1.2-4 libwvstreams4.6-base
  libwvstreams4.6-extras link-grammar-dictionaries-en lubuntu-artwork lubuntu-artwork-18-04 lubuntu-default-session
  lubuntu-default-settings lubuntu-gtk-core lubuntu-gtk-desktop lubuntu-icon-theme lubuntu-lxpanel-icons lxappearance lxappearance-obconf
  lxde-common lxde-core lxinput lxlock lxpanel lxpanel-data lxpanel-indicator-applet-plugin lxpolkit lxrandr lxsession lxsession-data
  lxsession-default-apps lxsession-logout lxshortcut lxtask minisat mtools mtpaint openbox-lxde-session pcmanfm pidgin pidgin-data
  pidgin-libnotify plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text presage pxlib1 sylpheed sylpheed-doc sylpheed-i18n
  sylpheed-plugins syslinux syslinux-common syslinux-legacy ttf-ubuntu-font-family ubuntu-report usb-creator-common usb-creator-gtk
  uvcdynctrl uvcdynctrl-data wvdial xfonts-100dpi xpad xscreensaver xscreensaver-data
Suggested packages:
  nautilus-sendto fcitx-m17n fcitx-tools kdialog plasma-widgets-kimpanel gnumeric-plugins-extra libgsf-1-dev
  unity-greeter-session-broadcast evince-gtk link-grammar-dictionaries-all jpilot pilot-link kpilot gnome-pilot evolution claws-mail
  sidplayfp url-dispatcher amixer xbacklight lxde menu indicator-messages-gtk2 floppyd gnome-panel | kdebase-workspace-bin | docker
  evolution-data-server claws-mail-tools bogofilter bsfilter xfishtank xdaliclock xscreensaver-data-extra xscreensaver-gl
  xscreensaver-gl-extra qcam | streamer gdm3 | kdm-gdmcompat
Recommended packages:
  perl5
The following NEW packages will be installed
  abiword abiword-common abiword-plugin-grammar audacious audacious-plugins audacious-plugins-data blueman evince evince-common
  evolution-data-server-common fcitx fcitx-bin fcitx-config-common fcitx-config-gtk fcitx-config-gtk2 fcitx-data fcitx-frontend-all
  fcitx-frontend-gtk2 fcitx-frontend-gtk3 fcitx-frontend-qt4 fcitx-frontend-qt5 fcitx-module-dbus fcitx-module-kimpanel fcitx-module-lua
  fcitx-module-x11 fcitx-modules fcitx-ui-classic ffmpegthumbnailer fonts-noto-color-emoji galculator gdebi gdebi-core
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-gudev-1.0 gir1.2-udisks-2.0 gir1.2-unity-5.0 gnome-mpv gnumeric gnumeric-common
  gnumeric-doc gpicview gsettings-ubuntu-schemas gtklp guvcview hardinfo indicator-application indicator-application-gtk2 indicator-sound
  indicator-sound-gtk2 leafpad libabiword-3.0 libaudcore5 libaudgui5 libaudtag3 libcamel-1.2-61 libchamplain-0.12-0
  libchamplain-gtk-0.12-0 libcompfaceg1 libcue1 libebook-contacts-1.2-2 libedataserver-1.2-23 libevdocument3-4 libevview3-3
  libfcitx-config4 libfcitx-core0 libfcitx-gclient1 libfcitx-qt5-1 libfcitx-utils0 libffmpegthumbnailer4v5 libgettextpo0
  libgoffice-0.10-10 libgoffice-0.10-10-common libgsf-1-114 libgsf-1-common libguvcview-2.0-2 libido-0.1-0 libjpeg-turbo-progs
  liblink-grammar5 libloudmouth1-0 libmpv1 libots0 libphonenumber7 libpisock9 libpresage-data libpresage1v5 libpurple-bin libpurple0
  libsidplayfp4 libtelepathy-glib0 libtidy5 libuniconf4.6 liburl-dispatcher1 libusb-0.1-4 libwebcam0 libwv-1.2-4 libwvstreams4.6-base
  libwvstreams4.6-extras link-grammar-dictionaries-en lubuntu-artwork lubuntu-artwork-18-04 lubuntu-default-session
  lubuntu-default-settings lubuntu-desktop lubuntu-gtk-core lubuntu-gtk-desktop lubuntu-icon-theme lubuntu-lxpanel-icons lxappearance
  lxappearance-obconf lxde-common lxde-core lxinput lxlock lxpanel lxpanel-data lxpanel-indicator-applet-plugin lxpolkit lxrandr
  lxsession lxsession-data lxsession-default-apps lxsession-logout lxshortcut lxtask minisat mtools mtpaint openbox-lxde-session pcmanfm
  pidgin pidgin-data pidgin-libnotify plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text presage pxlib1 sylpheed sylpheed-doc
  sylpheed-i18n sylpheed-plugins syslinux syslinux-common syslinux-legacy ttf-ubuntu-font-family ubuntu-report usb-creator-common
  usb-creator-gtk uvcdynctrl uvcdynctrl-data wvdial xfonts-100dpi xpad xscreensaver xscreensaver-data
0 to upgrade, 155 to newly install, 0 to remove and 0 not to upgrade.
Need to get 76.9 MB of archives.
After this operation, 272 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```

Removing the lubuntu-desktop package is safe to do but does not remove any of the other packages installed as dependencies.
When testing other desktops I usually make a copy of the new packages to be installed and if I want to completely remove that desktop I would
run something like...
```
sudo apt remove abiword abiword-common abiword-plugin-grammar audacious audacious-plugins audacious-plugins-data blueman evince evince-common evolution-data-server-common fcitx fcitx-bin fcitx-config-common fcitx-config-gtk fcitx-config-gtk2 fcitx-data fcitx-frontend-all fcitx-frontend-gtk2 fcitx-frontend-gtk3 fcitx-frontend-qt4 fcitx-frontend-qt5 fcitx-module-dbus fcitx-module-kimpanel fcitx-module-lua fcitx-module-x11 fcitx-modules fcitx-ui-classic ffmpegthumbnailer fonts-noto-color-emoji galculator gdebi gdebi-core gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-gudev-1.0 gir1.2-udisks-2.0 gir1.2-unity-5.0 gnome-mpv gnumeric gnumeric-common gnumeric-doc gpicview gsettings-ubuntu-schemas gtklp guvcview hardinfo indicator-application indicator-application-gtk2 indicator-sound indicator-sound-gtk2 leafpad libabiword-3.0 libaudcore5 libaudgui5 libaudtag3 libcamel-1.2-61 libchamplain-0.12-0 libchamplain-gtk-0.12-0 libcompfaceg1 libcue1 libebook-contacts-1.2-2 libedataserver-1.2-23 libevdocument3-4 libevview3-3 libfcitx-config4 libfcitx-core0 libfcitx-gclient1 libfcitx-qt5-1 libfcitx-utils0 libffmpegthumbnailer4v5 libgettextpo0 libgoffice-0.10-10 libgoffice-0.10-10-common libgsf-1-114 libgsf-1-common libguvcview-2.0-2 libido-0.1-0 libjpeg-turbo-progs liblink-grammar5 libloudmouth1-0 libmpv1 libots0 libphonenumber7 libpisock9 libpresage-data libpresage1v5 libpurple-bin libpurple0 libsidplayfp4 libtelepathy-glib0 libtidy5 libuniconf4.6 liburl-dispatcher1 libusb-0.1-4 libwebcam0 libwv-1.2-4 libwvstreams4.6-base libwvstreams4.6-extras link-grammar-dictionaries-en lubuntu-artwork lubuntu-artwork-18-04 lubuntu-default-session lubuntu-default-settings lubuntu-desktop lubuntu-gtk-core lubuntu-gtk-desktop lubuntu-icon-theme lubuntu-lxpanel-icons lxappearance lxappearance-obconf lxde-common lxde-core lxinput lxlock lxpanel lxpanel-data lxpanel-indicator-applet-plugin lxpolkit lxrandr lxsession lxsession-data lxsession-default-apps lxsession-logout lxshortcut lxtask minisat mtools mtpaint openbox-lxde-session pcmanfm pidgin pidgin-data pidgin-libnotify plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text presage pxlib1 sylpheed sylpheed-doc sylpheed-i18n sylpheed-plugins syslinux syslinux-common syslinux-legacy ttf-ubuntu-font-family ubuntu-report usb-creator-common usb-creator-gtk uvcdynctrl uvcdynctrl-data wvdial xfonts-100dpi xpad xscreensaver xscreensaver-data

```

---


---
title: "Kubuntu-desktop or Standalone install?"
date: 2011-08-28
forum: Desktop Environments
---

### Post by Anfloyd on 2011-08-28
Hi. I'm new to Ubuntu but slowly finding my feet and starting to love both how it runs and what it stands for. But I'm quite an indecisive kind of guy and can't make up my mind on whether to use Ubuntu with Unity or KDE. Now I'm aware that I can install kde desktop from within ubuntu 11.04 but my question is whether or not there are any significant differences (performance or otherwise) in doing this or just using a fresh standalone install of Kubuntu?

Cheers.

---

### Post by rectec794613 on 2011-08-28
Hello, Anfloyd.

Welcome to the forums and Ubuntu.

It's normal for new users to have a hard time deciding desktop environments. Mostly it's a matter of personal choice. If you haven't decided over KDE or Unity, I would recommend you watch some videos and view pictures on each one, and see which fits you best.

Regarding your question about installing KDE from within Ubuntu, there's not gonna be much difference performance-wise. However there might be some conflicts with things such as default programs, icons, etc. For that reason I would recommend doing a fresh install of Kubuntu 11.04. I'm not completely sure how well the former will go as I've not installed KDE over Unity, but have installed it over Gnome several times, and the results were not good. Some stability issues, startup errors. I think it would be best to enjoy KDE on a fresh install. If you have personal files and/or program settings saved, I recommend making a copy of your home folder, and we'll aid you from there.

Good luck!

-Rob

---

### Post by IWantFroyo on 2011-08-28
You can just install kubuntu-desktop, but if you want to install the KDE programs, I would recommend a fresh install.

---

### Post by SeijiSensei on 2011-08-28
You can try installing from the Kubuntu CD and setting up a dual-boot with your current Unity installation.  You'll probably need to repartition the hard drive to free up some space.  

Another alternative is to install the Kubuntu ISO image [to a USB key]("https://help.ubuntu.com/community/Installation/FromUSBStick") and boot from that.  You could run Kubuntu from the CD to try it out, but it's very slow.  A USB key has better performance.

---

### Post by realzippy on 2011-08-28
+1 for a "true" Kubuntu.

Otherwise your menus get pretty mixed up.

---

### Post by Anfloyd on 2011-08-28
Thanks for your replies. Decided to just to a clean install of Kubuntu and stick with that. I have an ATI graphics card installed and I noticed a few glitches now and again with Unity, not so much with KDE.
Will explore some more now. No doubt you'll be hearing from me again with further questions!
Thanks again.:P

---

### Post by realzippy on 2011-08-28
I started a similar thread some time ago,there are useful suggestions
from KDE user.[Go ahead]("http://ubuntuforums.org/showthread.php?t=1826925")..

---

### Post by dniMretsaM on 2011-08-28
For future reference, there is no need to do a complete new install of Kubuntu. If you run the following command in terminal, it will install KDE and programs and remove GNOME/Unity and programs. This is what I did when I changed and it worked like a charm.

```
sudo apt-get remove adium-theme-ubuntu aisleriot alacarte  app-install-data-partner apport-gtk aptdaemon aptdaemon-data at-spi  bamfdaemon banshee banshee-extension-soundmenu  banshee-extension-ubuntuonemusicstore baobab binfmt-support  bluez-gstreamer bogofilter bogofilter-bdb bogofilter-common  branding-ubuntu brasero brasero-cdrkit brasero-common brltty-x11  build-essential capplets-data checkbox checkbox-gtk cli-common compiz  compiz-core compiz-gnome compiz-plugins compiz-plugins-main  compizconfig-backend-gconf computer-janitor computer-janitor-gtk  desktop-file-utils diffstat dmz-cursor-theme doc-base dpkg-dev empathy  empathy-common eog espeak espeak-data evince evince-common evolution  evolution-common evolution-data-server evolution-data-server-common  evolution-exchange evolution-indicator evolution-plugins  evolution-webcal example-content fakeroot file-roller firefox  firefox-globalmenu firefox-gnome-support g++ g++-4.5 gamin gbrainy  gcalctool gcc gcc-4.5 gconf-defaults-service gconf-editor gdm  gdm-guest-session gedit gedit-common geoclue geoclue-ubuntu-geoip  gettext ginn gir1.2-appindicator-0.1 gir1.2-atk-1.0 gir1.2-freedesktop  gir1.2-gconf-2.0 gir1.2-gdkpixbuf-2.0 gir1.2-gtk-2.0 gir1.2-notify-0.7  gir1.2-panelapplet-3.0 gir1.2-pango-1.0 gir1.2-soup-2.4 gir1.2-vte-0.0  gksu gnome-about gnome-accessibility-themes gnome-applets  gnome-applets-data gnome-bluetooth gnome-codec-install  gnome-control-center gnome-desktop-data gnome-disk-utility  gnome-doc-utils gnome-games-common gnome-icon-theme gnome-keyring  gnome-mag gnome-mahjongg gnome-media gnome-media-common gnome-menus  gnome-mime-data gnome-nettool gnome-orca gnome-panel gnome-panel-bonobo  gnome-panel-data gnome-power-manager gnome-screensaver gnome-screenshot  gnome-search-tool gnome-session gnome-session-bin gnome-session-canberra  gnome-session-common gnome-settings-daemon gnome-sudoku  gnome-system-log gnome-system-monitor gnome-system-tools gnome-terminal  gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu  gnome-user-guide gnome-user-share gnome-utils-common gnomine  gsettings-desktop-schemas gstreamer0.10-gnonlin gstreamer0.10-nice  gstreamer0.10-plugins-base-apps gstreamer0.10-tools gtk2-engines  gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs  gvfs-backends gvfs-fuse gwibber gwibber-service gwibber-service-facebook  gwibber-service-identica gwibber-service-twitter humanity-icon-theme  hwdata ibus ibus-gtk ibus-pinyin ibus-pinyin-db-android  ibus-pinyin-db-open-phrase ibus-table indicator-applet  indicator-applet-appmenu indicator-applet-complete  indicator-applet-session indicator-application indicator-appmenu  indicator-datetime indicator-me indicator-messages indicator-session  indicator-sound intltool-debian jockey-gtk language-selector-gnome  launchpad-integration libalgorithm-diff-perl libalgorithm-diff-xs-perl  libalgorithm-merge-perl libappindicator0.1-cil libappindicator1  libapt-pkg-perl libart-2.0-2 libart2.0-cil libatkmm-1.6-1 libatspi1.0-0  libavahi-glib1 libavahi-gobject0 libavahi-ui0 libbamf0 libbonobo2-0  libbonobo2-common libbonoboui2-0 libbonoboui2-common  libboost-serialization1.42.0 libbrasero-media1 libburn4 libc-dev-bin  libc6-dev libcairo-gobject2 libcairo-perl libcairomm-1.0-1  libcamel1.2-19 libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse  libcdio-cdda0 libcdio-paranoia0 libcdio10 libclass-accessor-perl  libcompizconfig0 libcroco3 libcryptui0 libdconf0 libdecoration0  libdee-1.0-1 libdigest-hmac-perl libdotconf1.0 libdpkg-perl  libebackend1.2-0 libebook1.2-10 libecal1.2-8 libedata-book1.2-8  libedata-cal1.2-10 libedataserver1.2-14 libedataserverui1.2-11  libegroupwise1.2-13 libemail-valid-perl libept1 libespeak1  libevdocument3 libevent-1.4-2 libevolution libevview3 libexempi3  libfolks-telepathy22 libfolks22 libfreezethaw-perl libgail-common  libgail-gnome-module libgail18 libgamin0 libgconf2.0-cil libgcr0  libgd2-xpm libgdata-common libgdata1.7-cil libgdata11 libgdu-gtk0  libgdu0 libgee2 libgeoclue0 libgexiv2-0 libgkeyfile1.0-cil libgksu2-0  libglade2-0 libglade2.0-cil libgladeui-1-11 libglew1.5 libglewmx1.5  libglib-perl libglib2.0-bin libglib2.0-cil libglib2.0-data  libglibmm-2.4-1c2a libgmime-2.4-2 libgmime2.4-cil libgnome-bluetooth8  libgnome-desktop-2-17 libgnome-mag2 libgnome-media0 libgnome-menu2  libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0  libgnome2-common libgnome2.24-cil libgnomecanvas2-0  libgnomecanvas2-common libgnomekbd-common libgnomekbd4 libgnomeui-0  libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgoocanvas-common  libgoocanvas3 libgp11-0 libgsl0ldbl libgssdp-1.0-2 libgstfarsight0.10-0  libgtk-sharp-beans-cil libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil  libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19  libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtksourceview2.0-common  libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgudev1.0-cil  libgupnp-1.0-3 libgupnp-igd-1.0-3 libgvfscommon0 libgweather-common  libgweather1 libgwibber1 libibus2 libido-0.1-0 libindicate-gtk2  libindicator3 libio-pty-perl libio-string-perl libipc-run-perl libisofs6  libjson-glib-1.0-0 libkpathsea5 liblaunchpad-integration-common  liblaunchpad-integration1 liblaunchpad-integration1.0-cil liblircclient0  liblouis-data liblouis2 liblua5.1-0 libmetacity-private0  libmission-control-plugins0 libmldbm-perl libmono-addins-gui0.2-cil  libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil  libmono-i18n-west2.0-cil libmono-management2.0-cil libmono-posix2.0-cil  libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-system2.0-cil  libmono-zeroconf1.0-cil libnautilus-extension1 libndesk-dbus-glib1.0-cil  libndesk-dbus1.0-cil libnet-dbus-perl libnet-dns-perl  libnet-domain-tld-perl libnet-ip-perl libnice10 libnotify0.4-cil  libnotify1 libnotify4 libnux-0.9-0 libnux-0.9-common liboobs-1-5  libopencc1 liboverlay-scrollbar-0.1-0 libpam-gnome-keyring  libpanel-applet-3-0 libpanel-applet2-0 libpango-perl libpangomm-1.4-1  libparse-debianchangelog-perl libpolkit-gtk-1-0 libpoppler-glib6  libportaudio2 libprotobuf6 libprotoc6 libpst4 libpurple-bin libpurple0  libquvi0 librarian0 libreoffice-gnome libreoffice-gtk  libreoffice-help-en-us libreoffice-style-human librsvg2-2  librsvg2-common libsdl1.2debian libsdl1.2debian-pulseaudio  libsigc++-2.0-0c2a libsilc-1.1-2 libsilcclient-1.1-3 libspeechd2  libstartup-notification0 libstdc++6-4.5-dev libsub-name-perl  libsyncdaemon-1.0-1 libt1-5 libtaglib2.0-cil libtelepathy-farsight0  libtelepathy-glib0 libtelepathy-logger2 libtie-ixhash-perl  libtotem-plparser17 libubuntuone-1.0-1 libubuntuone1.0-cil  libunique-1.0-0 libunistring0 libunity-misc0 libunity4 libutouch-geis1  libuuid-perl libvte-common libvte9 libwebkitgtk-1.0-0  libwebkitgtk-1.0-common libwmf0.2-7 libwmf0.2-7-gtk libwnck-common  libwnck22 libxcb-event1 libxklavier16 libxml-twig-perl libxml-xpath-perl  libxres1 libzeitgeist-1.0-1 libzephyr4 light-themes lintian  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic  linux-headers-generic linux-libc-dev lzma make manpages-dev  media-player-info metacity metacity-common mono-2.0-gac  mono-csharp-shell mono-gac mono-gmcs mono-runtime mousetweaks nautilus  nautilus-data nautilus-sendto nautilus-sendto-empathy nautilus-share  network-manager-gnome network-manager-pptp-gnome notification-daemon  notify-osd notify-osd-icons nux-tools onboard overlay-scrollbar patch  pinyin-database pitivi pkg-config plymouth-theme-ubuntu-logo  policykit-1-gnome protobuf-compiler pulseaudio-module-gconf  python-appindicator python-aptdaemon python-aptdaemon-gtk  python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-argparse  python-brlapi python-configglue python-defer python-egenix-mxdatetime  python-egenix-mxtools python-farsight python-gconf python-glade2  python-gmenu python-gnome2 python-gnomecanvas python-gnomekeyring  python-gst0.10 python-gtk2 python-gtksourceview2 python-gtkspell  python-ibus python-indicate python-launchpad-integration python-libproxy  python-libxml2 python-louis python-mako python-markupsafe python-notify  python-openssl python-pam python-papyon python-piston-mini-client  python-protobuf python-pyatspi python-pygoocanvas python-pyinotify  python-pyorbit python-rdflib python-serial python-speechd  python-telepathy python-twisted-bin python-twisted-core  python-twisted-names python-twisted-web python-ubuntuone-client  python-ubuntuone-control-panel python-ubuntuone-storageprotocol  python-virtkey python-vte python-webkit python-wnck rarian-compat  screensaver-default-images seahorse sessioninstaller shotwell  simple-scan software-center software-properties-gtk speech-dispatcher  ssh-askpass-gnome synaptic system-config-printer-gnome  system-tools-backends telepathy-butterfly telepathy-gabble  telepathy-haze telepathy-idle telepathy-logger  telepathy-mission-control-5 telepathy-salut tomboy totem totem-common  totem-mozilla totem-plugins transmission-common transmission-gtk  tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono  ubuntu-sounds ubuntu-sso-client ubuntu-system-service ubuntu-wallpapers  ubuntuone-client ubuntuone-client-gnome ubuntuone-control-panel  ubuntuone-control-panel-gtk unity unity-asset-pool unity-common  unity-place-applications unity-place-files update-manager  update-notifier update-notifier-common usb-creator-gtk vinagre vino  whois xdg-user-dirs-gtk xscreensaver-data xscreensaver-gl xsltproc  xul-ext-ubufox yelp yelp-xsl zeitgeist zeitgeist-core zeitgeist-datahub  zeitgeist-extension-fts zenity && sudo apt-get install  kubuntu-desktop
```

---


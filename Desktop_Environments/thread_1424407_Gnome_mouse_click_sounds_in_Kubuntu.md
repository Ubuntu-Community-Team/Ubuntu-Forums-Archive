---
title: "Gnome mouse click sounds in Kubuntu"
date: 2010-03-07
forum: Desktop Environments
---

### Post by James.Lazo on 2010-03-07
Hi All,

I'm having minor, but very annoying, issue in Kubuntu 9.10.
Recently I installed the Gnome desktop to see if certain bugs I was experiencing were KDE-centric. I have since uninstalled Gnome (and reconfigured my audio drivers and reinstalled wicd, all of which was made short shrift of by Gnome), but one thing I can't get rid of is this annoying drum click sound in certain applications. All extension buttons in my browser now make the click sound, as well as the TrueCrypt GUI.

I know this is a very minor issue, but I've always configured my operating systems with absolutely no system sounds (only audio and video playback), so I'm finding this particularly distracting. Right now, the only option I have is to mute PCM volume, which also mutes streaming audio and video in my browser...

I'm at my wit's end. I have all sound notifications turned off in system settings (though there were relatively few to begin with in KDE). Please tell me there's a magic sudo code I can cast to exorcise my computer of mouse click sounds.

Many thanks,

James

---

### Post by inobe on 2010-03-08
it's very complicated removing remnants of gnome, it's best to test them on separate machines or boot devices.


there are things you can do except you will risk breakage.


i hear it's best to use aptitude instead of apt-get, i think it's because it tracks all packages and dependencies, if you decided to remove something' you will be able to rid of all remnants.

---

### Post by James.Lazo on 2010-03-08
Yes, I remember I ended up reinstalling Ubuntu the first time I tried to install another desktop. Well, consider the lesson thoroughly learned now.

So any ideas how to get those sounds off my computer?

---

### Post by inobe on 2010-03-08
okay, here we go, you can reinstall ubuntu desktop using aptitude instead of apt-get, then remove ubuntu desktop with aptitude.


>   Aptitude

Aptitude is a terminal-based package manager that can be used instead of apt-get. Aptitude marks packages that are automatically installed and removes them when no packages depend on them. This makes it easy to remove applications completely. To use Aptitude, replace apt-get with aptitude in the command line. Example: 

```
sudo aptitude install packagename
sudo aptitude remove packagename
sudo aptitude update
sudo aptitude upgrade

```

> For an ncurses-based graphical user interface, type 

```
sudo aptitude
```

[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/)


now here's the deal, i have no doubt that there are much more remnants left behind, at least this way you have a chance.

---

### Post by James.Lazo on 2010-03-08
Thanks for that inobe - I'll remember to use aptitude for packages I'm not sure I want to keep. I'm going to hunt around a bit more before I consider reinstalling Gnome.

I did come across this morsel, but unfortunately nothing happened when I invoked the commands...

[http://psychocats.net/ubuntu/purekde](http://psychocats.net/ubuntu/purekde)

-J

---

### Post by inobe on 2010-03-08
> **James.Lazo said:**
> Thanks for that inobe - I'll remember to use aptitude for packages I'm not sure I want to keep. I'm going to hunt around a bit more before I consider reinstalling Gnome.

I did come across this morsel, but unfortunately nothing happened when I invoked the commands...

[http://psychocats.net/ubuntu/purekde](http://psychocats.net/ubuntu/purekde)

-J

nice, looks like it even reinstalls kubuntu desktop !

```
sudo apt-get remove aisleriot alacarte app-install-data-partner apport-gtk aptdaemon at-spi binfmt-support brasero brltty-x11 capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf computer-janitor computer-janitor-gtk couchdb-bin dcraw desktop-file-utils desktopcouch devicekit-power dmz-cursor-theme doc-base docbook-xml empathy empathy-doc eog erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl esound-clients esound-common espeak espeak-data evince evolution evolution-common evolution-couchdb evolution-data-server evolution-data-server-common evolution-documentation-en evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content f-spot file-roller firefox firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support firefox-gnome-support gamin gcalctool gconf-defaults-service gconf-editor gconf2 gconf2-common gdebi gdm gdm-guest-session gedit gedit-common ggzcore-bin gimp gimp-data gksu glchess glines gnect gnibbles gnobots2 gnome-about gnome-accessibility-themes gnome-applets gnome-applets-data gnome-blackjack gnome-bluetooth gnome-codec-install gnome-control-center gnome-desktop-data gnome-disk-utility gnome-doc-utils gnome-games gnome-games-common gnome-icon-theme gnome-keyring gnome-mag gnome-mahjongg gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-session-bin gnome-session-canberra gnome-settings-daemon gnome-sudoku gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-user-guide gnome-utils gnometris gnomine gnotravex gnotski gstreamer0.10-alsa gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x gtali gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse human-theme humanity-icon-theme iagno ibus ibus-gtk ibus-m17n ibus-table indicator-applet indicator-applet-session indicator-messages indicator-session jockey-gtk language-selector launchpad-integration libanthy0 libart-2.0-2 libart2.0-cil libasound2-plugins libatspi1.0-0 libaudiofile0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbabl-0.0-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrasero-media0 libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio7 libclutter-1.0-0 libclutter-gtk-0.10-0 libcompizconfig0 libcouchdb-glib-1.0-1 libcroco3 libcryptui0 libcurl3 libdbusmenu-glib0 libdbusmenu-gtk0 libdecoration0 libdevkit-power-gobject1 libdotconf1.0 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 libempathy-common libempathy-gtk-common libempathy-gtk28 libempathy30 libesd-alsa0 libespeak1 libevdocument1 libevent-1.4-2 libevview1 libexchange-storage1.2-3 libexempi3 libflickrnet2.2-cil libfreezethaw-perl libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2-4 libgconf2.0-cil libgcr0 libgd2-xpm libgdata-common libgdata-google1.2-1 libgdata1.2-1 libgdata5 libgdict-1.0-6 libgdiplus libgdu-gtk0 libgdu0 libgegl-0.0-0 libggz2 libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2-0 libglade2.0-cil libglib-perl libglib2.0-cil libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime-2.4-2 libgmime2.2a-cil libgnome-bluetooth7 libgnome-desktop-2-11 libgnome-keyring0 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomekbd-common libgnomekbd4 libgnomekbdui4 libgnomepanel2.24-cil libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgsf-1-114 libgsf-1-common libgssdp-1.0-1 libgstfarsight0.10-0 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgupnp-1.0-2 libgupnp-igd-1.0-2 libgvfscommon0 libgweather-common libgweather1 libibus1 libidl0 libiec61883-0 libindicate-gtk1 libjson-glib-1.0-0 libkpathsea4 liblaunchpad-integration1 liblircclient0 liblouis-data liblouis0 liblpint-bonobo0 libm17n-0 libmetacity0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-i18n-west2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnice0 libnotify1 liboil0.3 liboobs-1-4 liborbit2 libotf0 libpam-gnome-keyring libpanel-applet2-0 libpango-perl libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-agent-1-0 libpolkit-gtk-1-0 libpoppler-glib4 libportaudio2 libprotobuf3 libproxy0 libpst4 libpulse-browse0 libpulse-mainloop-glib0 libpurple-bin libpurple0 librarian0 libraw1394-11 librsvg2-2 librsvg2-common libsctp1 libsexy2 libshout3 libsilc-1.1-2 libsilcclient-1.1-3 libsoup-gnome2.4-1 libsoup2.4-1 libspeechd2 libspeexdsp1 libsqlite0 libstartup-notification0 libtdb1 libtelepathy-farsight0 libtelepathy-glib0 libtie-ixhash-perl libtotem-plparser12 libtrackerclient0 libunique-1.0-0 libuuid-perl libvisual-0.4-0 libvisual-0.4-plugins libvte-common libvte9 libwebkit-1.0-2 libwebkit-1.0-common libwmf0.2-7-gtk libwnck-common libwnck22 libxcb-atom1 libxcb-aux0 libxcb-event1 libxml-twig-perl libxml-xpath-perl libxres1 libzephyr4 lksctp-tools m17n-contrib m17n-db media-player-info mesa-utils metacity metacity-common mobile-broadband-provider-info mono-2.0-gac mono-gac mono-runtime mousetweaks nautilus nautilus-data nautilus-sendto nautilus-share network-manager-gnome notification-daemon notify-osd notify-osd-icons obexd-client onboard openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-style-human pkg-config policykit-1-gnome protobuf-compiler pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11 pulseaudio-utils python-aptdaemon python-aptdaemon-gtk python-avahi python-brlapi python-cairo python-configglue python-couchdb python-crypto python-desktopcouch python-desktopcouch-records python-fstab python-gconf python-glade2 python-gmenu python-gnome2 python-gnomeapplet python-gnomecanvas python-gnomekeyring python-gst0.10 python-gtk2 python-gtksourceview2 python-ibus python-launchpad-integration python-libxml2 python-louis python-notify python-openssl python-pam python-papyon python-protobuf python-pyatspi python-pyinotify python-pyorbit python-rdflib python-rsvg python-serial python-sexy python-speechd python-telepathy python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntuone-client python-ubuntuone-storageprotocol python-virtkey python-vte python-webkit rarian-compat rhythmbox same-gnome screen-resolution-extra screensaver-default-images seahorse sgml-data software-center software-properties-gtk speech-dispatcher ssh-askpass-gnome synaptic system-config-printer-gnome system-tools-backends telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-mission-control-5 telepathy-salut tomboy totem totem-common totem-mozilla totem-plugins transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds ubuntu-system-service ubuntu-wallpapers ubuntu-xsplash-artwork ubuntuone-client ubuntuone-client-gnome update-manager update-notifier usb-creator-gtk vinagre vino whois xdg-user-dirs-gtk xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xsplash xulrunner-1.9.1 xulrunner-1.9.1-gnome-support yelp zenity && sudo apt-get install kubuntu-desktop
```


i wanted to see it in the open.

edit: lets stick it in a quote to have a better look

> sudo apt-get remove aisleriot alacarte app-install-data-partner apport-gtk aptdaemon at-spi binfmt-support brasero brltty-x11 capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf computer-janitor computer-janitor-gtk couchdb-bin dcraw desktop-file-utils desktopcouch devicekit-power dmz-cursor-theme doc-base docbook-xml empathy empathy-doc eog erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl esound-clients esound-common espeak espeak-data evince evolution evolution-common evolution-couchdb evolution-data-server evolution-data-server-common evolution-documentation-en evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content f-spot file-roller firefox firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support firefox-gnome-support gamin gcalctool gconf-defaults-service gconf-editor gconf2 gconf2-common gdebi gdm gdm-guest-session gedit gedit-common ggzcore-bin gimp gimp-data gksu glchess glines gnect gnibbles gnobots2 gnome-about gnome-accessibility-themes gnome-applets gnome-applets-data gnome-blackjack gnome-bluetooth gnome-codec-install gnome-control-center gnome-desktop-data gnome-disk-utility gnome-doc-utils gnome-games gnome-games-common gnome-icon-theme gnome-keyring gnome-mag gnome-mahjongg gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-session-bin gnome-session-canberra gnome-settings-daemon gnome-sudoku gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-user-guide gnome-utils gnometris gnomine gnotravex gnotski gstreamer0.10-alsa gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x gtali gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse human-theme humanity-icon-theme iagno ibus ibus-gtk ibus-m17n ibus-table indicator-applet indicator-applet-session indicator-messages indicator-session jockey-gtk language-selector launchpad-integration libanthy0 libart-2.0-2 libart2.0-cil libasound2-plugins libatspi1.0-0 libaudiofile0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbabl-0.0-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrasero-media0 libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio7 libclutter-1.0-0 libclutter-gtk-0.10-0 libcompizconfig0 libcouchdb-glib-1.0-1 libcroco3 libcryptui0 libcurl3 libdbusmenu-glib0 libdbusmenu-gtk0 libdecoration0 libdevkit-power-gobject1 libdotconf1.0 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 libempathy-common libempathy-gtk-common libempathy-gtk28 libempathy30 libesd-alsa0 libespeak1 libevdocument1 libevent-1.4-2 libevview1 libexchange-storage1.2-3 libexempi3 libflickrnet2.2-cil libfreezethaw-perl libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2-4 libgconf2.0-cil libgcr0 libgd2-xpm libgdata-common libgdata-google1.2-1 libgdata1.2-1 libgdata5 libgdict-1.0-6 libgdiplus libgdu-gtk0 libgdu0 libgegl-0.0-0 libggz2 libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2-0 libglade2.0-cil libglib-perl libglib2.0-cil libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime-2.4-2 libgmime2.2a-cil libgnome-bluetooth7 libgnome-desktop-2-11 libgnome-keyring0 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomekbd-common libgnomekbd4 libgnomekbdui4 libgnomepanel2.24-cil libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgsf-1-114 libgsf-1-common libgssdp-1.0-1 libgstfarsight0.10-0 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgupnp-1.0-2 libgupnp-igd-1.0-2 libgvfscommon0 libgweather-common libgweather1 libibus1 libidl0 libiec61883-0 libindicate-gtk1 libjson-glib-1.0-0 libkpathsea4 liblaunchpad-integration1 liblircclient0 liblouis-data liblouis0 liblpint-bonobo0 libm17n-0 libmetacity0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-i18n-west2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnice0 libnotify1 liboil0.3 liboobs-1-4 liborbit2 libotf0 libpam-gnome-keyring libpanel-applet2-0 libpango-perl libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-agent-1-0 libpolkit-gtk-1-0 libpoppler-glib4 libportaudio2 libprotobuf3 libproxy0 libpst4 libpulse-browse0 libpulse-mainloop-glib0 libpurple-bin libpurple0 librarian0 libraw1394-11 librsvg2-2 librsvg2-common libsctp1 libsexy2 libshout3 libsilc-1.1-2 libsilcclient-1.1-3 libsoup-gnome2.4-1 libsoup2.4-1 libspeechd2 libspeexdsp1 libsqlite0 libstartup-notification0 libtdb1 libtelepathy-farsight0 libtelepathy-glib0 libtie-ixhash-perl libtotem-plparser12 libtrackerclient0 libunique-1.0-0 libuuid-perl libvisual-0.4-0 libvisual-0.4-plugins libvte-common libvte9 libwebkit-1.0-2 libwebkit-1.0-common libwmf0.2-7-gtk libwnck-common libwnck22 libxcb-atom1 libxcb-aux0 libxcb-event1 libxml-twig-perl libxml-xpath-perl libxres1 libzephyr4 lksctp-tools m17n-contrib m17n-db media-player-info mesa-utils metacity metacity-common mobile-broadband-provider-info mono-2.0-gac mono-gac mono-runtime mousetweaks nautilus nautilus-data nautilus-sendto nautilus-share network-manager-gnome notification-daemon notify-osd notify-osd-icons obexd-client onboard openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-style-human pkg-config policykit-1-gnome protobuf-compiler pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11 pulseaudio-utils python-aptdaemon python-aptdaemon-gtk python-avahi python-brlapi python-cairo python-configglue python-couchdb python-crypto python-desktopcouch python-desktopcouch-records python-fstab python-gconf python-glade2 python-gmenu python-gnome2 python-gnomeapplet python-gnomecanvas python-gnomekeyring python-gst0.10 python-gtk2 python-gtksourceview2 python-ibus python-launchpad-integration python-libxml2 python-louis python-notify python-openssl python-pam python-papyon python-protobuf python-pyatspi python-pyinotify python-pyorbit python-rdflib python-rsvg python-serial python-sexy python-speechd python-telepathy python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntuone-client python-ubuntuone-storageprotocol python-virtkey python-vte python-webkit rarian-compat rhythmbox same-gnome screen-resolution-extra screensaver-default-images seahorse sgml-data software-center software-properties-gtk speech-dispatcher ssh-askpass-gnome synaptic system-config-printer-gnome system-tools-backends telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-mission-control-5 telepathy-salut tomboy totem totem-common totem-mozilla totem-plugins transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds ubuntu-system-service ubuntu-wallpapers ubuntu-xsplash-artwork ubuntuone-client ubuntuone-client-gnome update-manager update-notifier usb-creator-gtk vinagre vino whois xdg-user-dirs-gtk xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xsplash xulrunner-1.9.1 xulrunner-1.9.1-gnome-support yelp zenity && sudo apt-get install kubuntu-desktop

---

### Post by inobe on 2010-03-08
did you copy and paste the entire ubuntu removal command ?

---

### Post by James.Lazo on 2010-03-08
Yeah, I got it all in there. I thought about excluding the last bit on installing Kubuntu desktop as I still had it, but I left it in the command for good measure. Ah, but to no avail.

I've also tried checking gnome sound preferences because I figured that's where the sounds are coming from, but that got removed with the gnome desktop as well. If I could just find out where the sound files are, I'd happily delete them...anyway, it'll have to wait till later this week.

Thanks for keeping the suggestions coming. I'll post back with anything else I find.

Cheers,

-J

---

### Post by James.Lazo on 2010-03-09
Upon further inspection, Gnome is STILL installed much to my chagrin. I found it by way of checking the session options. Checking now, I see a bunch of gnome packages in my package manager. 

Anyway, after fooling around a bit, I found out that selecting "No Sounds" from the Gnome sounds preferences did not affect my KDE session, but selecting "Mute" for system alerts did. No more spurious mouse clicks sounds. I can sleep easy now.

-J

---

### Post by Rayaz on 2010-12-01
> **James.Lazo said:**
> 
Anyway, after fooling around a bit, I found out that selecting "No Sounds" from the Gnome sounds preferences did not affect my KDE session, but selecting "Mute" for system alerts did. No more spurious mouse clicks sounds. I can sleep easy now.

-J

Thank you, thank you, thank you so very much!! Finally I can use Chrome in peace! Thank you again and again!!

Regards

---


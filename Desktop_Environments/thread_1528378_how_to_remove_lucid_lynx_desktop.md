---
title: "how to remove lucid lynx desktop?"
date: 2010-07-10
forum: Desktop Environments
---

### Post by psihokiller4 on 2010-07-10
I've been searching but I cannot find

let me do an example so there won't be any misunderstanding

to install KDE desktop you do

```
sudo aptitude install kubuntu-desktop
```if you want to remove KDE desktop you do

```
sudo aptitude remove kubuntu-desktop
```now I'd only need command to remove ubuntu 10.04 lucid lynx original desktop environment

---

### Post by Mr_VeRiTy on 2010-07-10
> **psihokiller4 said:**
> I've been searching but I cannot find

let me do an example so there won't be any misunderstanding

to install KDE desktop you do

```
sudo aptitude install kubuntu-desktop
```if you want to remove KDE desktop you do

```
sudo aptitude remove kubuntu-desktop
```now I'd only need command to remove ubuntu 10.04 lucid lynx original desktop environment
Do you mean that you are trying to remove The Gnome desktop environment (which is the default one in ubuntu) if so, then i'd imagine that it would be by uninstalling gnome in synaptic (or whatever the KDE alternative is)

Or do you mean that you want to remove ubuntu itself, if so then formatting your drive takes care of that, but beware, formatting your drive means erasing EVERYTHING on it.

---

### Post by ST3ALTHPSYCH0 on 2010-07-10
If you look at the information that you're given when yo urun 
```

sudo apt-get remove kubuntu-desktop

```
you'll see that far less is removed than was installed.

[This](http://www.psychocats.net/ubuntu/puregnome) tells how to get back to pure Gnome.
[Here's](http://www.psychocats.net/ubuntu/purekde) the same article for KDE

---

### Post by Mr_VeRiTy on 2010-07-10
> **ST3ALTHPSYCH0 said:**
> If you look at the information that you're given when yo urun 
```

sudo apt-get remove kubuntu-desktop

```
you'll see that far less is removed than was installed.

[This](http://www.psychocats.net/ubuntu/puregnome) tells how to get back to pure Gnome.
[Here's](http://www.psychocats.net/ubuntu/purekde) the same article for KDE
Thats because kubuntu-desktop is an empty package that installs all the other required packages that are necessary for KDE to run

---

### Post by ST3ALTHPSYCH0 on 2010-07-10
> **Mr_VeRiTy said:**
> Thats because kubuntu-desktop is an empty package that installs all the other required packages that are necessary for KDE to run
Which could have something to do with me posting links that give all the packages that need removing... I didn't feel that defining the term "meta-package" would help the OP reach the desired results.

---

### Post by psihokiller4 on 2010-07-11
well I want to remove only desktop environment

well than if it has kde or gnome desktop environment than this is strange and can anyone explain me why?

first ```
sudo su
``````
aptitude remove ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 234 not  upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

``````
aptitude remove kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 234 not  upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

``````
aptitude remove xubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 234 not  upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

``````
aptitude remove edubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 234 not  upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

``````
apt-get remove ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ubuntu-desktop is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 234 not upgraded.

``````
apt-get remove kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kubuntu-desktop is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 234 not upgraded.

``````
apt-get remove xubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xubuntu-desktop is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 234 not upgraded.

``````
apt-get remove edubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package edubuntu-desktop is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 234 not upgraded.

```now I restart my PC and I'm still running in a desktop environment why?
and I need a solution to how to remove desktop environment

I can output any code you need

---

### Post by psihokiller4 on 2010-07-12
so actually noone know how to remove desktop environment on ubuntu 10.04 (lucid lynx)?

---

### Post by yossell on 2010-07-12
> **psihokiller4 said:**
> so actually noone know how to remove desktop environment on ubuntu 10.04 (lucid lynx)?

It could be that, I can't speak for everyone. But, for my own part, I don't have a clear idea of what you're trying to achieve.

Is it that you've installed a particular desktop environment, such as KDE, and you want to get rid of it, going back to a pure Gnome environment? Or vice versa? Then follow the links that St3ealth gave in his original post, and follow the instructions.

Or are you trying to do something radical - all desktop environments, Gnome, KDE, the lot of them? And be left with - what? No Ubuntu at all? Or do you envisage a minimal install, a kind of pure terminal interface?

Perhaps if you said more about what you wanted to achieve, and why the questions you've already been asked and the suggestions that have been made don't cut it for you, people could give you more helpful advice.

---

### Post by darolu on 2010-07-12
So what you want is to start in command-line mode? You can do it by removing/renaming the gdm file in /etc/init.d/:
```
sudo mv /etc/init.d/gdm gdm-disabled
```
If you want a completely GUI-free OS, I suggest you to download and install the server edition.

**Edit:** removing/renaming /etc/init.d/gdm does no longer work in 10.04; I believe because it uses DeviceKit instead of HAL now or the use of Plymouth; it seems to startX before loading init.d scripts ??; I have no idea how to prevent it to startX now. A custom initrd.img may be needed.

---

### Post by ST3ALTHPSYCH0 on 2010-07-12
If you want a CLI you could just hit ctrl+alt+F1 at the login screen

---

### Post by psihokiller4 on 2010-07-18
I tried everything no luck

well what I want to do is remove desktop environment as I hate that new look in lucid lynx so that when I login I'll start in console
I could did it perfectly with ubuntu 10,04 server edition as it's 64 bit and it starts in console and I installed desktop of my choice
but here on laptop I cannot do that as it's already included so I want to get rid of this stupid look first

and I want to get rid of too much used space for that desktop environment
I don't want to switch to console I want to remove desktop environment.

---

### Post by ST3ALTHPSYCH0 on 2010-07-18
You may have to boot into your preferred DE in order to remove Gnome.

---

### Post by Mr_VeRiTy on 2010-08-04
If you still haven't removed gnome yet, here's what you do:

Boot up your computer and log into a kde session (do not use a gnome session), open a konsole (is that what you call it in kde?) and enter:
```
sudo apt-get remove adium-theme-ubuntu aisleriot alacarte app-install-data-partner apport-gtk aptdaemon at-spi binfmt-support binutils bluez-gstreamer branding-ubuntu brasero brasero-common brltty-x11 capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf computer-janitor computer-janitor-gtk couchdb-bin dcraw desktop-file-utils desktopcouch dmz-cursor-theme doc-base docbook-xml empathy empathy-common eog erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl esound-clients esound-common espeak espeak-data evince evolution evolution-common evolution-couchdb evolution-data-server evolution-data-server-common evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content f-spot file-roller firefox firefox-branding firefox-gnome-support gamin gbrainy gcalctool gcc gcc-4.4 gconf-defaults-service gconf-editor gdebi gdm gdm-guest-session gedit gedit-common gksu gnome-about gnome-accessibility-themes gnome-applets gnome-applets-data gnome-bluetooth gnome-codec-install gnome-control-center gnome-desktop-data gnome-disk-utility gnome-doc-utils gnome-games-common gnome-icon-theme gnome-mag gnome-mahjongg gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-power-manager gnome-screensaver gnome-session gnome-session-bin gnome-session-canberra gnome-settings-daemon gnome-sudoku gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-user-guide gnome-user-share gnome-utils gnomine gstreamer0.10-alsa gstreamer0.10-gnonlin gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse gwibber gwibber-service humanity-icon-theme ibus ibus-gtk ibus-m17n ibus-table imagemagick indicator-applet indicator-applet-session indicator-application indicator-me indicator-messages indicator-session indicator-sound jockey-gtk language-selector launchpad-integration libanthy0 libappindicator0 libart-2.0-2 libart2.0-cil libasound2-plugins libatspi1.0-0 libaudiofile0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrasero-media0 libc-dev-bin libc6-dev libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio10 libclutter-1.0-0 libclutter-gtk-0.10-0 libcompizconfig0 libcouchdb-glib-1.0-2 libcroco3 libcryptui0 libcurl3 libdbusmenu-gtk1 libdecoration0 libdesktopcouch-glib-1.0-2 libdevkit-power-gobject1 libdotconf1.0 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 libesd0 libespeak1 libevdocument2 libevent-1.4-2 libevview2 libexchange-storage1.2-3 libexempi3 libflickrnet2.2-cil libfreezethaw-perl libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2.0-cil libgd2-xpm libgdata-common libgdata-google1.2-1 libgdata1.2-1 libgdata6 libgdict-1.0-6 libgdiplus libgdu-gtk0 libgdu0 libgksu2-0 libglade2.0-cil libglib-perl libglib2.0-cil libglib2.0-data libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.4-2 libgmime2.4-cil libgnome-bluetooth7 libgnome-desktop-2-17 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomekbd-common libgnomekbd4 libgnomepanel2.24-cil libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgoocanvas-common libgoocanvas3 libgraphviz4 libgsf-1-114 libgsf-1-common libgssdp-1.0-2 libgstfarsight0.10-0 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgupnp-1.0-3 libgupnp-igd-1.0-2 libgvfscommon0 libgweather-common libgweather1 libibus1 libido-0.1-0 libiec61883-0 libindicate-gtk2 libindicator0 libjson-glib-1.0-0 libkpathsea5 liblaunchpad-integration1 liblaunchpad-integration1.0-cil liblircclient0 liblouis-data liblouis0 liblpint-bonobo0 libm17n-0 libmagickcore2-extra libmetacity-private0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-i18n-west2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-runtime2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnice0 libnotify1 libnunit2.4-cil liboil0.3 liboobs-1-4 libotf0 libpanel-applet2-0 libpango-perl libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-gtk-1-0 libpoppler-glib4 libportaudio2 libprotobuf5 libprotoc5 libproxy0 libpst4 libpulse-browse0 libpurple-bin libpurple0 librarian0 libraw1394-11 librsvg2-2 librsvg2-common libsctp1 libsdl1.2debian-pulseaudio libsexy2 libshout3 libsilc-1.1-2 libsilcclient-1.1-3 libsoup-gnome2.4-1 libsoup2.4-1 libspeechd2 libspeexdsp1 libsqlite0 libstartup-notification0 libtdb1 libtelepathy-farsight0 libtelepathy-glib0 libtie-ixhash-perl libtotem-plparser17 libubuntuone-1.0-1 libunique-1.0-0 libupower-glib1 libuuid-perl libvisual-0.4-0 libvisual-0.4-plugins libvte-common libvte9 libwebkit-1.0-2 libwebkit-1.0-common libwmf0.2-7 libwmf0.2-7-gtk libwnck-common libwnck22 libxcb-atom1 libxcb-aux0 libxcb-event1 libxml-twig-perl libxml-xpath-perl libxres1 libzephyr4 light-themes linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic linux-headers-generic linux-libc-dev lksctp-tools m17n-contrib m17n-db manpages-dev media-player-info metacity metacity-common mobile-broadband-provider-info mono-2.0-gac mono-gac mono-runtime mousetweaks nautilus nautilus-data nautilus-sendto nautilus-sendto-empathy nautilus-share network-manager-gnome notification-daemon notify-osd notify-osd-icons obexd-client onboard openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-style-human pitivi pkg-config plymouth-theme-ubuntu-logo policykit-1-gnome protobuf-compiler pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils python-appindicator python-aptdaemon python-aptdaemon-gtk python-avahi python-brlapi python-cairo python-configglue python-couchdb python-crypto python-desktopcouch python-desktopcouch-records python-egenix-mxdatetime python-egenix-mxtools python-farsight python-fstab python-gconf python-glade2 python-gmenu python-gnome2 python-gnomeapplet python-gnomecanvas python-gnomekeyring python-gst0.10 python-gtk2 python-gtksourceview2 python-gtkspell python-ibus python-indicate python-launchpad-integration python-libxml2 python-louis python-mako python-notify python-openssl python-pam python-papyon python-protobuf python-pyatspi python-pycurl python-pygoocanvas python-pyinotify python-pyorbit python-rdflib python-serial python-speechd python-telepathy python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntuone python-ubuntuone-client python-ubuntuone-storageprotocol python-virtkey python-vte python-webkit python-wnck quadrapassel rarian-compat rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone-music-store rtkit screen-resolution-extra screensaver-default-images scrollkeeper seahorse sgml-data simple-scan software-center software-properties-gtk speech-dispatcher ssh-askpass-gnome synaptic system-config-printer-gnome system-tools-backends telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-mission-control-5 telepathy-salut tomboy totem totem-common totem-mozilla totem-plugins transmission-common transmission-gtk tsclient ttf-liberation ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-sounds ubuntu-system-service ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome update-manager update-notifier upower usb-creator-gtk vinagre vino whois xdg-user-dirs-gtk xscreensaver-data xscreensaver-gl xsltproc xulrunner-1.9.2 yelp zenity && sudo apt-get install kubuntu-desktop
```
this will remove gnome, and leave you with KDE, it might remove some packages that you want to keep, so make a note to re-install them later. Though if you wanted kde by default, then why did you not just install Kubuntu instead of Ubuntu, anyways hope that solves your problem.

---

### Post by ashokmkd on 2010-08-04
hey buddy, just note down which packages are used for gnome and then switch to recovery console and remove them using apt-get.

---

### Post by psihokiller4 on 2010-08-07
well I have moved to arch now and I'm not bugging with ubuntu any more

maybe it would help maybe it wouldn't maybe when I'll have more time I'll look in to it again
but for now I'll make it for solved

---


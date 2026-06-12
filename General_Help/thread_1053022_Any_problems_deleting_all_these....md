---
title: "Any problems deleting all these?..."
date: 2009-01-28
forum: General Help
---

### Post by r0g on 2009-01-28
Hi There,

I'm working on a very light console only live-cd remaster, as such I don't need gnome or x-windows, or indeed much else other that samba, python, tftp and SSH so... with that in mind, can anyone see anything amongst this lot that I _really_ shouldn't remove?

I'm not v.sure about...
app-install-data
ttf-arphic-uming
linux-ubuntu-modules-2.6.24-19-generic
...or the mono stuff. Does any console based stuff use mono?

Anyway I was thinking of saving 1.5Gb by losing the following...

110392	openoffice.org-core
91220	evolution-common
55604	ubuntu-docs
53680	wine
46048	linux-restricted-modules-2.6.24-16-generic
37176	gnome-games-data
36748	openoffice.org-common
34296	libgl1-mesa-dri
27952	gimp-data
27080	gimp-help-common
26920	openoffice.org-help-en-us
26564	openoffice.org-help-en-gb
26052	gnome-applets-data
24936	gnome-user-guide
21436	gnome-icon-theme
21228	openoffice.org-thesaurus-en-us
21208	app-install-data
21176	openoffice.org-thesaurus-en-au
21160	ttf-arphic-uming
20836	xulrunner-1.9
20420	openoffice.org-writer
20356	pidgin-data
19676	libgweather-common
17008	libgtk2.0-common
15936	gdm
15412	openoffice.org-calc
15280	linux-ubuntu-modules-2.6.24-19-generic
14652	nautilus-data
14632	ekiga
14056	gnome-panel-data
13180	rhythmbox
12888	gedit-common
12648	gnome-utils
12508	gnome-power-manager
12204	foomatic-db
11928	metacity-common
11756	libmagick10
11184	seahorse
11052	example-content
10884	xserver-xorg-core
10744	gnome-terminal-data
10668	gimp
10648	hplip-data
10164	tomboy
9896	cupsys
9104	f-spot
8996	ttf-kochi-mincho
8836	libopal-2.2
8800	capplets-data
8692	texlive-base-bin
8652	locales
8588	libsane
8436	gnome-system-tools
8344	evolution
8312	xfonts-base
8144	compiz-fusion-plugins-extra
8036	gimp-help-en
7936	compiz-fusion-plugins-main
7856	evolution-data-server-common
7824	ttf-kochi-gothic
7464	openoffice.org-draw
7004	dpkg
6896	openoffice.org-l10n-en-gb
6868	libgs8
6808	gcalctool
6788	gnome-system-monitor
6660	totem-common
6384	gnome-orca
6368	openoffice.org-style-human
6276	evince
6200	tzdata
6036	gconf2-common
6012	synaptic
6012	gnome-media-common
5956	eog
5736	brltty
5732	rss-glx
5628	openprinting-ppds
5600	cpp-4.2
5436	foo2zjs
5228	cupsys-common
5096	openoffice.org-l10n-en-za
5080	file-roller
5036	brasero
4972	libgtk2.0-0
4896	xfonts-100dpi
4872	sound-juicer
4844	python-gtk2
4792	gsfonts
4664	xscreensaver-gl
4644	libgnome2-common
4564	xfonts-75dpi
4304	zenity
4280	libpurple0
4248	gnome-screensaver
4220	diveintopython
4184	libgtkmm-2.4-1c2a
4156	gucharmap
4144	libgphoto2-2
4136	deskbar-applet
4128	libgtk2.0-cil
4108	libquicktimecv
4032	libgtk2-perl
4028	libmono-system2.0-cil
3976	libgnomevfs2-common
3964	yelp
3928	xkb-data
3848	xcursor-themes
3748	scrollkeeper
3716	ubuntu-wallpapers
3620	human-icon-theme
3584	firefox-3.0
3528	libgimp2.0
3528	ghostscript
3520	dmz-cursor-theme
3500	gnome-doc-utils
3484	libpt-1.10.10
3468	tangerine-icon-theme
3460	libgucharmap6
3444	ttf-freefont
3436	gnome-desktop-data
3408	evolution-exchange
3372	ubuntu-gdm-themes
3320	libgnomeui-common
3308	ubuntu-sounds
3276	gnome-themes
3140	xsane-common
3140	gnome-volume-manager
3120	libtotem-plparser10
3116	libgtkhtml3.14-19
3048	vinagre
2968	nautilus-cd-burner
2944	libgtksourceview2.0-common
2932	gnome-session
2888	gnome-settings-daemon
2864	fast-user-switch-applet
2760	ttf-thai-tlwg
2748	gstreamer0.10-plugins-good
2728	bug-buddy
2676	libmono-system1.0-cil
2656	gnome-games
2644	openoffice.org-impress
2596	openoffice.org-base-core
2516	libmono-corlib2.0-cil
2512	vino
2508	gnome-keyring
2508	gnome-app-install
2484	gnome-nettool
2476	shared-mime-info
2460	ttf-dejavu-core
2460	libgtksourceview-common
2428	gconf-editor
2412	libaspell15
2396	gnome-netstatus-applet
2388	libbonoboui2-common
2384	libmono-system-web2.0-cil
2336	gnome-pilot
2324	libgutenprint2
2276	language-pack-gnome-en-base
2260	transmission-gtk
2196	nautilus
2160	libgstreamer0.10-0
2144	libdjvulibre15
2124	libmono0
2072	libmono-corlib1.0-cil
2008	libx11-data

Thanks v.much if you've made it through all that! :-)

Roger.

---

### Post by Nepherte on 2009-01-28
On a side node: perhaps you should consider using something different than ubuntu? Preferable a system that you build yourself from the bottom up? Something like Arch Linux.

---

### Post by r0g on 2009-01-28
> **Nepherte said:**
> On a side node: perhaps you should consider using something different than ubuntu? Preferable a system that you build yourself from the bottom up? Something like Arch Linux.

Yeah, I spent a good chunk of yesterday researching other options but I decided to trim down a system that already does everything I need rather than build upwards.  I need reliable NTFS, kickass hardware detection and debian packages for starters. I considered building up from Ubuntu Mini but at < 10Meg I can't see it having great driver support. I also considered DSL but I wanted a 2.6 kernel and DSL-N has been stalled at RC3 for years so I don't have much faith in it. Another big factor was that I use Ubuntu on my desktop and there's way more info/tutorials/help for Ubuntu than any other distro now.

---

### Post by Nepherte on 2009-01-28
This command is supposed to remove gnome:
```
sudo apt-get remove alacarte app-install-data-commercial apport-gtk apturl at-spi binfmt-support bluez-gnome brasero brltty-x11 capplets-data cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet desktop-file-utils dmz-cursor-theme doc-base docbook-xml ekiga eog espeak espeak-data evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet file-roller firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support gamin gcalctool gconf-editor gconf2 gconf2-common gdebi gdm gdm-guest-session gedit gedit-common ggzcore-bin gimp gimp-data gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-cards-data gnome-control-center gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-mount gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-settings-daemon gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse human-icon-theme human-theme hwtest hwtest-gtk jockey-gtk language-selector libart2.0-cil libasound2-plugins libatspi1.0-0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbabl-0.0-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gnome libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio7 libcompizconfig0 libcryptui0 libdecoration0 libdeskbar-tracker libdmx1 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libespeak1 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libfreezethaw-perl libgadu3 libgail-gnome-module libgamin0 libgconf2-4 libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libgdiplus libgegl-0.0-0 libggz2 libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2-0 libglade2.0-cil libglew1.5 libglib-perl libglib2.0-cil libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime2.2-cil libgnome-desktop-2-7 libgnome-keyring0 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-speech7 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomekbd-common libgnomekbd3 libgnomekbdui3 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgpod3 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkglext1 libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml2-0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview-common libgtksourceview1.0-0 libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgvfscommon0 libgweather-common libgweather1 libhesiod0 libidl0 libiec61883-0 libjpeg-progs libkpathsea4 liblaunchpad-integration1 liblircclient0 liblpint-bonobo0 libmbca0 libmeanwhile1 libmetacity0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-i18n1.0-cil libmono-i18n2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libnautilus-burn4 libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnotify1 liboil0.3 liboobs-1-4 libopal-2.2 libopenobex1 liborbit2 libpam-gnome-keyring libpanel-applet2-0 libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-gnome0 libpoppler-glib3 libportaudio0 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpulse-browse0 libpulsecore5 libpurple-bin libpurple0 librarian0 librsvg2-common libschroedinger-1.0-0 libscim8c2a libsexy2 libshout3 libsilc-1.1-2 libsndfile1 libsoup2.4-1 libspeexdsp1 libsqlite0 libstartup-notification0 libtie-ixhash-perl libtotem-plparser12 libtracker-gtk0 libtrackerclient0 libuuid-perl libv4l-0 libvte-common libvte9 libwnck-common libwnck22 libwv-1.2-3 libx11-xcb1 libxevie1 libxml-twig-perl libxml-xpath-perl libxml2-utils libxres1 libzephyr3 metacity metacity-common mobile-broadband-provider-info mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share network-manager-gnome notification-daemon obex-data-server onboard openoffice.org-gnome openoffice.org-gtk pidgin pidgin-data pidgin-otr pkg-config policykit-gnome pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils python-beagle python-brlapi python-cairo python-gconf python-gdata python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnomecanvas python-gst0.10 python-gtk2 python-gtkhtml2 python-gtksourceview2 python-launchpad-integration python-notify python-numeric python-pkg-resources python-pyatspi python-pyorbit python-rdflib python-sexy python-virtkey python-vte rarian-compat rhythmbox rss-glx scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket screen-resolution-extra screensaver-default-images seahorse seahorse-plugins sgml-data software-properties-gtk sqlite sqlite3 ssh-askpass-gnome synaptic syslinux system-config-printer-gnome system-tools-backends tangerine-icon-theme tomboy totem totem-common totem-gstreamer totem-mozilla totem-plugins tracker tracker-search-tool tracker-utils transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-gdm-themes ubuntu-sounds ubuntu-system-service ubuntu-wallpapers untex update-manager update-notifier usb-creator vinagre vino whois wv xbase-clients xbitmaps xdg-user-dirs-gtk xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xterm xulrunner-1.9 xulrunner-1.9-gnome-support yelp zenity
```
Taken from [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by directhex on 2009-01-28
Why not start with the Ubuntu Server CD, which has a rather more minimal base install?

As for the Mono stuff, no, the only Mono apps on a standard Ubuntu system are Tomboy & F-Spot, which are both Gnome apps

---

### Post by r0g on 2009-01-28
> **Nepherte said:**
> This command is supposed to remove gnome:
```
sudo apt-get remove alacarte app-install-data-commercial apport-gtk apturl at-spi binfmt-support bluez-gnome brasero brltty-x11 capplets-data cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet desktop-file-utils dmz-cursor-theme doc-base docbook-xml ekiga eog espeak espeak-data evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet file-roller firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support gamin gcalctool gconf-editor gconf2 gconf2-common gdebi gdm gdm-guest-session gedit gedit-common ggzcore-bin gimp gimp-data gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-cards-data gnome-control-center gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-mount gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-settings-daemon gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse human-icon-theme human-theme hwtest hwtest-gtk jockey-gtk language-selector libart2.0-cil libasound2-plugins libatspi1.0-0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbabl-0.0-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gnome libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio7 libcompizconfig0 libcryptui0 libdecoration0 libdeskbar-tracker libdmx1 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libespeak1 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libfreezethaw-perl libgadu3 libgail-gnome-module libgamin0 libgconf2-4 libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libgdiplus libgegl-0.0-0 libggz2 libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2-0 libglade2.0-cil libglew1.5 libglib-perl libglib2.0-cil libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime2.2-cil libgnome-desktop-2-7 libgnome-keyring0 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-speech7 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomekbd-common libgnomekbd3 libgnomekbdui3 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgpod3 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkglext1 libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml2-0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview-common libgtksourceview1.0-0 libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgvfscommon0 libgweather-common libgweather1 libhesiod0 libidl0 libiec61883-0 libjpeg-progs libkpathsea4 liblaunchpad-integration1 liblircclient0 liblpint-bonobo0 libmbca0 libmeanwhile1 libmetacity0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-i18n1.0-cil libmono-i18n2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libnautilus-burn4 libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnotify1 liboil0.3 liboobs-1-4 libopal-2.2 libopenobex1 liborbit2 libpam-gnome-keyring libpanel-applet2-0 libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-gnome0 libpoppler-glib3 libportaudio0 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpulse-browse0 libpulsecore5 libpurple-bin libpurple0 librarian0 librsvg2-common libschroedinger-1.0-0 libscim8c2a libsexy2 libshout3 libsilc-1.1-2 libsndfile1 libsoup2.4-1 libspeexdsp1 libsqlite0 libstartup-notification0 libtie-ixhash-perl libtotem-plparser12 libtracker-gtk0 libtrackerclient0 libuuid-perl libv4l-0 libvte-common libvte9 libwnck-common libwnck22 libwv-1.2-3 libx11-xcb1 libxevie1 libxml-twig-perl libxml-xpath-perl libxml2-utils libxres1 libzephyr3 metacity metacity-common mobile-broadband-provider-info mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share network-manager-gnome notification-daemon obex-data-server onboard openoffice.org-gnome openoffice.org-gtk pidgin pidgin-data pidgin-otr pkg-config policykit-gnome pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils python-beagle python-brlapi python-cairo python-gconf python-gdata python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnomecanvas python-gst0.10 python-gtk2 python-gtkhtml2 python-gtksourceview2 python-launchpad-integration python-notify python-numeric python-pkg-resources python-pyatspi python-pyorbit python-rdflib python-sexy python-virtkey python-vte rarian-compat rhythmbox rss-glx scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket screen-resolution-extra screensaver-default-images seahorse seahorse-plugins sgml-data software-properties-gtk sqlite sqlite3 ssh-askpass-gnome synaptic syslinux system-config-printer-gnome system-tools-backends tangerine-icon-theme tomboy totem totem-common totem-gstreamer totem-mozilla totem-plugins tracker tracker-search-tool tracker-utils transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-gdm-themes ubuntu-sounds ubuntu-system-service ubuntu-wallpapers untex update-manager update-notifier usb-creator vinagre vino whois wv xbase-clients xbitmaps xdg-user-dirs-gtk xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xterm xulrunner-1.9 xulrunner-1.9-gnome-support yelp zenity
```
Taken from [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

Ah, lovely, thanks for that :-)

---

### Post by r0g on 2009-01-28
> **directhex said:**
> Why not start with the Ubuntu Server CD, which has a rather more minimal base install?

Yeah, considered that for a while but I need to start with a live CD really and, from what I remember, the server edition boots into an installer.


> **directhex said:**
> As for the Mono stuff, no, the only Mono apps on a standard Ubuntu system are Tomboy & F-Spot, which are both Gnome apps

Good good, I wondered who the hell used mono!

---


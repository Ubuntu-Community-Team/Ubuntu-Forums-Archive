---
title: "[SOLVED] Switch To KDE 4"
date: 2008-07-19
forum: Desktop Environments
---

### Post by adrian007 on 2008-07-19
Hello all. 

i would like to switch to kde 4 completely and remove the ubuntu desktop.

however once installed kde 4 i need to remove gnome. but when i select to remove the ubuntu-desktop package it only removes the meta package. 

how do i remove all of the ubuntu desktop and only be left with kde 4

Thanks :):):)

---

### Post by damis648 on 2008-07-19
I wouldn't recommend KD4, but that is just a choice. To install kde4, run
```
sudo apt-get install kubuntu-kde4-desktop
``` in terminal. I do not think it is possible to remove all of gnome, though. Sorry.

---

### Post by adrian007 on 2008-07-19
thanks 

but is there a way i can remove most of gnome 

i just want to have no gnome stuff on my kde menu and want to save up most of the disk space


if possible i would not like to have gnome displayed on the session menu

---

### Post by adrian007 on 2008-07-19
Nevrmind i found it:

here is the code:```
sudo apt-get remove alacarte app-install-data-commercial apport-gtk apturl at-spi bluez-gnome brasero brltty brltty-x11 bug-buddy capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet desktop-file-utils displayconfig-gtk diveintopython dmz-cursor-theme doc-base docbook-xml ekiga eog espeak espeak-data evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet file-roller firefox firefox-3.0 firefox-3.0-gnome-support firefox-gnome-support gamin gcalctool gconf-editor gconf2 gconf2-common gdebi gdebi-core gdm gedit gedit-common gimp gimp-data gimp-gnomevfs gimp-python gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-cards-data gnome-control-center gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-mount gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-settings-daemon gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gtk2-engines-ubuntulooks gtkhtml3.14 gucharmap guile-1.6-libs gvfs gvfs-backends gvfs-fuse human-icon-theme human-theme hwtest hwtest-gtk jockey-gtk language-selector libalut0 libao2 libart2.0-cil libatspi1.0-0 libavahi-glib1 libavahi-ui0 libavc1394-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrlapi0.5 libcairo-perl libcairomm-1.0-1 libcamel1.2-11 libcdio-cdda0 libcdio-paranoia0 libcdio7 libcompizconfig0 libdecoration0 libdeskbar-tracker libdmx1 libdv4 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libespeak1 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libgadu3 libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2-4 libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libggz2 libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2-0 libglade2.0-cil libglew1.5 libglib-perl libglib2.0-cil libglibmm-2.4-1c2a libgmime-2.0-2 libgmime2.2-cil libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-speech7 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomekbd-common libgnomekbd2 libgnomekbdui2 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgpod-common libgpod3 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-bin libgtk2.0-cil libgtkhtml2-0 libgtkhtml3.14-19 libgtkhtml3.16-cil libgtkmm-2.4-1c2a libgtksourceview-common libgtksourceview1.0-0 libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap6 libguile-ltdl-1 libgvfscommon0 libgweather-common libgweather1 libhesiod0 libidl0 libiec61883-0 libkpathsea4 liblaunchpad-integration1 liblircclient0 liblpint-bonobo0 libmeanwhile1 libmetacity0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libmtp7 libnautilus-burn4 libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnm-glib0 libnotify1 liboil0.3 liboobs-1-4 libopal-2.2 libopenal0a libopenobex1 liborbit2 libotr2 libpam-gnome-keyring libpanel-applet2-0 libpisock9 libpisync1 libpolkit-gnome0 libpoppler-glib2 libportaudio0 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpulse-browse0 libpulsecore5 libpurple0 libqthreads-12 librarian0 libraw1394-8 librsvg2-common libsamplerate0 libscrollkeeper0 libsexy2 libsgutils1 libshout3 libsndfile1 libsoup2.4-1 libstartup-notification0 libtotem-plparser10 libtracker-gtk0 libtrackerclient0 libvisual-0.4-0 libvte-common libvte9 libwnck-common libwnck22 libx11-xcb1 libxevie1 libxml-twig-perl libxml2-utils libxres1 libzephyr3 mesa-utils metacity metacity-common mono-common mono-gac mono-jit mono-runtime mousetweaks nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share network-manager-gnome notification-daemon o3read obex-data-server onboard openoffice.org-gnome openoffice.org-gtk pidgin pidgin-data pidgin-otr pkg-config policykit-gnome pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils python-brlapi python-cairo python-gconf python-gdata python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnomecanvas python-gst0.10 python-gtk2 python-gtkhtml2 python-gtksourceview2 python-launchpad-integration python-notify python-numeric python-pyatspi python-pyorbit python-sexy python-virtkey python-vte rdesktop rhythmbox rss-glx scim scim-bridge-client-gtk scim-gtk2-immodule screensaver-default-images scrollkeeper seahorse sgml-base sgml-data software-properties-gtk sound-juicer sqlite sqlite3 ssh-askpass-gnome synaptic system-config-printer-gnome system-tools-backends tangerine-icon-theme tomboy totem totem-common totem-gstreamer totem-mozilla totem-plugins tracker tracker-search-tool transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-gdm-themes ubuntu-sounds ubuntu-wallpapers update-manager update-notifier usplash-theme-ubuntu vinagre vino whois xcursor-themes xdg-user-dirs-gtk xml-core xsane xsane-common xscreensaver-data xscreensaver-gl xsltproc xulrunner-1.9 xulrunner-1.9-gnome-support yelp zenity
```

IS THIS THE CORRECT WAY OF DOING IT!!!!!!!



P.S Is This A 100% SAFE TO PERFORM

---

### Post by damis648 on 2008-07-19
That will remove those applications listed. You can try it if you want, and if it causes problems, run the same command replacing remove with install.

---

### Post by kkjaergaard on 2008-07-19
> **adrian007 said:**
> Nevrmind i found it:

here is the code:```
sudo apt-get remove alacarte app-install-data-commercial apport-gtk...
```

IS THIS THE CORRECT WAY OF DOING IT!!!!!!!

I guess not. I *think* (think, not know) that most of the GNOME applications are installed because of the ubuntu-desktop package. I *guess* installing kubuntu-kde4-desktop and removing ubuntu-desktop and it's dependencies will actually remove all GNOME apps.

---

### Post by adrian007 on 2008-07-19
Thanks.

I did it. i now only have kde 4 and no problems




THANKS

:):):):):)

---


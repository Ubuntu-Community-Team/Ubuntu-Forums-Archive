---
title: "Hardy Bugs - Places menu broken and desktop icons gone after update."
date: 2009-03-09
forum: General Help
---

### Post by AvesCorax on 2009-03-09
My girlfriend updated her Hardy machine a week or so ago using the update manager and something in there broke gnome.  All icons on the desktop vanished, and more frustratingly, the places menu does not work.  Everything that was in there before is still there, but none of the shortcuts actually work.  Her file system is still intact, and she can browse it through OpenOffice's open/save menus and access her files.  I've checked around and seen some discussion on the desktop half of the problem, but the usually solution (sudo apt-get install --reinstall ubuntu-desktop) didn't get us anywhere.  So first off, is anyone familiar with this problem?  And secondly, is there a simple way to roll-back updates in this sort of situation?

---

### Post by prince_niceguy on 2009-03-10
try resetting her gnome settings like [here]("http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/") 

hope that resolves the issue.

---

### Post by heindsight on 2009-03-10
> **prince_niceguy said:**
> try resetting her gnome settings like [here]("http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/") 

hope that resolves the issue.

That link recommends permanently deleting all your gnome settings by doing:
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```
I'm not sure that's such a good idea - you might just lose something you'll regret later. Much safer would be to do:
```
mv .gnome .gnome2 .gconf .gconfd .metacity old_gnome_conf
```
which would move all your old gnome configuration directories into a new directory called old_gnome_conf. This way you can restore all or some of your old configuration if you want/need to.

---

### Post by AvesCorax on 2009-03-10
> **heindsight said:**
> 
```
mv .gnome .gnome2 .gconf .gconfd .metacity old_gnome_conf
```
which would move all your old gnome configuration directories into a new directory called old_gnome_conf. This way you can restore all or some of your old configuration if you want/need to.

I tried that path, and logged out and back in.  It was successful in clearing her old gui settings but didn't fix the problem.  Thanks for the tip, though.

Any other ideas?

---

### Post by AvesCorax on 2009-03-10
Alright, after poking around a bit it seems that this problem goes a bit deeper.  Nautilus wasn't loading anything in her file system, so I gave it a reinstall.  No dice.  So I installed Konqueror as a temporary workaround but I get the same result - I get an "opening Konqueror" bit on the task bar that eventually gives up and goes away without producing any result.  The file system is still there, and I can access it through the terminal, limited only by my unfamiliarity with the command line.

---

### Post by prince_niceguy on 2009-03-11
trying removing everything related to gnome and again reinstall ubuntu-desktop,  do the following

```
sudo apt-get --purge remove alacarte app-install-data-commercial apport-gtk apturl at-spi binfmt-support bluez-gnome brasero brltty-x11 capplets-data cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet desktop-file-utils dmz-cursor-theme doc-base docbook-xml ekiga eog espeak espeak-data evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet file-roller firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support gamin gcalctool gconf-editor gconf2 gconf2-common gdebi gdm gdm-guest-session gedit gedit-common ggzcore-bin gimp gimp-data gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-cards-data gnome-control-center gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-mount gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-settings-daemon gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse human-icon-theme human-theme hwtest hwtest-gtk jockey-gtk language-selector libart2.0-cil libasound2-plugins libatspi1.0-0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbabl-0.0-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gnome libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio7 libcompizconfig0 libcryptui0 libdecoration0 libdeskbar-tracker libdmx1 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libespeak1 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libfreezethaw-perl libgadu3 libgail-gnome-module libgamin0 libgconf2-4 libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libgdiplus libgegl-0.0-0 libggz2 libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2-0 libglade2.0-cil libglew1.5 libglib-perl libglib2.0-cil libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime2.2-cil libgnome-desktop-2-7 libgnome-keyring0 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-speech7 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomekbd-common libgnomekbd3 libgnomekbdui3 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgpod3 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkglext1 libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml2-0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview-common libgtksourceview1.0-0 libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgvfscommon0 libgweather-common libgweather1 libhesiod0 libidl0 libiec61883-0 libjpeg-progs libkpathsea4 liblaunchpad-integration1 liblircclient0 liblpint-bonobo0 libmbca0 libmeanwhile1 libmetacity0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-i18n1.0-cil libmono-i18n2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libnautilus-burn4 libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnotify1 liboil0.3 liboobs-1-4 libopal-2.2 libopenobex1 liborbit2 libpam-gnome-keyring libpanel-applet2-0 libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-gnome0 libpoppler-glib3 libportaudio0 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpulse-browse0 libpulsecore5 libpurple-bin libpurple0 librarian0 librsvg2-common libschroedinger-1.0-0 libscim8c2a libsexy2 libshout3 libsilc-1.1-2 libsndfile1 libsoup2.4-1 libspeexdsp1 libsqlite0 libstartup-notification0 libtie-ixhash-perl libtotem-plparser12 libtracker-gtk0 libtrackerclient0 libuuid-perl libv4l-0 libvte-common libvte9 libwnck-common libwnck22 libwv-1.2-3 libx11-xcb1 libxevie1 libxml-twig-perl libxml-xpath-perl libxml2-utils libxres1 libzephyr3 metacity metacity-common mobile-broadband-provider-info mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share network-manager-gnome notification-daemon obex-data-server onboard openoffice.org-gnome openoffice.org-gtk pidgin pidgin-data pidgin-otr pkg-config policykit-gnome pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils python-beagle python-brlapi python-cairo python-gconf python-gdata python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnomecanvas python-gst0.10 python-gtk2 python-gtkhtml2 python-gtksourceview2 python-launchpad-integration python-notify python-numeric python-pkg-resources python-pyatspi python-pyorbit python-rdflib python-sexy python-virtkey python-vte rarian-compat rhythmbox rss-glx scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket screen-resolution-extra screensaver-default-images seahorse seahorse-plugins sgml-data software-properties-gtk sqlite sqlite3 ssh-askpass-gnome synaptic syslinux system-config-printer-gnome system-tools-backends tangerine-icon-theme tomboy totem totem-common totem-gstreamer totem-mozilla totem-plugins tracker tracker-search-tool tracker-utils transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-gdm-themes ubuntu-sounds ubuntu-system-service ubuntu-wallpapers untex update-manager update-notifier usb-creator vinagre vino whois wv xbase-clients xbitmaps xdg-user-dirs-gtk xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xterm xulrunner-1.9 xulrunner-1.9-gnome-support yelp zenity
```

and install ubuntu desktop

```
sudo aptitude install ubuntu-desktop
```

---

### Post by AvesCorax on 2009-03-13
I ended up solving the problem through a variation of prince_niceguy's advice.  apt-get was aborting completely whenever it hit something it couldn't find, so I ended up marking all of the installed gnome packages for reinstall through aptitude.  Thanks for the help!

---


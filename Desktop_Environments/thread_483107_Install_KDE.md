---
title: "Install KDE"
date: 2007-06-24
forum: Desktop Environments
---

### Post by cuervo_jones_85 on 2007-06-24
Ok i used search but couldnt find any post that showed how to install KDE on ubuntu...
so how do i do it?

---

### Post by bkorb on 2007-06-24
If you haven't ``apt-get install kde'', you need to start with that.  I've done that, but I'm here now because I am instantly logged out using my original KDE home directory (I've "upgraded") and I come up in this "Gnome" thingey if I log in as a new user.  Either way, I'm not in KDE.  So, I'm looking for further help myself.  :)

---

### Post by Silenus on 2007-06-24
```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

Then ctrl alt backspace and change session to kde, and login, to remove kde

```
 sudo aptitude remove kubuntu-desktop
```
Hope it helps.

---

### Post by cuervo_jones_85 on 2007-06-24
i saw on synaptic and will install it trough there

how much space will it use on my hd? any ideas?

also can i remove gnome if i choose to stick with kde? or should i just use kubuntu?

---

### Post by Silenus on 2007-06-24
Not much, if you just install the base system, you can install the apps later, it's not like installing ubuntu over again, just  a new window manager.

---

### Post by cuervo_jones_85 on 2007-06-24
will i be able to remove gnome?

thanks for the input Silenus

---

### Post by Silenus on 2007-06-24
Yes you can remove gnome if you want to this will remove all gnome and install kubuntu
```
sudo apt-get remove alacarte app-install-data-commercial apport-gtk at-spi binfmt-support bittorrent brltty-x11 bug-buddy capplets-data cdrecord cli-common compiz compiz-core compiz-gnome compiz-gtk compiz-plugins contact-lookup-applet dbus-1-utils dcraw deskbar-applet desktop-effects diveintopython doc-base docbook-xml ekiga eog esound espeak espeak-data evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot feisty-gdm-themes feisty-session-splashes feisty-wallpapers file-roller firefox firefox-gnome-support gaim gaim-data gamin gcalctool gcc-3.3-base gconf-editor gconf2 gdebi gdebi-core gdm gedit gedit-common gimp gimp-data gimp-print gimp-python gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-cards-data gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-keyring-manager gnome-mag gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-mount gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines gtk2-engines-pixbuf gtk2-engines-ubuntulooks gtkhtml3.14 gucharmap guile-1.6-libs hal-device-manager human-cursors-theme human-icon-theme human-theme hwdb-client-gnome language-selector libaa1 libatspi1.0-0 libavahi-glib1 libavc1394-0 libbeagle0 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrlapi1 libcaca0 libcairo-perl libcamel1.2-10 libcdio6 libcroco3 libcucul0 libdecoration0 libdjvulibre15 libdv4 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libenchant1c2a libespeak1 libexchange-storage1.2-3 libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2.0-cil libgda2-3 libgda2-common libgdiplus libgdl-1-0 libgdl-1-common libgimp2.0 libgksu1.2-1 libgksu2-0 libgksuui1.0-1 libglade2.0-cil libglew1 libglib-perl libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomecupsui1.0-1c2a libgnomekbd-common libgnomekbd1 libgnomekbdui1 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common libgtk2-perl libgtk2.0-cil libgtkhtml2-0 libgtkhtml3.14-19 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-7 libgtop2-common libgucharmap6 libguile-ltdl-1 libgutenprintui2-1 libhsqldb-java libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libiec61883-0 libkpathsea4 liblaunchpad-integration0 liblircclient0 liblpint-bonobo0 libmdbtools libmetacity0 libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil libnautilus-burn4 libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnm-glib0 libnotify1 libnspr4 libnss3 liboil0.3 liboobs-1-3 libopal-2.2.0 libpanel-applet2-0 libpisock9 libpisync0 libpoppler1-glib libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 librsvg2-2 librsvg2-common libscrollkeeper0 libservlet2.3-java libsexy2 libshout3 libslab0 libsoup2.2-8 libstdc++5 libtotem-plparser1 liburi-perl libvte-common libvte9 libwmf0.2-7 libwnck-common libwnck18 libwww-perl libxevie1 libxklavier11 libxml-parser-perl libxml-twig-perl libxml2-utils libxres1 metacity metacity-common mkisofs mono-common mono-gac mono-jit mono-runtime nautilus nautilus-cd-burner nautilus-data nautilus-sendto network-manager-gnome notification-daemon onboard openoffice.org openoffice.org-base openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk pkg-config python-at-spi python-bittorrent python-cairo python-gconf python-gdbm python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras python-gnomecanvas python-gobject python-gst0.10 python-gtk2 python-gtkhtml2 python-launchpad-integration python-libxml2 python-notify python-numeric python-orca-brlapi python-pyorbit python-virtkey python-vte python-xml rdesktop restricted-manager rhythmbox rss-glx scim scim-gtk2-immodule scim-modules-socket scim-modules-table scim-tables-additional screensaver-default-images scrollkeeper serpentine sgml-data shared-mime-info software-properties-gtk sound-juicer ssh-askpass-gnome synaptic system-tools-backends tangerine-icon-theme tango-icon-theme tango-icon-theme-common tomboy totem totem-gstreamer totem-mozilla tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds update-manager update-notifier usplash-theme-ubuntu vino vnc-common whois xsane xsane-common xscreensaver-data xscreensaver-gl xsltproc xvncviewer yelp zenity && sudo apt-get install kubuntu-desktop
```

Just copy and paste that all into terminal.

---

### Post by bkorb on 2007-06-24
Yep.  Thank you, Silenus.  I finally found the ``change options'' thing to click on at the bottom of the splash screen also.  That got me in to KDE and I'm a happy camper now.

By the way, Silenus, who might be interested to know about an installation issue?  I have a 1200X1024 screen but the install was 800 X 600 and the "forward" button would not fit on the screen.  Since the window was unresizeable, getting to that "forward" button was an extreme  pain.  (remove bottom tool bar, auto hide top tool bar, still not enough so slide top tool bar to  right and finally had top half of button to click.)

Thank you again - Bruce

---

### Post by Silenus on 2007-06-24
I would put that in installation and upgrade section, or in general help.

---

### Post by Magnentius on 2007-06-24
The unofficial ubuntu guide describes this in detail [_here_]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_KDE_.28Kubuntu.29")

---

### Post by coxc24 on 2007-06-25
You could just install from scratch. If you want to then just download the Kubuntu CD or alternate CD and install a system from there.

Personally I use KDE all the time and have recently been playing round with installing base systems on both Debian and Kubuntu. If you install a command line system and then install the following packages; you will be provided with the standard KDE that does not include all of the bloat associated with Kubuntu. You will need to install your required apps but that is not difficult.


```

sudo apt-get install xserver-xorg-core xserver-xorg xorg kdebase kdm

```

Just my thoughts ;)

---

### Post by mac71 on 2007-06-25
> **bkorb said:**
> Yep.  Thank you, Silenus.  I finally found the ``change options'' thing to click on at the bottom of the splash screen also.  That got me in to KDE and I'm a happy camper now.

By the way, Silenus, who might be interested to know about an installation issue?  I have a 1200X1024 screen but the install was 800 X 600 and the "forward" button would not fit on the screen.  Since the window was unresizeable, getting to that "forward" button was an extreme  pain.  (remove bottom tool bar, auto hide top tool bar, still not enough so slide top tool bar to  right and finally had top half of button to click.)

Thank you again - Bruce

Hi just some info on that 800x600 annoyance. If you hold the Alt key and click anywhere on a window, you can drag it right off the screen. Its a great help in getting to those buttons you know are there but can't see. Its a good work around for 800x600 issues.

---


---
title: "IceWM and Rhythmbox - unable to activate plugin?"
date: 2007-04-29
forum: Desktop Environments
---

### Post by aysiu on 2007-04-29
So I used to have Ubuntu (full with Gnome) installed with IceWM. The Rhythmbox plugin for Jamendo was working fine then.

Now I'm using just IceWM and some select other packages.

I do like Rhythmbox, so I have that installed. Only problem is that when I start Rhythmbox, I get a message saying > **Plugin Error**
Unable to activate plugin Jamendo And if I try to activate the plugin, I get that message again. I'd like to activate that plugin if possible.

So what am I missing? I don't want to install *everything* from *ubuntu-desktop* just to get a plugin working. Anyone know which of  the following packages would give me Jamendo-plugin functionality in Rhythmbox? ```
alacarte app-install-data app-install-data-commercial aspell at-spi avahi-autoipd avahi-daemon
  binfmt-support bluez-cups bluez-pin bluez-utils brltty brltty-x11 bug-buddy capplets-data cdrdao cdrecord
  cli-common compiz compiz-core compiz-gnome compiz-gtk compiz-plugins contact-lookup-applet dcraw
  deskbar-applet desktop-effects diveintopython dvd+rw-tools ekiga eog espeak espeak-data evolution
  evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins
  evolution-webcal f-spot feisty-gdm-themes feisty-session-splashes feisty-wallpapers firefox-gnome-support
  foomatic-db-hpijs gaim gaim-data gconf-editor gedit gedit-common gnome-about gnome-accessibility-themes
  gnome-app-install gnome-applets gnome-applets-data gnome-cards-data gnome-control-center gnome-desktop-data
  gnome-doc-utils gnome-games gnome-games-data gnome-mag gnome-menus gnome-netstatus-applet gnome-nettool
  gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-screensaver gnome-session
  gnome-spell gnome-system-monitor gnome-terminal gnome-terminal-data gnome-user-guide gnome-volume-manager
  gthumb gtkhtml3.14 gucharmap hpijs hplip hplip-data libavahi-core5 libbluetooth2 libcamel1.2-10
  libdecoration0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8
  libespeak1 libexchange-storage1.2-3 libgadu3 libgail-gnome-module libgconf2.0-cil libgdiplus libgdl-1-0
  libgdl-1-common libglade2.0-cil libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-speech3
  libgnome-window-settings1 libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomekbd-common libgnomekbd1
  libgnomekbdui1 libgnomevfs2-bin libgnomevfs2-extra libgtk2.0-cil libgtkhtml3.14-19 libgucharmap6
  liblpint-bonobo0 libmetacity0 libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil
  libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil
  libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0
  libmono2.0-cil libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnss-mdns libpisock9 libpisync0 libslab0
  libusplash0 metacity metacity-common mono-common mono-gac mono-jit mono-runtime nautilus nautilus-cd-burner
  nautilus-data nautilus-sendto openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev
  openoffice.org-gnome openoffice.org-gtk openoffice.org-hyphenation openoffice.org-impress
  openoffice.org-java-common openoffice.org-math openoffice.org-style-human openoffice.org-writer ppp
  python-at-spi python-gmenu python-gnome2-desktop python-gnome2-extras python-orca-brlapi
  python-software-properties python-uno rdesktop samba-common screensaver-default-images serpentine smbclient
  software-properties-gtk sound-juicer ssh-askpass-gnome tangerine-icon-theme tomboy totem totem-gstreamer
  totem-mozilla tsclient ttf-arabeyes ttf-bengali-fonts ttf-devanagari-fonts ttf-gujarati-fonts
  ttf-indic-fonts ttf-kannada-fonts ttf-lao ttf-malayalam-fonts ttf-oriya-fonts ttf-punjabi-fonts
  ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds
  update-manager update-manager-core update-notifier usplash usplash-theme-ubuntu vino vnc-common whois
  wvdial xsane xsane-common xsltproc xvncviewer yelp zenity
```

---

### Post by aysiu on 2007-04-30
Bump.

---

### Post by aysiu on 2007-05-01
All right. I give up.

I'm just going to install *ubuntu-desktop*. I can't figure out what package I'm missing...

---

### Post by aysiu on 2007-05-02
Well, I managed to uninstall a bunch more crap, and it's still working: ```
  alacarte app-install-data app-install-data-commercial apport apport-gtk aspell bluez-cups bluez-pin bluez-utils bug-buddy cdrdao cdrecord compiz compiz-core
  compiz-gnome compiz-gtk compiz-plugins deskbar-applet desktop-effects diveintopython dvd+rw-tools ekiga eog evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot feisty-gdm-themes feisty-session-splashes feisty-wallpapers
  firefox-gnome-support gaim gaim-data gconf-editor gdebi gdebi-core gedit gnome-app-install gnome-applets gnome-cards-data gnome-control-center gnome-doc-utils
  gnome-games gnome-games-data gnome-panel gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-terminal gnome-terminal-data gnome-user-guide gthumb
  gtkhtml3.14 guile-1.6-libs libdecoration0 libedata-book1.2-2 libedata-cal1.2-6 libegroupwise1.2-13 libexchange-storage1.2-3 libgadu3 libgdl-1-0 libgdl-1-common
  libgksu1.2-1 libgksuui1.0-1 libguile-ltdl-1 libmetacity0 libmono-sqlite2.0-cil libnm-glib0 libopal-2.2.0 libpt-plugins-alsa libqthreads-12 libusplash0 metacity
  metacity-common nautilus nautilus-cd-burner nautilus-data nautilus-sendto onboard ppp python-gnome2-desktop python-gnome2-extras python-software-properties rdesktop
  restricted-manager serpentine software-properties-gtk sound-juicer tomboy totem totem-gstreamer totem-mozilla tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs
  update-manager update-manager-core update-notifier usplash usplash-theme-ubuntu vino vnc-common wodim wvdial xsltproc xvncviewer yelp zenity
```

---

### Post by ciro314 on 2007-05-12
just sudo apt-get install libgnomevfs2-extra

so you can install jamendo plugin

---

### Post by Vinze on 2007-07-11
> **ciro314 said:**
> just sudo apt-get install libgnomevfs2-extra

so you can install jamendo plugin

Thanks, this worked for me. And apparently, this only pulls in a few other libgnomevfs packages so you don't end up with half of gnome installed :D

---


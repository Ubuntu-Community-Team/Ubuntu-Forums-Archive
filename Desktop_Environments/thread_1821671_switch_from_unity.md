---
title: "switch from unity"
date: 2011-08-09
forum: Desktop Environments
---

### Post by jfbooth on 2011-08-09
This is a WUBI install of UBUNTU 11.04.  The option to switch to CLASSIC is not included with a WUBI install so I have never seen the CLASSIC desktop.

I really do not like UNITY.  I am also ignorant when it comes to Linux Desktops.  Pretty confused between gnome, kde, xfce, unity except that I can guess these are simply different desktop environments .. except I have read that UNITY is a 'front end' for GNOME .. whatever that means.

What I would like to do is dump UNITY for XFCE if possible .. with this WUBI install.  I have another computer running XUBUNTU 32-bit and I THINK it uses XFCE which I am accustomed to and like.

Am I dreaming or is this feasible?  If it is, I assume I need to:

1.  Install XFCE
2.  Uninstall Unity

and it will automatically boot up to XFCE .. but I doubt it would be that simple.

Also .. seems a more logical thing is install XUBUNTU and I am not exactly sure why I wouldn't ... isn't UBUNTU somehow superior to XUBUNTU?

The XUBUNTU I have installed is on an old 32-bit Windows ME machine.  I have a 'better' machine w/ a 64-bit dual core and figured it was well suited for UBUNTU rather than XUBUNTU for some PRESUMBED reason.

I guess my objective is to run UBUNTU 64 bit with a WUBI install and not use/have UNITY.

Thank you in advance.

EDIT:  I thought I found it here:

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Seemed to explain how to go from UNITY to XFCE .. but it did not work.  Here is the output I got:

```
owner@ubuntu:~$ sudo apt-get remove adium-theme-ubuntu alacarte appmenu-gtk at-spi bamfdaemon banshee banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore baobab binfmt-support bluez-gstreamer bogofilter bogofilter-bdb bogofilter-common branding-ubuntu brasero brasero-cdrkit brasero-common capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-main compizconfig-backend-gconf computer-janitor computer-janitor-gtk dvd+rw-tools empathy empathy-common eog evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content exiv2 gbrainy gconf-defaults-service gconf-editor gdm-guest-session gedit gedit-common geoclue geoclue-ubuntu-geoip ginn gir1.2-gconf-2.0 gir1.2-panelapplet-3.0 gir1.2-soup-2.4 gnome-about gnome-applets gnome-applets-data gnome-bluetooth gnome-control-center gnome-disk-utility gnome-mag gnome-media gnome-media-common gnome-mime-data gnome-nettool gnome-orca gnome-panel gnome-panel-bonobo gnome-panel-data gnome-power-manager gnome-screensaver gnome-screenshot gnome-search-tool gnome-session gnome-session-canberra gnome-session-common gnome-system-log gnome-system-monitor gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-user-share gnome-utils-common growisofs gsettings-desktop-schemas gstreamer0.10-gnonlin gwibber gwibber-service gwibber-service-facebook gwibber-service-identica gwibber-service-twitter indicator-applet indicator-applet-appmenu indicator-applet-complete indicator-applet-session indicator-appmenu indicator-datetime indicator-me indicator-session libappindicator0.1-cil libart-2.0-2 libart2.0-cil libbamf0 libbonoboui2-0 libbonoboui2-common libboost-serialization1.42.0 libbrasero-media1 libcamel1.2-19 libcanberra-pulse libcompizconfig0 libcryptui0 libdconf0 libdecoration0 libdee-1.0-1 libebackend1.2-0 libebook1.2-10 libecal1.2-8 libedata-book1.2-8 libedata-cal1.2-10 libedataserver1.2-14 libedataserverui1.2-11 libegroupwise1.2-13 libevolution libexempi3 libexiv2-10 libfolks-telepathy22 libfolks22 libgail-common libgail-gnome-module libgconf2.0-cil libgdata-common libgdata1.7-cil libgdata11 libgdu-gtk0 libgeoclue0 libgexiv2-0 libgkeyfile1.0-cil libglade2.0-cil libgladeui-1-11 libglew1.5 libglewmx1.5 libglib2.0-bin libglib2.0-cil libglib2.0-data libgmime-2.4-2 libgmime2.4-cil libgnome-mag2 libgnome-media0 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2.24-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgoocanvas-common libgoocanvas3 libgpgme11 libgpod-common libgpod4 libgraphite3 libgsl0ldbl libgtk-sharp-beans-cil libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libgtksourceview2.0-0 libgtksourceview2.0-common libgudev1.0-cil libgweather-common libgweather1 libgwibber1 libhyphen0 liblaunchpad-integration1.0-cil liblircclient0 liblouis-data liblouis2 libmetacity-private0 libmission-control-plugins0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-i18n-west2.0-cil libmono-management2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-system2.0-cil libmono-zeroconf1.0-cil libmtp8 libmythes-1.2-0 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27-gnutls libnotify0.4-cil libnux-0.9-0 libnux-0.9-common liboverlay-scrollbar-0.1-0 libpanel-applet-3-0 libpanel-applet2-0 libprotobuf6 libprotoc6 libpst4 libpth20 libquvi0 libraptor1 librasqal2 librdf0 libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress libreoffice-math libreoffice-style-human libreoffice-writer libsdl1.2debian libsdl1.2debian-pulseaudio libstlport4.6ldbl libsyncdaemon-1.0-1 libtaglib2.0-cil libtelepathy-farsight0 libtelepathy-logger2 libtextcat-data libtextcat0 libtotem-plparser17 libubuntuone-1.0-1 libubuntuone1.0-cil libunity-misc0 libunity4 libutouch-geis1 libwmf0.2-7-gtk libzeitgeist-1.0-1 light-themes media-player-info metacity metacity-common mono-2.0-gac mono-csharp-shell mono-gac mono-gmcs mono-runtime mousetweaks nautilus nautilus-data nautilus-sendto nautilus-sendto-empathy nautilus-share notify-osd notify-osd-icons nux-tools obexd-client overlay-scrollbar pitivi plymouth-theme-ubuntu-logo protobuf-compiler pulseaudio-module-bluetooth pulseaudio-module-gconf python-argparse python-brlapi python-configglue python-egenix-mxdatetime python-egenix-mxtools python-farsight python-gnome2 python-gnomecanvas python-gtksourceview2 python-gtkspell python-indicate python-libproxy python-louis python-mako python-markupsafe python-papyon python-protobuf python-pyatspi python-pygoocanvas python-pyinotify python-pyorbit python-rdflib python-speechd python-telepathy python-twisted-names python-ubuntuone-client python-ubuntuone-control-panel python-ubuntuone-storageprotocol python-uno python-wnck rdesktop seahorse shotwell ssh-askpass-gnome telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-logger telepathy-mission-control-5 telepathy-salut tomboy totem totem-common totem-mozilla totem-plugins tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-sounds ubuntu-system-service ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome ubuntuone-control-panel ubuntuone-control-panel-gtk unity unity-asset-pool unity-common unity-place-applications unity-place-files uno-libs3 ure vino whois wodim xfonts-mathml zeitgeist zeitgeist-datahub zeitgeist-extension-fts && sudo apt-get install xubuntu-desktop 
[sudo] password for owner: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libstlport4.6ldbl
E: Couldn't find any package by regex 'libstlport4.6ldbl'
owner@ubuntu:~$ 
```

---

### Post by Frogs Hair on 2011-08-09
The option to use Classic Gnome is included in a Wubi installation . If Classic Gnome does not appear on the session list you have another problem with your installation . See the link for instructions . 

[http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/](http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/)

---

### Post by jfbooth on 2011-08-09
> **Frogs Hair said:**
> The option to use Classic Gnome is included in a Wubi installation . If Classic Gnome does not appear on the session list you have another problem with your installation . See the link for instructions . 

[http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/](http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/)

I don't know how I missed that.  I guess I got distracted by something I read at another website .. that Classic was 'not included' on a Wubi install.

Thank you for your prompt and well informed answer.

---

### Post by Frogs Hair on 2011-08-09
You're welcome , the classic option will be removed in 11.10 because that release will use Gnome 3 .

---

### Post by infamous-online on 2011-08-09
> **Frogs Hair said:**
> You're welcome , the classic option will be removed in 11.10 because that release will use Gnome 3 .

Hopefully they'll give you more customization to the interface as I quickly was turned off by Unity and instantly went back to Ubuntu 10.10 because 11.04 seemed very sluggish and buggy :(.

---

### Post by IWantFroyo on 2011-08-09
> **infamous-online said:**
> Hopefully they'll give you more customization to the interface as I quickly was turned off by Unity and instantly went back to Ubuntu 10.10 because 11.04 seemed very sluggish and buggy :(.

Same here, except I went to Debian and Ubuntu Lucid.
Openbox is worlds faster than Unity.

---


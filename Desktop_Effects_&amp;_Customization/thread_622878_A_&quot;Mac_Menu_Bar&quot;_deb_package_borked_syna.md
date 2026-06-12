---
title: "A &quot;Mac Menu Bar&quot; deb package borked synaptic... HALP!"
date: 2007-11-25
forum: Desktop Effects &amp; Customization
---

### Post by Izobalax on 2007-11-25
OK...

I wanted to find out how to add the "Mac Menu Bar" applet. So I went [HERE](https://wiki.ubuntu.com/global_menu) and downloaded the .tar file containing all the necessary .deb packages needed to make this a reality. 

I installed one .deb package (libgtk2.0-common_2.12.0-1ubuntu3.1_all.deb), and though it installed, it told me it couldn't meet one of the dependencies and typing:

```
sudo apt-get install -f
```

...would fix the broken dependencies. 

Problem is, when I do that in the terminal, it says I need to remove *lots* of software, like OpenOffice, GNOME and stuff like that. 

How do I resolve this!?

/izo\

---

### Post by Ub1476 on 2007-11-25
If I'm correct it will not remove it, but sort of hack it to make it working with the mac menu bar hack. I'm not sure though..

---

### Post by Izobalax on 2007-11-25
> **Ub1476 said:**
> If I'm correct it will not remove it, but sort of hack it to make it working with the mac menu bar hack. I'm not sure though..
Hmm... ideally I'd like to revert the libgtk2.0-common_2.12.0-1ubuntu3.1_all file back to it's normal state. Problem is, synaptic won't let me do that. 

/izo\

---

### Post by Izobalax on 2007-11-25
Also, because of this, it means I can no longer install ANYTHING until this is fixed. 

HALP!

/izo\

---

### Post by Izobalax on 2007-11-25
Can anyone help me? Please? I can't INSTALL anything!

/izo\

---

### Post by Ub1476 on 2007-11-25
Check around in Synaptic and see if you can reinstall libgtk and such (those who are hacked).

Maybe also this will help: 

```
sudo apt-get install -f
```

---

### Post by Izobalax on 2007-11-25
> **Ub1476 said:**
> Check around in Synaptic and see if you can reinstall libgtk and such (those who are hacked).
> **Ub1476 said:**
> Maybe also this will help: 

```
sudo apt-get install -f
```

When I go into the Synaptic Package Manager, it tells me that there is ONE broken package: libgtk-2.0. If I want to reinstall it, or if I type "sudo apt-get install -f" into the terminal, it always tells me that all this software will be REMOVED:

```
adobereader-enu adobereader-plugin alacarte apport-gtk apturl at-spi
  automatix2 banshee bluez-gnome brltty-x11 bug-buddy checkgmail compiz
  compiz-gnome compiz-plugins compizconfig-settings-manager
  contact-lookup-applet deluge-torrent deskbar-applet displayconfig-gtk ekiga
  emerald eog evince evolution evolution-exchange evolution-plugins
  evolution-webcal f-spot fast-user-switch-applet file-roller firefox
  firefox-gnome-support firefox-themes-ubuntu flashplugin-nonfree fusion-icon
  gcalctool gconf-editor gdebi gdm gedit gimmie gimp gimp-print gimp-python
  gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets
  gnome-bluetooth gnome-btdownload gnome-control-center gnome-games
  gnome-icon-theme gnome-keyring gnome-keyring-manager gnome-mag
  gnome-main-menu gnome-media gnome-menus gnome-mount gnome-netstatus-applet
  gnome-nettool gnome-orca gnome-panel gnome-pilot gnome-pilot-conduits
  gnome-power-manager gnome-screensaver gnome-session gnome-spell
  gnome-system-monitor gnome-system-tools gnome-terminal gnome-themes
  gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-plugins-good
  gthumb gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf
  gtk2-engines-qtcurve gtk2-engines-qtpixmap gtk2-engines-ubuntulooks
  gtkhtml3.14 gucharmap hal-cups-utils hal-device-manager human-theme
  hwdb-client-gnome inkscape language-selector language-support-en
  libatspi1.0-0 libbonoboui2-0 libdeskbar-tracker libedataserverui1.2-8
  libeel2-2 libemeraldengine-dev libemeraldengine0 libexchange-storage1.2-3
  libgail-common libgail-gnome-module libgail18 libgconf2.0-cil libgdl-1-0
  libgdl-gnome-1-0 libgimp2.0 libgksu2-0 libgksuui1.0-1 libglade2-0
  libglade2.0-cil libgnome-desktop-2 libgnome-keyring0
  libgnome-window-settings1 libgnome2-canvas-perl libgnome2-perl
  libgnome2.0-cil libgnomebt0 libgnomecanvas2-0 libgnomekbd1 libgnomekbdui1
  libgnomeprintui2.2-0 libgnomeui-0 libgpod2 libgtk2-perl
  libgtk2-trayicon-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtkhtml2-0
  libgtkhtml2.0-cil libgtkhtml3.14-19 libgtkhtml3.8-15 libgtkmm-2.4-1c2a
  libgtksourceview1.0-0 libgtksourceview2.0-0 libgtkspell0 libgucharmap6
  libgutenprintui2-1 liblaunchpad-integration0 liblpint-bonobo0 libmetacity0
  libnautilus-burn4 libnautilus-extension1 libnotify1 libpanel-applet2-0
  libpoppler-glib2 librsvg2-2 librsvg2-common librsvg2.0-cil libsexy2 libslab0
  libtotem-plparser7 libtracker-gtk0 libvte9 libwmf0.2-7 libwnck22
  libwxgtk2.6-0 metacity mozilla-firefox-adblock mozilla-firefox-locale-en-gb
  nautilus nautilus-cd-burner nautilus-sendto network-manager-gnome nicotine
  notification-daemon nvidia-glx-new onboard openoffice.org
  openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us
  openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human
  openoffice.org-thesaurus-en-us openoffice.org-writer pidgin python-at-spi
  python-glade2 python-gnome2 python-gnome2-desktop python-gnome2-extras
  python-gnomecanvas python-gtk2 python-gtkhtml2 python-launchpad-integration
  python-notify python-pygtksourceview python-sexy python-uno python-virtkey
  python-vte restricted-manager rhythmbox scim scim-gtk2-immodule
  scim-modules-table scim-tables-additional screensaver-default-images
  serpentine software-properties-gtk sound-juicer ssh-askpass-gnome
  sun-java6-plugin synaptic system-config-printer tangerine-icon-theme
  tango-icon-theme-common thunderbird-locale-en-gb tomboy totem
  totem-gstreamer totem-mozilla tracker tracker-search-tool tsclient ubufox
  ubuntu-artwork ubuntu-desktop ubuntu-docs update-manager update-notifier
  vino vlc xdg-user-dirs-gtk xsane xscreensaver-data xscreensaver-gl yelp
  zenity
```



I am NOT doing that. 

/izo\

---

### Post by Izobalax on 2007-11-26
HALP!

/izo\

---

### Post by BoardDWorld on 2007-11-26
Haha, I know what that's like. Have you tried reinstalling the package and taking note of the dependency. If so what is it?

---


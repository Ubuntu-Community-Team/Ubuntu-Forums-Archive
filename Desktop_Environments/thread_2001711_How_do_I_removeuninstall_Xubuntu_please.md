---
title: "How do I remove/uninstall Xubuntu please"
date: 2012-06-11
forum: Desktop Environments
---

### Post by welshmike on 2012-06-11
I was unsure about how much I liked 12.04 Ubuntu Unity so I ran sudo apt-get install xubuntu-desktop in the terminal to install Xubuntu desktop and try it out.
I really didn't like the limitations of the Xubuntu desktop so I would now like to remove Xubuntu and the software included in its install so that the login choice reverts to just Ubuntu Unity.
I tried sudo apt-get remove xubuntu-desktop but that did not uninstall Xubuntu.

---

### Post by sudodus on 2012-06-11
I would have suggested exactly what you tried. Maybe you need to do it without running the XFCE desktop environment, for example booting into the recovery environment or running a full screen terminal when logged into Unity.

---

### Post by malspa on 2012-06-11
sudo apt-get purge xubuntu-desktop?

---

### Post by cortman on 2012-06-11
Try [this]("http://askubuntu.com/questions/92084/how-to-remove-xubuntu-desktop").

---

### Post by IWantFroyo on 2012-06-11
From [http://psychocats.net/ubuntu/pureubuntu](http://psychocats.net/ubuntu/pureubuntu)

```
sudo apt-get remove abiword abiword-common abiword-plugin-grammar  abiword-plugin-mathview alacarte bison blueman brltty-x11 catfish  docbook-xml exo-utils flex fonts-droid gigolo gimp gimp-data  gmusicbrowser gnome-desktop-data gnome-system-tools gnome-time-admin  gnumeric gnumeric-common gnumeric-doc gstreamer0.10-gnomevfs gthumb  gthumb-data gtk2-engines-pixbuf indicator-application-gtk2  indicator-messages-gtk2 indicator-sound-gtk2  indicator-status-provider-pidgin leafpad libabiword-2.9 libao-common  libao4 libaudio-scrobbler-perl libbabl-0.0-0 libbison-dev libcolamd2.7.1  libconfig-inifiles-perl libdigest-crc-perl libencode-locale-perl  libept1.4.12 libexo-1-0 libexo-common libexo-helpers  libfile-listing-perl libfl-dev libfont-afm-perl libgarcon-1-0  libgarcon-common libgdome2-0 libgdome2-cpp-smart0c2a libgegl-0.0-0  libgimp2.0 libglade2-0 libgnomevfs2-0 libgnomevfs2-common  libgnomevfs2-extra libgoffice-0.8-8 libgoffice-0.8-8-common libgsf-1-114  libgsf-1-common libgstreamer-perl libgtk2-notify-perl  libgtk2-trayicon-perl libgtkmathview0c2a libgtkspell0 libhtml-form-perl  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl  libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl  libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libid3tag0  libido-0.1-0 libilmbase6 libio-socket-inet6-perl libio-socket-ssl-perl  libjavascriptcoregtk-1.0-0 libjpeg-progs libjpeg-turbo-progs  libkeybinder0 liblaunchpad-integration1 liblink-grammar4 libloudmouth1-0  liblwp-mediatypes-perl liblwp-protocol-https-perl libmad0  libmailtools-perl libnet-dbus-perl libnet-http-perl libnet-ssleay-perl  liboobs-1-5 libopenexr6 libotr2 libots0 librarian0 libsexy2  libsocket6-perl libtagc0 libthunarx-2-0 libtidy-0.99-0  libtie-ixhash-perl libtimedate-perl libtumbler-1-0 libunique-1.0-0  liburi-perl libvte-common libvte9 libwebkitgtk-1.0-0  libwebkitgtk-1.0-common libwv-1.2-4 libwww-perl libwww-robotrules-perl  libxfce4ui-1-0 libxfce4util-bin libxfce4util-common libxfce4util4  libxfcegui4-4 libxfconf-0-2 libxml-parser-perl libxml-twig-perl  libxml-xpath-perl libxss1 lightdm-gtk-greeter  link-grammar-dictionaries-en linux-headers-3.2.0-24  linux-headers-3.2.0-24-generic linux-headers-generic lp-solve m4 mpg321  orage parole pastebinit pavucontrol pidgin pidgin-data pidgin-libnotify  pidgin-microblog pidgin-otr plymouth-theme-xubuntu-logo  plymouth-theme-xubuntu-text python-configobj python-glade2 python-gmenu  rarian-compat ristretto screensaver-default-images sgml-data  shimmer-themes synaptic system-tools-backends tcl8.5 thunar  thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-volman  ttf-droid ttf-lyx tumbler tumbler-common xchat xchat-common xfburn  xfce-keyboard-shortcuts xfce4-appfinder xfce4-cpugraph-plugin  xfce4-datetime-plugin xfce4-dict xfce4-indicator-plugin  xfce4-mailwatch-plugin xfce4-netload-plugin xfce4-notes  xfce4-notes-plugin xfce4-notifyd xfce4-panel xfce4-places-plugin  xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin  xfce4-screenshooter xfce4-session xfce4-settings xfce4-systemload-plugin  xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin  xfce4-volumed xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4  xfdesktop4-data xfwm4 xscreensaver xscreensaver-data xscreensaver-gl  xubuntu-artwork xubuntu-default-settings xubuntu-desktop xubuntu-docs  xubuntu-icon-theme xubuntu-wallpapers && sudo apt-get install  ubuntu-desktop && sudo /usr/lib/lightdm/lightdm-set-defaults -g  unity-greeter
```

---

### Post by wilee-nilee on 2012-06-11
> **IWantFroyo said:**
> From [http://psychocats.net/ubuntu/pureubuntu](http://psychocats.net/ubuntu/pureubuntu)

```
sudo apt-get remove abiword abiword-common abiword-plugin-grammar  abiword-plugin-mathview alacarte bison blueman brltty-x11 catfish  docbook-xml exo-utils flex fonts-droid gigolo gimp gimp-data  gmusicbrowser gnome-desktop-data gnome-system-tools gnome-time-admin  gnumeric gnumeric-common gnumeric-doc gstreamer0.10-gnomevfs gthumb  gthumb-data gtk2-engines-pixbuf indicator-application-gtk2  indicator-messages-gtk2 indicator-sound-gtk2  indicator-status-provider-pidgin leafpad libabiword-2.9 libao-common  libao4 libaudio-scrobbler-perl libbabl-0.0-0 libbison-dev libcolamd2.7.1  libconfig-inifiles-perl libdigest-crc-perl libencode-locale-perl  libept1.4.12 libexo-1-0 libexo-common libexo-helpers  libfile-listing-perl libfl-dev libfont-afm-perl libgarcon-1-0  libgarcon-common libgdome2-0 libgdome2-cpp-smart0c2a libgegl-0.0-0  libgimp2.0 libglade2-0 libgnomevfs2-0 libgnomevfs2-common  libgnomevfs2-extra libgoffice-0.8-8 libgoffice-0.8-8-common libgsf-1-114  libgsf-1-common libgstreamer-perl libgtk2-notify-perl  libgtk2-trayicon-perl libgtkmathview0c2a libgtkspell0 libhtml-form-perl  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl  libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl  libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libid3tag0  libido-0.1-0 libilmbase6 libio-socket-inet6-perl libio-socket-ssl-perl  libjavascriptcoregtk-1.0-0 libjpeg-progs libjpeg-turbo-progs  libkeybinder0 liblaunchpad-integration1 liblink-grammar4 libloudmouth1-0  liblwp-mediatypes-perl liblwp-protocol-https-perl libmad0  libmailtools-perl libnet-dbus-perl libnet-http-perl libnet-ssleay-perl  liboobs-1-5 libopenexr6 libotr2 libots0 librarian0 libsexy2  libsocket6-perl libtagc0 libthunarx-2-0 libtidy-0.99-0  libtie-ixhash-perl libtimedate-perl libtumbler-1-0 libunique-1.0-0  liburi-perl libvte-common libvte9 libwebkitgtk-1.0-0  libwebkitgtk-1.0-common libwv-1.2-4 libwww-perl libwww-robotrules-perl  libxfce4ui-1-0 libxfce4util-bin libxfce4util-common libxfce4util4  libxfcegui4-4 libxfconf-0-2 libxml-parser-perl libxml-twig-perl  libxml-xpath-perl libxss1 lightdm-gtk-greeter  link-grammar-dictionaries-en linux-headers-3.2.0-24  linux-headers-3.2.0-24-generic linux-headers-generic lp-solve m4 mpg321  orage parole pastebinit pavucontrol pidgin pidgin-data pidgin-libnotify  pidgin-microblog pidgin-otr plymouth-theme-xubuntu-logo  plymouth-theme-xubuntu-text python-configobj python-glade2 python-gmenu  rarian-compat ristretto screensaver-default-images sgml-data  shimmer-themes synaptic system-tools-backends tcl8.5 thunar  thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-volman  ttf-droid ttf-lyx tumbler tumbler-common xchat xchat-common xfburn  xfce-keyboard-shortcuts xfce4-appfinder xfce4-cpugraph-plugin  xfce4-datetime-plugin xfce4-dict xfce4-indicator-plugin  xfce4-mailwatch-plugin xfce4-netload-plugin xfce4-notes  xfce4-notes-plugin xfce4-notifyd xfce4-panel xfce4-places-plugin  xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin  xfce4-screenshooter xfce4-session xfce4-settings xfce4-systemload-plugin  xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin  xfce4-volumed xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4  xfdesktop4-data xfwm4 xscreensaver xscreensaver-data xscreensaver-gl  xubuntu-artwork xubuntu-default-settings xubuntu-desktop xubuntu-docs  xubuntu-icon-theme xubuntu-wallpapers && sudo apt-get install  ubuntu-desktop && sudo /usr/lib/lightdm/lightdm-set-defaults -g  unity-greeter
```


+1 This is the correct answer. 

Just removing the desktop is bad advice, the OP asked for all of Xubuntu to be removed at the least.  

The desktop is a meta package and should be removed correctly.

---

### Post by pete04 on 2012-06-11
I successfully did this a while back and used synaptic package manager. I think a search for xubuntu or xfce turned up all the packages I needed to remove completely.

---

### Post by welshmike on 2012-06-14
> **IWantFroyo said:**
> From [http://psychocats.net/ubuntu/pureubuntu](http://psychocats.net/ubuntu/pureubuntu)

```
sudo apt-get remove abiword abiword-common abiword-plugin-grammar  abiword-plugin-mathview alacarte bison blueman brltty-x11 catfish  docbook-xml exo-utils flex fonts-droid gigolo gimp gimp-data  gmusicbrowser gnome-desktop-data gnome-system-tools gnome-time-admin  gnumeric gnumeric-common gnumeric-doc gstreamer0.10-gnomevfs gthumb  gthumb-data gtk2-engines-pixbuf indicator-application-gtk2  indicator-messages-gtk2 indicator-sound-gtk2  indicator-status-provider-pidgin leafpad libabiword-2.9 libao-common  libao4 libaudio-scrobbler-perl libbabl-0.0-0 libbison-dev libcolamd2.7.1  libconfig-inifiles-perl libdigest-crc-perl libencode-locale-perl  libept1.4.12 libexo-1-0 libexo-common libexo-helpers  libfile-listing-perl libfl-dev libfont-afm-perl libgarcon-1-0  libgarcon-common libgdome2-0 libgdome2-cpp-smart0c2a libgegl-0.0-0  libgimp2.0 libglade2-0 libgnomevfs2-0 libgnomevfs2-common  libgnomevfs2-extra libgoffice-0.8-8 libgoffice-0.8-8-common libgsf-1-114  libgsf-1-common libgstreamer-perl libgtk2-notify-perl  libgtk2-trayicon-perl libgtkmathview0c2a libgtkspell0 libhtml-form-perl  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl  libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl  libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libid3tag0  libido-0.1-0 libilmbase6 libio-socket-inet6-perl libio-socket-ssl-perl  libjavascriptcoregtk-1.0-0 libjpeg-progs libjpeg-turbo-progs  libkeybinder0 liblaunchpad-integration1 liblink-grammar4 libloudmouth1-0  liblwp-mediatypes-perl liblwp-protocol-https-perl libmad0  libmailtools-perl libnet-dbus-perl libnet-http-perl libnet-ssleay-perl  liboobs-1-5 libopenexr6 libotr2 libots0 librarian0 libsexy2  libsocket6-perl libtagc0 libthunarx-2-0 libtidy-0.99-0  libtie-ixhash-perl libtimedate-perl libtumbler-1-0 libunique-1.0-0  liburi-perl libvte-common libvte9 libwebkitgtk-1.0-0  libwebkitgtk-1.0-common libwv-1.2-4 libwww-perl libwww-robotrules-perl  libxfce4ui-1-0 libxfce4util-bin libxfce4util-common libxfce4util4  libxfcegui4-4 libxfconf-0-2 libxml-parser-perl libxml-twig-perl  libxml-xpath-perl libxss1 lightdm-gtk-greeter  link-grammar-dictionaries-en linux-headers-3.2.0-24  linux-headers-3.2.0-24-generic linux-headers-generic lp-solve m4 mpg321  orage parole pastebinit pavucontrol pidgin pidgin-data pidgin-libnotify  pidgin-microblog pidgin-otr plymouth-theme-xubuntu-logo  plymouth-theme-xubuntu-text python-configobj python-glade2 python-gmenu  rarian-compat ristretto screensaver-default-images sgml-data  shimmer-themes synaptic system-tools-backends tcl8.5 thunar  thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-volman  ttf-droid ttf-lyx tumbler tumbler-common xchat xchat-common xfburn  xfce-keyboard-shortcuts xfce4-appfinder xfce4-cpugraph-plugin  xfce4-datetime-plugin xfce4-dict xfce4-indicator-plugin  xfce4-mailwatch-plugin xfce4-netload-plugin xfce4-notes  xfce4-notes-plugin xfce4-notifyd xfce4-panel xfce4-places-plugin  xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin  xfce4-screenshooter xfce4-session xfce4-settings xfce4-systemload-plugin  xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin  xfce4-volumed xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4  xfdesktop4-data xfwm4 xscreensaver xscreensaver-data xscreensaver-gl  xubuntu-artwork xubuntu-default-settings xubuntu-desktop xubuntu-docs  xubuntu-icon-theme xubuntu-wallpapers && sudo apt-get install  ubuntu-desktop && sudo /usr/lib/lightdm/lightdm-set-defaults -g  unity-greeter
```

Thank you very much.
The command looked formidable but I ran it on my old laptop that is running Unity and had XFCE installed too.
Nothing appears damaged and Unity runs as it did before I installed XFCE.
Now to bite the bullet and remove XFCE from my main newish laptop.

---


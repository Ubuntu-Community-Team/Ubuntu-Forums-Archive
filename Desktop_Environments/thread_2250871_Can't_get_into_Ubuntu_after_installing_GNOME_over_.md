---
title: "Can't get into Ubuntu after installing GNOME over Unity."
date: 2014-10-31
forum: Desktop Environments
---

### Post by Connor_Webb on 2014-10-31
I installed Ubuntu on a Dell studio xps 435 and it worked fine until I tried to install GNOME over it. I wanted to return to unity, so I typed into the alt-f2 window, "unity --replace", a command I found on askubuntu.com. It didn't do anything, and when I turned on the computer the next time, the screen was black. It finally worked after several tries, but was still in Ubuntu. Then, to bypass a BIOS password a so called "friend" put on it after that, I took out the CMOS battery and on next boot there was no BIOS password but when ubuntu booted up it had the GNOME logo with the blinking dots instead of the Ubuntu one. When I tried to log in all I saw was the wallpaper and I waited and waited and the launcher and files on the desktop didn't show up. How would I fix this? I have a bootable Ubuntu USB that I could use to delete the GNOME files and install the Unity ones.

---

### Post by grahammechanical on 2014-10-31
I am a little confused. Ubuntu is built on the Gnome 3 desktop environment (DE). So, what did you install? Gnome 3 shell. That should not have removed the Unity user interface. It should give us an additional session at the login screen where we can select to login to either Ubuntu (Unity) or Gnome shell.

Installing an alternative desktop such as Gnome 3 shell will change the flash screen and the background image to the log in screen. Reversing things is not so easy. So, what is the immediate problem? Loading to a desktop with only the wallpaper or the Gnome logo on the flash screen instead of the Ubuntu logo?

At the login screen can you select the Ubuntu session? Lets make sure we are in Ubuntu (Unity). Then open the terminal with Crtl+Alt+T or a LInux console with Ctrl+Alt+F2 and run

```
dconf reset -f /org/compiz/
```

to reset the Compiz window compositor and to restart Unity run

```
setsid unity
```

Regards.

---

### Post by Connor_Webb on 2014-11-03
I think I might have accidentally installed GNOME shell but I meant to install the desktop environment.
Also, I can't run those commands because my computer is completely non-functioning

---

### Post by Frogs Hair on 2014-11-03
When installing other sessions they are selected from the icon on the top right of the password window in the login screen. The replace command was primarily used to switch between metacity and compiz on older versions of Ubuntu.

---

### Post by Connor_Webb on 2014-11-11
I don't see that icon.

---

### Post by deadflowr on 2014-11-11
Does the login screen look the same as when you only had unity?
(Meaning, does the username and password box show up in the middle of the screen on the left side. And not directly in the middle of the screen)

---

### Post by Connor_Webb on 2014-11-12
Yes, it looks the same.

---

### Post by deadflowr on 2014-11-12
So when you go to login, the little box next to the username shows the gnome logo( a foot) and not the Ubuntu logo?
And clicking on the box does not change or show the Ubuntu logo?
Is that correct?

---

### Post by kansasnoob on 2014-11-12
Not sure which version of Ubuntu you have so I'll assume Trusty (but we should know for sure), anyway installing the meta-package 'gnome' installs a lot of other packages:

```
lance@lance-desktop:~$ sudo apt-get install gnome --assume-no
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  alacarte argyll binfmt-support browser-plugin-gnash caribou caribou-antler
  cli-common dconf-editor dconf-tools desktop-base evolution evolution-common
  evolution-indicator evolution-plugins finger five-or-more fonts-cantarell
  four-in-a-row freerdp-x11 gawk gdebi gdebi-core gdm gedit-plugins gimp
  gimp-data gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0
  gir1.2-evince-3.0 gir1.2-gck-1 gir1.2-gconf-2.0 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0
  gir1.2-gnomedesktop-3.0 gir1.2-gtkclutter-1.0 gir1.2-gtop-2.0
  gir1.2-gucharmap-2.90 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-nmgtk-1.0
  gir1.2-panelapplet-4.0 gir1.2-polkit-1.0 gir1.2-rest-0.7
  gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-tracker-0.16
  gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gir1.2-zeitgeist-2.0 gir1.2-zpj-0.0 gjs
  gksu gnash gnash-common gnome-applets gnome-applets-data gnome-backgrounds
  gnome-chess gnome-color-manager gnome-control-center
  gnome-control-center-data gnome-core gnome-dictionary gnome-documents
  gnome-games gnome-icon-theme-extras gnome-icon-theme-full gnome-klotski
  gnome-media gnome-nettool gnome-nibbles gnome-online-accounts
  gnome-online-miners gnome-packagekit gnome-packagekit-data
  gnome-packagekit-session gnome-panel gnome-panel-data gnome-robots
  gnome-session gnome-session-flashback gnome-settings-daemon gnome-shell
  gnome-shell-common gnome-shell-extensions gnome-sushi gnome-tetravex
  gnome-themes-standard gnome-themes-standard-data gnome-tweak-tool gnuchess
  gnuchess-book grilo-plugins-0.2 gstreamer0.10-gconf gtk2-engines
  gtk2-engines-pixbuf hamster-applet hamster-indicator iagno imagemagick
  imagemagick-common indicator-applet-complete inkscape libamd2.3.1
  libappindicator0.1-cil libappindicator1 libavahi-ui-gtk3-0 libavresample1
  libbabl-0.1-0 libblas3 libbonobo2-0 libbonobo2-common libbonoboui2-0
  libbonoboui2-common libboost-iostreams1.54.0 libboost-program-options1.54.0
  libboost-thread1.54.0 libcairo-perl libcamd2.3.1 libcaribou-common
  libcaribou-gtk-module libcaribou-gtk3-module libcaribou0 libccolamd2.8.0
  libcholmod2.1.2 libcolord-gtk1 libdbus-glib2.0-cil libdbus2.0-cil libdiscid0
  libencode-locale-perl liberror-perl libevolution libfile-listing-perl
  libfont-afm-perl libgconf2.0-cil libgdict-1.0-6 libgdict-common libgdiplus
  libgdm1 libgegl-0.2-0 libgfortran3 libgif4 libgimp2.0 libgjs0e libgksu2-0
  libglade2-0 libglib-perl libglib2.0-cil libgmime2.6-cil
  libgnome-media-profiles-3.0-0 libgnome2-0 libgnome2-bin libgnome2-common
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common
  libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgoa-backend-1.0-1
  libgrilo-0.2-1 libgsf-1-114 libgsf-1-common libgsl0ldbl libgtk-vnc-2.0-0
  libgtk2-perl libgtk2.0-cil libgtkhtml-4.0-0 libgtkhtml-4.0-common
  libgtkhtml-editor-4.0-0 libgtkspell0 libgupnp-av-1.0-2 libgupnp-dlna-2.0-3
  libgvnc-1.0-0 libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libicc2 libidl-common libidl0 libimdi0 libindicator7
  libio-html-perl libiptcdata0 libjavascriptcoregtk-1.0-0 libjemalloc1
  liblapack3 liblinear-tools liblinear1 liblqr-1-0 liblwp-mediatypes-perl
  liblwp-protocol-https-perl libmagick++5 libmagickcore5 libmagickcore5-extra
  libmagickwand5 libmail-spf-perl libmediaart-1.0-0 libmng2
  libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo4.0-cil
  libmono-corlib4.0-cil libmono-corlib4.5-cil libmono-i18n-west4.0-cil
  libmono-i18n4.0-cil libmono-posix4.0-cil libmono-security4.0-cil
  libmono-sharpzip4.84-cil libmono-system-configuration4.0-cil
  libmono-system-core4.0-cil libmono-system-drawing4.0-cil
  libmono-system-security4.0-cil libmono-system-xml4.0-cil
  libmono-system4.0-cil libmozjs-24-0 libmusicbrainz5-0 libmutter0c
  libnet-http-perl libnetaddr-ip-perl libnetpbm10 liborbit-2-0 liborbit2
  libpanel-applet-4-0 libpango-perl libpst4 librygel-core-2.0-1
  librygel-renderer-2.0-1 librygel-renderer-gst-2.0-1 librygel-server-2.0-1
  libsdl1.2debian libsigsegv2 libsofia-sip-ua-glib3 libsofia-sip-ua0
  libsys-hostname-long-perl libtracker-extract-0.16-0 libtracker-miner-0.16-0
  libtracker-sparql-0.16-0 libumfpack5.6.2 libwebkitgtk-1.0-0
  libwebkitgtk-1.0-common libwmf-bin libwww-perl libwww-robotrules-perl
  libxcb-keysyms1 libxcb-xf86dri0 libxcb-xv0 libytnef0 libzapojit-0.0-0
  lightsoff metacity mono-4.0-gac mono-gac mono-runtime mono-runtime-common
  mono-runtime-sgen mutter-common netpbm nmap notification-daemon perlmagick
  python-appindicator python-gnome2 python-numpy python-pyatspi python-pyorbit
  python-wnck quadrapassel re2c rygel rygel-playbin rygel-preferences
  sa-compile sound-juicer spamassassin spamc swell-foop tali telepathy-rakia
  tomboy tracker tracker-extract tracker-gui tracker-miner-fs tracker-utils
  transfig unoconv vinagre whois xserver-xephyr
Suggested packages:
  gir1.2-colordgtk-1.0 browser-plugin-lightspark evolution-ews
  evolution-plugins-experimental gawk-doc gimp-help-en gimp-help
  gimp-data-extras dia-gnome gnome-boxes gnucash libreoffice-evolution planner
  gnome-netstatus-applet deskbar-applet cpufrequtils gnome-hearts
  gnome-system-tools gnome-packagekit-tools xboard eboard scid
  python-evolution imagemagick-doc autotrace curl enscript gnuplot grads hp2xx
  html2ps mplayer povray radiance texlive-base-bin ufraw-batch pstoedit
  libsvg-perl libxml-xql-perl python-uniconvertor ruby libbonobo2-bin
  libfont-freetype-perl libdiscid0-dbg monodoc-gtk2.0-manual libgnomevfs2-bin
  gamin fam gnome-mime-data gsl-ref-psdoc gsl-doc-pdf gsl-doc-info
  gsl-ref-html libgtk2-perl-doc libdata-dump-perl libsvm-tools liblinear-dev
  libcrypt-ssleay-perl libmono-i18n4.0-all libgamin0 sofia-sip-doc
  libauthen-ntlm-perl python-gnome2-doc gfortran python-dev python-nose
  python-numpy-dbg python-numpy-doc python-pyorbit-dbg rygel-tracker
  rygel-mediathek tumbler gstreamer1.0-lame gstreamer1.0-plugins-really-bad
  razor libdbi-perl pyzor libmail-dkim-perl tasque xfig
Recommended packages:
  gstreamer0.10-ffmpeg
The following NEW packages will be installed:
  alacarte argyll binfmt-support browser-plugin-gnash caribou caribou-antler
  cli-common dconf-editor dconf-tools desktop-base evolution evolution-common
  evolution-indicator evolution-plugins finger five-or-more fonts-cantarell
  four-in-a-row freerdp-x11 gawk gdebi gdebi-core gdm gedit-plugins gimp
  gimp-data gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0
  gir1.2-evince-3.0 gir1.2-gck-1 gir1.2-gconf-2.0 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0
  gir1.2-gnomedesktop-3.0 gir1.2-gtkclutter-1.0 gir1.2-gtop-2.0
  gir1.2-gucharmap-2.90 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-nmgtk-1.0
  gir1.2-panelapplet-4.0 gir1.2-polkit-1.0 gir1.2-rest-0.7
  gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-tracker-0.16
  gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gir1.2-zeitgeist-2.0 gir1.2-zpj-0.0 gjs
  gksu gnash gnash-common gnome gnome-applets gnome-applets-data
  gnome-backgrounds gnome-chess gnome-color-manager gnome-control-center
  gnome-control-center-data gnome-core gnome-dictionary gnome-documents
  gnome-games gnome-icon-theme-extras gnome-icon-theme-full gnome-klotski
  gnome-media gnome-nettool gnome-nibbles gnome-online-accounts
  gnome-online-miners gnome-packagekit gnome-packagekit-data
  gnome-packagekit-session gnome-panel gnome-panel-data gnome-robots
  gnome-session gnome-session-flashback gnome-settings-daemon gnome-shell
  gnome-shell-common gnome-shell-extensions gnome-sushi gnome-tetravex
  gnome-themes-standard gnome-themes-standard-data gnome-tweak-tool gnuchess
  gnuchess-book grilo-plugins-0.2 gstreamer0.10-gconf gtk2-engines
  gtk2-engines-pixbuf hamster-applet hamster-indicator iagno imagemagick
  imagemagick-common indicator-applet-complete inkscape libamd2.3.1
  libappindicator0.1-cil libappindicator1 libavahi-ui-gtk3-0 libavresample1
  libbabl-0.1-0 libblas3 libbonobo2-0 libbonobo2-common libbonoboui2-0
  libbonoboui2-common libboost-iostreams1.54.0 libboost-program-options1.54.0
  libboost-thread1.54.0 libcairo-perl libcamd2.3.1 libcaribou-common
  libcaribou-gtk-module libcaribou-gtk3-module libcaribou0 libccolamd2.8.0
  libcholmod2.1.2 libcolord-gtk1 libdbus-glib2.0-cil libdbus2.0-cil libdiscid0
  libencode-locale-perl liberror-perl libevolution libfile-listing-perl
  libfont-afm-perl libgconf2.0-cil libgdict-1.0-6 libgdict-common libgdiplus
  libgdm1 libgegl-0.2-0 libgfortran3 libgif4 libgimp2.0 libgjs0e libgksu2-0
  libglade2-0 libglib-perl libglib2.0-cil libgmime2.6-cil
  libgnome-media-profiles-3.0-0 libgnome2-0 libgnome2-bin libgnome2-common
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common
  libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgoa-backend-1.0-1
  libgrilo-0.2-1 libgsf-1-114 libgsf-1-common libgsl0ldbl libgtk-vnc-2.0-0
  libgtk2-perl libgtk2.0-cil libgtkhtml-4.0-0 libgtkhtml-4.0-common
  libgtkhtml-editor-4.0-0 libgtkspell0 libgupnp-av-1.0-2 libgupnp-dlna-2.0-3
  libgvnc-1.0-0 libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libicc2 libidl-common libidl0 libimdi0 libindicator7
  libio-html-perl libiptcdata0 libjavascriptcoregtk-1.0-0 libjemalloc1
  liblapack3 liblinear-tools liblinear1 liblqr-1-0 liblwp-mediatypes-perl
  liblwp-protocol-https-perl libmagick++5 libmagickcore5 libmagickcore5-extra
  libmagickwand5 libmail-spf-perl libmediaart-1.0-0 libmng2
  libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo4.0-cil
  libmono-corlib4.0-cil libmono-corlib4.5-cil libmono-i18n-west4.0-cil
  libmono-i18n4.0-cil libmono-posix4.0-cil libmono-security4.0-cil
  libmono-sharpzip4.84-cil libmono-system-configuration4.0-cil
  libmono-system-core4.0-cil libmono-system-drawing4.0-cil
  libmono-system-security4.0-cil libmono-system-xml4.0-cil
  libmono-system4.0-cil libmozjs-24-0 libmusicbrainz5-0 libmutter0c
  libnet-http-perl libnetaddr-ip-perl libnetpbm10 liborbit-2-0 liborbit2
  libpanel-applet-4-0 libpango-perl libpst4 librygel-core-2.0-1
  librygel-renderer-2.0-1 librygel-renderer-gst-2.0-1 librygel-server-2.0-1
  libsdl1.2debian libsigsegv2 libsofia-sip-ua-glib3 libsofia-sip-ua0
  libsys-hostname-long-perl libtracker-extract-0.16-0 libtracker-miner-0.16-0
  libtracker-sparql-0.16-0 libumfpack5.6.2 libwebkitgtk-1.0-0
  libwebkitgtk-1.0-common libwmf-bin libwww-perl libwww-robotrules-perl
  libxcb-keysyms1 libxcb-xf86dri0 libxcb-xv0 libytnef0 libzapojit-0.0-0
  lightsoff metacity mono-4.0-gac mono-gac mono-runtime mono-runtime-common
  mono-runtime-sgen mutter-common netpbm nmap notification-daemon perlmagick
  python-appindicator python-gnome2 python-numpy python-pyatspi python-pyorbit
  python-wnck quadrapassel re2c rygel rygel-playbin rygel-preferences
  sa-compile sound-juicer spamassassin spamc swell-foop tali telepathy-rakia
  tomboy tracker tracker-extract tracker-gui tracker-miner-fs tracker-utils
  transfig unoconv vinagre whois xserver-xephyr
0 upgraded, 305 newly installed, 0 to remove and 3 not upgraded.
Need to get 151 MB of archives.
After this operation, 606 MB of additional disk space will be used.
Do you want to continue? [Y/n] N
Abort.
```

But we'll need to check your /var/log/apt logs to be sure where we're at.

Anyway you may now be using 'gdm' to login rather than 'lightdm'. I compiled a collection of pics here:

[http://ubuntuforums.org/showthread.php?t=2184682&page=27&p=12929682#post12929682](http://ubuntuforums.org/showthread.php?t=2184682&page=27&p=12929682#post12929682)

So you could start by telling us what your login screen looks like and what sessions you see offered. Also what version of Ubuntu you're running.

---

### Post by Connor_Webb on 2014-11-12
Yes I am using Trusty, and the login screen looks exactly the same as it used to, no foot or gdm. And I can't check my [COLOR=#000000]/var/log/apt logs because I can't use my computer at all after login.[/COLOR]

---

### Post by Connor_Webb on 2014-11-12
It does not show any logo at all.

---

### Post by kansasnoob on 2014-11-12
So you do get to [this screen]("http://ubuntuforums.org/attachment.php?attachmentid=250349&d=1392455047") where you can enter your password, but there is nothing at all to click on to the right of your user name?

---

### Post by kansasnoob on 2014-11-13
Another way to go at this would be to open a terminal from the desktop - even though no top panel or launcher appears you should be able to do so by pressing Ctrl + Alt + T. Then type:

```
ls /usr/share/xsessions
```

What available sessions does that display?

If you can launch a terminal that way you may also be able to launch other apps just by typing their proper names, eg; firefox.

In terminal you could also try:

```
sudo dpkg-reconfigure lightdm
```

That may give you the option of choosing to use either lightdm or gdm.

---


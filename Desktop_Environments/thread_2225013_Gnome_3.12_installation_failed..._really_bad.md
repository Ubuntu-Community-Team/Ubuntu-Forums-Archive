---
title: "Gnome 3.12 installation failed... really bad"
date: 2014-05-19
forum: Desktop Environments
---

### Post by The musmula on 2014-05-19
hi all!
So, today I decided to give the new gnome 3.12 a try on my ubuntu machine, I followed the instructions provided here = [http://askubuntu.com/questions/452864/how-to-get-gnome-shell-3-12-on-ubuntu-14-04](http://askubuntu.com/questions/452864/how-to-get-gnome-shell-3-12-on-ubuntu-14-04)

and... it didn`t go out well, I followed the instructions but... I have now several issues
1) the login screen... it is... grey... dead... I don`t know if that is a new feature in gnome but, if it is... I hate it... Since ubuntu 14.04 came with that nice new unity login screen that is so much more beautiful. So I want to remove that
2) When I log in, nothing happens, I see my mouse and that grey screen and... nothing else... I am quite sure that the new gnome shell update includes a GUI lol
i have managed to start unity and to post this, but... I have also some keyboard bugs and it is hard to type this... this way, and I cannot change the layout back to croatian since I have no notifications area after I started unity

---

### Post by kansasnoob on 2014-05-19
GNOME 3.12 is NOT ready for prime time! **It should only be used in Ubuntu GNOME, not in Ubuntu as it breaks the the heck out of Unity!**

The instructions on that page are almost beyond horrible also. If you do want to use the staging PPA:

[https://launchpad.net/~gnome3-team/+archive/gnome3-staging](https://launchpad.net/~gnome3-team/+archive/gnome3-staging)

It says very clearly:

> === *WARNING* ===
The packages here have been deemed not ready for general use, they have known bugs and/or regressions, sometimes of a critical nature. Mostly things should run smoothly but be prepared to use ppa-purge, when you encounter issues!

If they break your system, you get to keep both halves.

And:

> === Installing ===
To use this PPA, you should enable the main GNOME3 PPA.

That means also use this PPA:

[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

And also:

> You need to run 'sudo apt-get dist-upgrade' to avoid problems. Please read the output before entering 'Y' to make sure important packages won't be removed.

But I tried it over the weekend and a lot of stuff is broken!!!!!

I tried adding the Ricotz PPA:

[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

And that made things even worse so I opted for a fresh install rather than even messing with ppa-purge.

---

### Post by The musmula on 2014-05-19
yeah, I see how stupid that was now... So, I am viewing your messeage from a live CD that I have had around and the reason for that is...
I purged the ppd
The grey login screen remained
so I removed gnome-shell
The smexy login screen is back
inputed my password
"Failed to start session" he said (or something like that anyway)
so.. yeah... not good
Since I`ve expected issues when I installed ubuntu, I have my /home on a seperate partition

My plan:
install ubuntu desktop on my old / partition
set my old /home as /home (question: will that format it, regardless what the formating checkbox says?)
install ubuntu GNOME on another partition and  set the /home folder of the desktop to be the /home folder of the GNOME version... will that format it?

---

### Post by philinux on 2014-05-19
[http://www.omgubuntu.co.uk/2014/05/upgrade-gnome-3-12-ubuntu-14-04](http://www.omgubuntu.co.uk/2014/05/upgrade-gnome-3-12-ubuntu-14-04)

I'm trying this but only on a test partition of 14.04.

---

### Post by The musmula on 2014-05-19
nice, but I did it on my non-test partition :)
While your here, maybe you can tell me if seting a partition to /home will format it?
But...  before I go and reinstall ubuntu, I might also just install gnome 3.10.  How do I do that from the command line? just sudo apt-get install  gnome-desktop?

---

### Post by kansasnoob on 2014-05-19
> **The musmula said:**
> yeah, I see how stupid that was now... So, I am viewing your messeage from a live CD that I have had around and the reason for that is...
I purged the ppd
The grey login screen remained
so I removed gnome-shell
The smexy login screen is back
inputed my password
"Failed to start session" he said (or something like that anyway)
so.. yeah... not good
Since I`ve expected issues when I installed ubuntu, I have my /home on a seperate partition

My plan:
install ubuntu desktop on my old / partition
set my old /home as /home (question: **[COLOR="#FF0000"]will that format it, regardless what the formating checkbox says?[/COLOR]**)
install ubuntu GNOME on another partition and  **[COLOR="#FF0000"]set the /home folder of the desktop to be the /home folder of the GNOME version... will that format it?[/COLOR]**

This is a rather old screenshot:

[ATTACH=CONFIG]253299[/ATTACH]

But **[COLOR="#FF0000"]selecting Format the partition will erase all data on that partition![/COLOR]**

Sharing a /home partition between distros frequently results in major borkage because they have to share settings stored in the hidden dot files :(

---

### Post by kansasnoob on 2014-05-19
> **The musmula said:**
> nice, but I did it on my non-test partition :)
While your here, maybe you can tell me if seting a partition to /home will format it?
But...  before I go and reinstall ubuntu, I might also just install gnome 3.10.  How do I do that from the command line? just sudo apt-get install  gnome-desktop?

There is no meta-package 'gnome-desktop' and you DO NOT just want to install 'gnome' because it's basically the whole Debian-ish GNOME DE:

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
[COLOR="#FF0000"]The following NEW packages will be installed:
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
**After this operation, 606 MB of additional disk space will be used**.[/COLOR]
Do you want to continue? [Y/n] N
Abort.
```

What desktop environment do you want?

If you want the "flashback" DE I made some notes here:

[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)

If you want "gnome-shell" and/or the new "classic" DE you can just install the package 'gnome-shell-extensions' but that also installs 'gdm' (although you'll be given the choice of using 'gdm' or 'lightdm').

But mixing desktop environments ATM is much messier than it used to be :(

IMHO if you want to use "gnome-shell" it's best to just install Ubuntu GNOME, if you want Unity install Ubuntu. Flashback w/Metacity seems to run fairly well in both Ubuntu and Ubuntu GNOME, but changing settings in one session frequently borks the default session :(

---

### Post by kurt18947 on 2014-05-20
I have 3.12 installed over 3.10 in Ubuntu Gnome 14.04 on two different machines.  It seems quite stable.  The only annoyance so far is that several extensions I favor have not yet made the 3.10 > 3.12 transition.  I used this guide:

[URL="http://askubuntu.com/questions/452864/how-to-get-gnome-shell-3-12-on-ubuntu-14-04"]http://askubuntu.com/questions/452864/how-to-get-gnome-shell-3-12-on-ubuntu-14-04

[FONT=arial][/FONT]
[/URL]

---

### Post by The musmula on 2014-05-20
Thank you all for the amazing amount of reply
"What DE do you want?" ==> gnome 3.10 or later (maybe 3.8 would do also), not the fallback thogh it is compatible with compitz I`ve already used it and now I am curious about the new 3.12 (though I never used 3.10 eighter)


a little update:
Installing ubuntu over again solved the problem (DUH), and as I said since I have my /home on a other partitin my settings and data survived. Though I didn`t set that partition to be /home in the install, I`ve just changed the fstab file from /etc/fstab
I also made some space and added a new partition which I will use for ubuntu GNOME

Thanks for everyones help, and btw, reinstalling the system my odd keyboard bug dissapeared, the bug from this post:
[http://ubuntuforums.org/showthread.php?t=2220564](http://ubuntuforums.org/showthread.php?t=2220564)

em.. sorry, no, it didnt (the keyboard layourd bug is still here), it was ok when I tested the new system for the first time, but now it`s back... does anyone know the command for changing the keyboard layout via terminal (if there is one)?

---


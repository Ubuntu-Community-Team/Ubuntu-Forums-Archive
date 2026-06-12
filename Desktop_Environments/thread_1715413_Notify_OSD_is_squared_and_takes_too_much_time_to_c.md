---
title: "Notify OSD is squared and takes too much time to close"
date: 2011-03-26
forum: Desktop Environments
---

### Post by GTMoraes on 2011-03-26
Title says it all. A picture won't hurt
[[IMG]http://img22.imageshack.us/img22/362/capturadetelavl.th.png[/IMG]](http://i51.tinypic.com/zsn4v4.png)
It takes around 2 minutes to disappear.
I don't know exactly how it started. It was working pretty well.
Before I notice the OSD was messed up, I had disabled Compiz (to test some game) and I've been goofing around with the Awn Dock, moving it around the corners of the screen. Not sure what caused it to bug. I've tried restarting the machine, "sudo apt-get remove notify-osd" and "apt-get install..", I've tried changing system fonts..

What should I do to 'reset' it, or something?
I'll be trying to fix it on my own over here. I'll post back if I get any luck at it.
Thanks

----------

Completely disabling Compiz (Desktop Effects OFF) renders this:

[[IMG]http://img135.imageshack.us/img135/8660/capturadetelag.th.png[/IMG]](http://i56.tinypic.com/2z400p5.png)
Doesn't look right.
The first picture was taken with Compiz enabled.

---

### Post by Krytarik on 2011-03-26
It seems like you are experiencing this "bug":
[https://bugs.launchpad.net/notify-osd/+bug/649838](https://bugs.launchpad.net/notify-osd/+bug/649838)

Are you using Xorg-Edgers' PPA?

Even if so, that doesn't explain the long time before it disappears.

Are you using this app?:
[http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26](http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26)

Or at least a patched version of notify-osd?

---

### Post by GTMoraes on 2011-03-26
Not the latter.
I think I'm using the Xorg's one because I have their repository. Same graphic chipset too. Is there any known way to fix it already?

Also, for some reason, after some GDM restarts, my FN button control for volume, brightness and battery status report (like on the first picture) have disappeared. I also can't find the Battery manager anymore (not even on System > Preferences). Tried restarting, but no luck. I'll google around for it

---

### Post by Krytarik on 2011-03-26
> **GTMoraes said:**
> 
I think I'm using the Xorg's one because I have their repository. Same graphic chipset too. Is there any known way to fix it already?
Not that I know. I enabled those PPA at my mom's system, to get the ATI OSED. I just used the mentioned app to make notify-osd completely squared.
> **GTMoraes said:**
> Also, for some reason, after some GDM restarts, my FN button control for volume, brightness and battery status report (like on the first picture) have disappeared. I also can't find the Battery manager anymore (not even on System > Preferences). Tried restarting, but no luck. I'll google around for it
I would also have to do a web search on it. But I don't think that it's related.

---

### Post by GTMoraes on 2011-03-26
Fixed the power and FN controls, the "gnome-power-manager" was uninstalled. Looks like it got deleted when I ran "remove notify-osd"

---

What might be the cause? It started out of the nowhere, really. It was working pretty well, until a major boredness hit me and I wanted to play a game. Turned off Compiz and played it. Closed the game, restarted compiz and started goofing around with Awn. Someone logged on MSN and I've noticed the weird OSD. Just like that. Tried removing Awn, but nothing happened.

Btw, the "time issue" looks like to happen only when I summon the Battery status (Fn + F1). It takes around 5~10 seconds on normal messages

---------
Hey, I've checked it now - Seems like I'm using a patched Notify-OSD from Xorg Edgers... how can I revert it to Maverick's default?

--------------------------

Tried this:
Disable Xorg's repositories
Remove notify-osd
Restart
Reinstall notify-osd (I've made sure it was getting from the normal source)
 Reinstall gnome-power-management (It gets uninstalled with notify-osd, but not installed together)
Restart
Test

No luck. Still the same thing.

---

### Post by Krytarik on 2011-03-26
> **GTMoraes said:**
> 
Btw, the "time issue" looks like to happen only when I summon the Battery status (Fn + F1). It takes around 5~10 seconds on normal messages
Ok. I believe it's a feature, the same happens when batteries of wireless mice are critically low.
> **GTMoraes said:**
> Hey, I've checked it now - Seems like I'm using a patched Notify-OSD from Xorg Edgers... how can I revert it to Maverick's default?

--------------------------

Tried this:
Disable Xorg's repositories
Remove notify-osd
Restart
Reinstall notify-osd (I've made sure it was getting from the normal source)
 Reinstall gnome-power-management (It gets uninstalled with notify-osd, but not installed together)
Restart
Test

No luck. Still the same thing.
Oh, actually. I didn't know until now that their PPA also provides a patched notifiy-osd. However, those isn't really different, the only difference is that one is able to change its appearance, those feature is imo just disabled in the official version.

It's actually curious that you didn't notice the issue with its corners earlier, because imo this issue is always present when using their packages.

---

### Post by GTMoraes on 2011-03-26
Weird, if I had that issue before, I would have noticed.. the text isn't centered. You really miss a border there.

Also, I've had some 'issues' with the OSD and Dual Monitor setup, with the osd only showing on the top-right corner of the right monitor (which I use only for demonstrations, and work on the notebook screen - but that's another topic). It was good looking, round borders till yesterday - actually, till two hours ago. 

Someone on a russian forum talked about "pixman" and Cairo. I'll try reinstall Cairo from the intellinuxgraphics.org (Also, I'm using the Kernel 2.6.38-4 and the latest graphic drivers, if that matters) and Pixman from.. somewhere. I'll post back with the results

----------
Installed the 0.18.4 (as said on the russian forum/bugtracker it would work) and Cairo 1.10.2, as requested by Intel. No luck, still bugged.
What it may be? I don't wanna reinstall Ubuntu just for this!

---

### Post by Krytarik on 2011-03-27
The "libpixman" package is the actual culprit, I remember:
[http://packages.ubuntu.com/maverick/libpixman-1-0](http://packages.ubuntu.com/maverick/libpixman-1-0)

It's also included by Xorg-Edgers' PPA.

Regarding modifying the position of the notify-osd bubbles, see my earlier post:
[http://ubuntuforums.org/showthread.php?p=10115367](http://ubuntuforums.org/showthread.php?p=10115367)

It refers to this article: [http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26](http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26)

---

### Post by GTMoraes on 2011-03-27
So, uh.. I tried "sudo apt-get remove libpixman-1-0" and the result... well

 ```
gtmoraes@GTMoraes-Aspire:~$ sudo apt-get remove libpixman-1-0
Reading packages list... Ready
Creating dependency tree       
Reading status information... Ready
The following packages have been automatically installed and are not necessary anymore:
  x11proto-resource-dev libcommons-collections3-java libfontenc-dev
  python-awn-extras libxmuu-dev junit4 libecj-java bzrtools libxaw7-dev
  libasm3-java libatk1.0-dev swh-plugins libbabl-0.0-0 libgcj-bc
  x11proto-fonts-dev x11proto-xf86dga-dev x11proto-gl-dev libxcb-shm0-dev
  python-paramiko libcommons-el-java fortunes-min junit x11proto-bigreqs-dev
  python-libmimic libcommons-compress-java libregexp-java libxmlrpc-c3
  cheese-common libjasper-java libcommons-httpclient-java libxxf86dga-dev
  libpciaccess-dev libservlet2.4-java fortune-mod liblucene2-java libdmx-dev
  libslf4j-java zeitgeist eclipse-platform-data python-utidylib
  gcj-4.4-jre-lib libxfont-dev libgcj10 zeitgeist-core python-configobj
  libtre5 libfs-dev x11proto-composite-dev libdb4.7-java-gcj libdmx1
  librecode0 libtidy-0.99-0 x11proto-dmx-dev ant x11proto-dri2-dev
  libcommons-logging-java gcj-4.4-base libcommons-codec-java jarwrapper
  libequinox-osgi-java bzr python-compizconfig libgcj-common
  x11proto-scrnsaver-dev x11proto-xf86bigfont-dev x11proto-damage-dev
  libjaxp1.3-java ladspa-sdk libjetty-java python-feedparser libjline-java
  avant-window-navigator-data libxdamage-dev libxerces2-java
  zeitgeist-fts-extension human-icon-theme sat4j libxpm-dev python-dateutil
  libcommons-beanutils-java libdbus-glib-1-dev libdb-je-java libxcomposite-dev
  zeitgeist-datahub fastjar libdb4.7-java libcommons-digester-java
  x11proto-xf86vidmode-dev libhamcrest-java libjtidy-java xsel
  libservlet2.5-java libicu4j-java libxxf86vm-dev libxres-dev
  libxcb-render0-dev libjsch-java awn-applets-common x11proto-xcmisc-dev
  gimp-data ant-optional transmission-cli x11proto-xf86dri-dev
  libzeitgeist-1.0-0 libgdk-pixbuf2.0-dev libxss-dev libxkbfile-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be uninstalled:
  akonadi-server apturl-kde gsfonts-x11 kdebase-runtime kdebase-runtime-data
  kdelibs-bin kdelibs5-data kdelibs5-plugins kdepim-runtime
  kdepimlibs-kio-plugins kdesudo kdoctools kubuntu-debug-installer
  libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4
  libakonadiprivate1 libattica0 libboost-program-options1.42.0 libclucene0ldbl
  libdbusmenu-qt2 libiodbc2 libkabc4 libkatepartinterfaces4 libkcal4
  libkdecore5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkfile4 libkhtml5
  libkimap4 libkio5 libkjsapi4 libkjsembed4 libkldap4 libkmediaplayer4
  libkmime4 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4
  libkparts4 libkpimutils4 libkpty4 libkresources4 libkrosscore4 libkrossui4
  libktexteditor4 libkutils4 libmailtransport4 libmicroblog4 libnepomuk4
  libnepomukquery4a libplasma3 libpolkit-qt-1-0 libqapt-runtime libqapt1
  libqca2 libsolid4 libsoprano4 libstreamanalyzer0 libstreams0
  libthreadweaver4 libvirtodbc0 mysql-client-core-5.1 mysql-server-core-5.1
  oxygen-icon-theme plasma-scriptengine-javascript python-kde4 qapt-batch
  shared-desktop-ontologies software-properties-kde soprano-daemon
  sun-java6-bin sun-java6-jre ttf-dejavu virtuoso-minimal
  virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
Suggested packages:
  djvulibre-bin hspell libqca2-plugin-cyrus-sasl libqca2-plugin-gnupg
  libqca2-plugin-ossl libqca2-plugin-pkcs11 sun-java6-plugin
  ia32-sun-java6-plugin sun-java6-fonts ttf-kochi-gothic ttf-sazanami-gothic
  ttf-kochi-mincho ttf-sazanami-mincho ttf-arphic-uming
The following packages will be REMOVED:
  aisleriot alacarte apport-gtk apturl at-spi avant-window-navigator
  awn-applets-c-core awn-applets-python-core awn-settings baobab boxee brasero
  brasero-cdrkit breathe-icon-theme brltty-x11 checkbox-gtk cheese
  community-themes compiz compiz-fusion-plugins-main compiz-gnome
  compiz-plugins compizconfig-settings-manager computer-janitor-gtk
  couchdb-bin default-jdk default-jre desktopcouch desktopnova
  desktopnova-module-gnome desktopnova-tray eclipse eclipse-jdt eclipse-pde
  eclipse-platform eclipse-plugin-cvs eclipse-rcp emesene empathy eog evince
  evolution evolution-couchdb evolution-data-server evolution-exchange
  evolution-indicator evolution-plugins evolution-webcal file-roller firefox
  firefox-branding firefox-gnome-support flashplugin-installer gbrainy
  gcalctool gconf-editor gdm gdm-guest-session gedit gimp gksu gnome-about
  gnome-accessibility-themes gnome-applets gnome-bluetooth gnome-codec-install
  gnome-control-center gnome-dictionary gnome-disk-utility gnome-games-common
  gnome-icon-theme gnome-keyring gnome-mag gnome-mahjongg gnome-media
  gnome-menus gnome-nettool gnome-orca gnome-panel gnome-power-manager
  gnome-screensaver gnome-screenshot gnome-search-tool gnome-session
  gnome-session-bin gnome-session-canberra gnome-settings-daemon gnome-sudoku
  gnome-system-log gnome-system-monitor gnome-system-tools gnome-terminal
  gnome-themes-selected gnome-themes-ubuntu gnome-user-guide
  gnome-user-guide-en gnome-user-guide-pt gnome-utils gnomine
  google-chrome-stable gstreamer0.10-plugins-bad gstreamer0.10-plugins-good
  gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf
  gucharmap gvfs gvfs-backends gvfs-fuse gwibber gwibber-service
  humanity-icon-theme ibus ibus-gtk ibus-pinyin ibus-table icedtea6-plugin
  indicator-applet indicator-applet-session indicator-application indicator-me
  indicator-messages indicator-session indicator-sound iscan jockey-gtk
  language-selector libaccess-bridge-java libaccess-bridge-java-jni
  libappindicator0.1-cil libappindicator1 libatspi1.0-0 libavahi-ui0 libawn1
  libbonoboui2-0 libbrasero-media1 libcairo-gobject2 libcairo-perl libcairo2
  libcairo2-dev libcairomm-1.0-1 libcanberra-gtk-module libcanberra-gtk0
  libcheese-gtk18 libclutter-1.0-0 libclutter-gtk-0.10-0 libcryptui0
  libdbusmenu-gtk1 libdesktop-agnostic-cfg-gconf libdesktop-agnostic-fdo-glib
  libdesktop-agnostic-vfs-gio libdesktop-agnostic0 libedataserverui1.2-8
  libevdocument3 libevolution libevview3 libgail-common libgail-gnome-module
  libgail18 libgcr0 libgdict-1.0-6 libgdu-gtk0 libgegl-0.0-0 libgimp2.0
  libgksu2-0 libglade2-0 libglade2.0-cil libglademm-2.4-1c2a libgladeui-1-9
  libgnome-bluetooth8 libgnome-desktop-2-17 libgnome-media0
  libgnome-window-settings1 libgnome2-canvas-perl libgnome2-perl
  libgnome2.24-cil libgnomecanvas2-0 libgnomekbd4 libgnomepanel2.24-cil
  libgnomeui-0 libgoocanvas3 libgstfarsight0.10-0 libgtk-vnc-1.0-0
  libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtk2.0-dev
  libgtkhtml-editor0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview2.0-0
  libgtkspell0 libgucharmap7 libgvc5 libgweather1 libgwibber0 libido-0.1-0
  libindicate-gtk2 libindicator1 liblaunchpad-integration1
  liblaunchpad-integration1.0-cil libmagickcore3-extra libmetacity-private0
  libmono-addins-gui0.2-cil libmono-cairo2.0-cil libnautilus-extension1
  libnotify-bin libnotify-dev libnotify1 libpanel-applet2-0 libpango-perl
  libpango1.0-0 libpango1.0-dev libpangomm-1.4-1 libpixman-1-0 libpixman-1-dev
  libpolkit-gtk-1-0 libpoppler-glib5 libpurple0 librsvg2-2 librsvg2-common
  libsexy2 libsyncdaemon-1.0-1 libtelepathy-farsight0 libubuntuone-1.0-1
  libunique-1.0-0 libvte9 libwebkit-1.0-2 libwnck22 light-themes metacity
  mousetweaks nautilus nautilus-sendto nautilus-sendto-empathy nautilus-share
  network-manager-gnome network-manager-pptp-gnome notification-daemon
  notify-osd notifyosdconfig onboard openjdk-6-jdk openjdk-6-jre
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-emailmerge
  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-gb
  openoffice.org-help-en-us openoffice.org-help-pt openoffice.org-help-pt-br
  openoffice.org-impress openoffice.org-l10n-en-gb openoffice.org-l10n-en-za
  openoffice.org-l10n-pt openoffice.org-l10n-pt-br openoffice.org-math
  openoffice.org-style-human openoffice.org-writer pavucontrol pipslite pitivi
  plymouth-label plymouth-theme-ubuntu-logo policykit-1-gnome
  pulseaudio-equalizer python-appindicator python-aptdaemon-gtk python-awn
  python-cairo python-desktop-agnostic python-desktopcouch-records
  python-evolution python-farsight python-glade2 python-gmenu python-gnome2
  python-gnomeapplet python-gnomecanvas python-gnomedesktop
  python-gnomekeyring python-gobject-cairo python-gtk2 python-gtkmozembed
  python-gtksourceview2 python-gtkspell python-gtop python-gweather
  python-ibus python-indicate python-launchpad-integration python-notify
  python-papyon python-pyatspi python-pygoocanvas python-rsvg python-ubuntuone
  python-ubuntuone-client python-uno python-virtkey python-vte python-webkit
  python-wnck python-xklavier quadrapassel rhythmbox
  rhythmbox-plugin-cdrecorder rhythmbox-plugins
  rhythmbox-ubuntuone-music-store screenlets seahorse sessioninstaller
  shotwell simple-ccsm simple-scan software-center software-properties-gtk
  ssh-askpass-gnome synaptic system-config-printer-gnome telepathy-butterfly
  telepathy-haze tomboy totem totem-mozilla totem-plugins transmission
  transmission-gtk tsclient ubuntu-artwork ubuntu-docs ubuntu-mono
  ubuntu-sso-client ubuntu-tweak ubuntuone-client ubuntuone-client-gnome
  update-manager usb-creator-gtk vinagre vino xdg-user-dirs-gtk xorg xorg-dev
  xserver-xorg xserver-xorg-core xserver-xorg-dev xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-geode
  xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-vesa xserver-xorg-video-vmware
  xserver-xorg-video-voodoo xulrunner-1.9.2 yelp zenity
The NEW following packages will be installed:
  akonadi-server apturl-kde gsfonts-x11 kdebase-runtime kdebase-runtime-data
  kdelibs-bin kdelibs5-data kdelibs5-plugins kdepim-runtime
  kdepimlibs-kio-plugins kdesudo kdoctools kubuntu-debug-installer
  libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4
  libakonadiprivate1 libattica0 libboost-program-options1.42.0 libclucene0ldbl
  libdbusmenu-qt2 libiodbc2 libkabc4 libkatepartinterfaces4 libkcal4
  libkdecore5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkfile4 libkhtml5
  libkimap4 libkio5 libkjsapi4 libkjsembed4 libkldap4 libkmediaplayer4
  libkmime4 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4
  libkparts4 libkpimutils4 libkpty4 libkresources4 libkrosscore4 libkrossui4
  libktexteditor4 libkutils4 libmailtransport4 libmicroblog4 libnepomuk4
  libnepomukquery4a libplasma3 libpolkit-qt-1-0 libqapt-runtime libqapt1
  libqca2 libsolid4 libsoprano4 libstreamanalyzer0 libstreams0
  libthreadweaver4 libvirtodbc0 mysql-client-core-5.1 mysql-server-core-5.1
  oxygen-icon-theme plasma-scriptengine-javascript python-kde4 qapt-batch
  shared-desktop-ontologies software-properties-kde soprano-daemon
  sun-java6-bin sun-java6-jre ttf-dejavu virtuoso-minimal
  virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
0 packages updated, 82 new packages installed, 394 to be removed and 0 not updated.
It's necessary to download 94,1MB of archives.
After this operation, 972MB of disk space will be free'd.
Do you want to continue [y/n]? n
Abort.
gtmoraes@GTMoraes-Aspire:~$
```

Looks scary. What should I do? Was I supposed to remove or update it?
[SIZE="1"]btw I've translated the output to english manually[/SIZE]

------
tried "sudo apt-get install --reinstall libpixman-1-0", it installed some things, but didn't solve the problem.

---

### Post by Krytarik on 2011-03-27
> **GTMoraes said:**
> So, uh.. I tried "sudo apt-get remove libpixman-1-0" and the result... well

Looks scary. What should I do? Was I supposed to remove or update it?

Yeah, you can't remove it. You could only "ppa-purge" Xorg-Edgers' PPA, or stick with it, and accept the squared corners of notify-osd. Why do you use their PPA then?

---

### Post by GTMoraes on 2011-03-27
> **Krytarik said:**
> Why do you use their PPA then?
Something related to Intel drivers, but then I've used the drivers directly from Intel. Basically I've forgotten to remove the Xorg's PPA from the repository =/

I'll try this 'purge' thing, never used it before

------------

HEI! That did the trick! Thank you very much for this tip and for your patience!

---

### Post by Krytarik on 2011-03-27
If you have the package "ppa-purge" already installed, simply run this command:
```
sudo ppa-purge ppa:xorg-edgers/ppa
```EDIT: Alright then. You're welcome!

---


---
title: "Can't logout after installing kubuntu desktop on ubuntu"
date: 2006-06-18
forum: Desktop Environments
---

### Post by jonboy99 on 2006-06-18
A long story, but to try and cut it short..

Installed dapper drake ubuntu, was working fine.  Then thought i'd install kubuntu desktop, and kdm.  Seemed to work fine but was hanging on logout to the display manager screen, and when shutting down at times.

So I thought i'd uninstall kubuntu desktop, and see if it hung with gdm. (did this from ubuntu desktop).  However, from gdm kde was still there, and i tried going into it (never could resist pressing big red buttons :D ).  Unfotunately i'm now stuck, as the K menu is now missing, and I can't logout.  I can't find any way of getting back into the gdm screen - if I could get back into gnome i could try reinstalling kubuntu desktop and using gdm not kdm and I suspect all would be fine.  Adept is now not working from kde.

kde is set to autologin, so even pushing the reset button gets me back onto the kde desktop with no logout button.  Can't find a way to add this back again.

Is there a terminal command to logout back to the gdm screen?


[EDIT]  sorted now, i'm such a twonk..

---

### Post by aysiu on 2006-06-18
Can you try pressing Alt-F2 and then typing this? ```
kdesu kcontrol
``` if you're still using KDM or ```
gksudo gdmsetup
``` if you're using GDM.

Turn off the autologin.

Then press Control-Alt-Backspace.

---

### Post by jonboy99 on 2006-06-18
Ok, thanks aysiu, managed to get back into gnome now, which is working.  I tried to reinstall kubuntu desktop, but keep getting this error:

> E: kdm: subprocess pre-removal script returned error exit status 1

I have tried removing kdebase and kubuntu desktop, kdm, thinking to try and get rid of everything kde and then reinstalling it might be the way to go but keep getting the same error as above.

Am trying to do all this from synaptic.

---

### Post by aysiu on 2006-06-18
Forget Synaptic. Try this:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by jonboy99 on 2006-06-18
I'm getting somewhere,but still getting similar messages.  The apt-get command removed most things the first time but not gdm.  So  I ran it again, and get this. 

(Note as far as I know i'm not running anyother package manager like synaptic, and only have a firefox window and a terminal window open.  Am in ubuntu at the moment.

Reading package lists... Done
Building dependency tree... Done
Package adept is not installed, so not removed
Package akregator is not installed, so not removed
Package amarok is not installed, so not removed
Package amarok-xine is not installed, so not removed
Package ark is not installed, so not removed
Package arts is not installed, so not removed
Package artsbuilder is not installed, so not removed
Package avahi-daemon is not installed, so not removed
Package bogofilter is not installed, so not removed
Package bogofilter-bdb is not installed, so not removed
Package bogofilter-common is not installed, so not removed
Package debtags is not installed, so not removed
Package enscript is not installed, so not removed
Package flac is not installed, so not removed
Package gtk2-engines-gtk-qt is not installed, so not removed
Package gwenview is not installed, so not removed
Package imagemagick is not installed, so not removed
Package k3b is not installed, so not removed
Package kaddressbook is not installed, so not removed
Package kaffeine is not installed, so not removed
Package kaffeine-xine is not installed, so not removed
Package kamera is not installed, so not removed
Package karm is not installed, so not removed
Package katapult is not installed, so not removed
Package kate is not installed, so not removed
Package kaudiocreator is not installed, so not removed
Package kcontrol is not installed, so not removed
Package kcron is not installed, so not removed
Package kde-guidance is not installed, so not removed
Package kde-style-lipstik is not installed, so not removed
Package kde-systemsettings is not installed, so not removed
Package kdeadmin-kfile-plugins is not installed, so not removed
Package kdebase-bin is not installed, so not removed
Package kdebase-data is not installed, so not removed
Package kdebase-kio-plugins is not installed, so not removed
Package kdebluetooth is not installed, so not removed
Package kdegraphics-kfile-plugins is not installed, so not removed
Package kdelibs-bin is not installed, so not removed
Package kdelibs-data is not installed, so not removed
Package kdelibs4c2a is not installed, so not removed
Package kdemultimedia-kfile-plugins is not installed, so not removed
Package kdemultimedia-kio-plugins is not installed, so not removed
Package kdenetwork-filesharing is not installed, so not removed
Package kdenetwork-kfile-plugins is not installed, so not removed
Package kdepasswd is not installed, so not removed
Package kdepim-kio-plugins is not installed, so not removed
Package kdepim-kresources is not installed, so not removed
Package kdepim-wizards is not installed, so not removed
Package kdeprint is not installed, so not removed
Package kdesktop is not installed, so not removed
Package kdnssd is not installed, so not removed
Package keep is not installed, so not removed
Package kfind is not installed, so not removed
Package kghostview is not installed, so not removed
Package khelpcenter is not installed, so not removed
Package kicker is not installed, so not removed
Package kio-apt is not installed, so not removed
Package kio-locate is not installed, so not removed
Package kitchensync is not installed, so not removed
Package klaptopdaemon is not installed, so not removed
Package klipper is not installed, so not removed
Package kmail is not installed, so not removed
Package kmailcvt is not installed, so not removed
Package kmenuedit is not installed, so not removed
Package kmilo is not installed, so not removed
Package kmix is not installed, so not removed
Package kmplayer-base is not installed, so not removed
Package kmplayer-konq-plugins is not installed, so not removed
Package knetworkconf is not installed, so not removed
Package knotes is not installed, so not removed
Package koffice-data is not installed, so not removed
Package koffice-libs is not installed, so not removed
Package konq-plugins is not installed, so not removed
Package konqueror is not installed, so not removed
Package konqueror-nsplugins is not installed, so not removed
Package konsole is not installed, so not removed
Package kontact is not installed, so not removed
Package konversation is not installed, so not removed
Package kooka is not installed, so not removed
Package kopete is not installed, so not removed
Package korganizer is not installed, so not removed
Package kpdf is not installed, so not removed
Package kpersonalizer is not installed, so not removed
Package kpf is not installed, so not removed
Package kppp is not installed, so not removed
Package krdc is not installed, so not removed
Package krfb is not installed, so not removed
Package krita is not installed, so not removed
Package krita-data is not installed, so not removed
Package kscd is not installed, so not removed
Package kscreensaver is not installed, so not removed
Package kscreensaver-xsavers is not installed, so not removed
Package ksmserver is not installed, so not removed
Package ksnapshot is not installed, so not removed
Package ksplash is not installed, so not removed
Package ksplash-engine-moodin is not installed, so not removed
Package ksvg is not installed, so not removed
Package ksysguard is not installed, so not removed
Package ksysguardd is not installed, so not removed
Package ksystemlog is not installed, so not removed
Package ktorrent is not installed, so not removed
Package kubuntu-artwork-usplash is not installed, so not removed
Package kubuntu-default-settings is not installed, so not removed
Package kubuntu-desktop is not installed, so not removed
Package kubuntu-docs is not installed, so not removed
Package kubuntu-konqueror-shortcuts is not installed, so not removed
Package kwalletmanager is not installed, so not removed
Package kwin is not installed, so not removed
Package kwin-style-crystal is not installed, so not removed
Package language-selector-qt is not installed, so not removed
Package latex-xft-fonts is not installed, so not removed
Package libakode2 is not installed, so not removed
Package libarts1-akode is not installed, so not removed
Package libarts1c2a is not installed, so not removed
Package libartsc0 is not installed, so not removed
Package libavahi-core4 is not installed, so not removed
Package libavahi-qt3-1 is not installed, so not removed
Package libdaemon0 is not installed, so not removed
Package libdbus-qt-1-1c2 is not installed, so not removed
Package libflac++5c2 is not installed, so not removed
Package libgadu3 is not installed, so not removed
Package libgpgme11 is not installed, so not removed
Package libgsl0 is not installed, so not removed
Package libjpeg-progs is not installed, so not removed
Package libk3b2 is not installed, so not removed
Package libkcal2b is not installed, so not removed
Package libkcddb1 is not installed, so not removed
Package libkdepim1a is not installed, so not removed
Package libkipi0 is not installed, so not removed
Package libkleopatra1 is not installed, so not removed
Package libkmime2 is not installed, so not removed
Package libkonq4 is not installed, so not removed
Package libkpimexchange1 is not installed, so not removed
Package libkpimidentities1 is not installed, so not removed
Package libkscan1 is not installed, so not removed
Package libksieve0 is not installed, so not removed
Package libktnef1 is not installed, so not removed
Package liblockdev1 is not installed, so not removed
Package libmimelib1c2a is not installed, so not removed
Package libmodplug0c2 is not installed, so not removed
Package libmpcdec3 is not installed, so not removed
Package libnss-mdns is not installed, so not removed
Package liboggflac3 is not installed, so not removed
Package libopenexr2c2a is not installed, so not removed
Package libpcre3 is not installed, so not removed
Package libpoppler1-qt is not installed, so not removed
Package libpythonize0 is not installed, so not removed
Package libqt-perl is not installed, so not removed
Package libqt3-mt is not installed, so not removed
Package librsync1 is not installed, so not removed
Package libruby1.8 is not installed, so not removed
Package libsamplerate0 is not installed, so not removed
Package libsensors3 is not installed, so not removed
Package libskim0 is not installed, so not removed
Package libsmokeqt1 is not installed, so not removed
Package libtdb1 is not installed, so not removed
Package libtunepimp2c2a is not installed, so not removed
Package libxcomposite1 is not installed, so not removed
Package libxine-main1 is not installed, so not removed
Package libxvmc1 is not installed, so not removed
Package menu-xdg is not installed, so not removed
Package openoffice.org-kde is not installed, so not removed
Package perl-suid is not installed, so not removed
Package poster is not installed, so not removed
Package postfix is not installed, so not removed
Package procmail is not installed, so not removed
Package psutils is not installed, so not removed
Package pykdeextensions is not installed, so not removed
Package python-kde3 is not installed, so not removed
Package python2.4-dev is not installed, so not removed
Package python2.4-kde3 is not installed, so not removed
Package python2.4-qt3 is not installed, so not removed
Package python2.4-sip4-qt3 is not installed, so not removed
Package qca-tls is not installed, so not removed
Package qobex is not installed, so not removed
Package rdiff-backup is not installed, so not removed
Package ruby is not installed, so not removed
Package ruby1.8 is not installed, so not removed
Package scim-qtimm is not installed, so not removed
Package skim is not installed, so not removed
Package speedcrunch is not installed, so not removed
Package ssl-cert is not installed, so not removed
Package vorbis-tools is not installed, so not removed
Package wlassistant is not installed, so not removed
The following packages will be REMOVED
  kdm
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1503kB disk space will be freed.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
(Reading database ... 72653 files and directories currently installed.)
Removing kdm ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
dpkg: error processing kdm (--remove):
 subprocess pre-removal script returned error exit status 1
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 kdm
E: Sub-process /usr/bin/dpkg returned an error code (1)
jonboy99@xp2000ubuntudrake:~$

---

### Post by jonboy99 on 2006-06-18
Ok, just about sorted now, rebooted, went straight to a terminal rather than start X, and did an apt-get remove kdm, which worked, and then I could reinstall kubuntu.

Ta for help :)

---


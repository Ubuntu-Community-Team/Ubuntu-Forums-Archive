---
title: "URGENT HELP: ubuntu messed up after xen"
date: 2008-12-22
forum: General Help
---

### Post by Howitzer777 on 2008-12-22
I installed ubuntu-xen desktop in synaptic and after it was done with everything I had to restart and Now none of the effects work AND it is VERY SLUGGISH. 

I completely removed everything dealing with xen and still no effects.

it won't let me activate my ati flgrx driver. when i click activate it just says "downloading and installing driver:0%" for a second and then stops. 


HELPP!?!?!?!?

---

### Post by Howitzer777 on 2008-12-22
bump help

---

### Post by MarblePanther on 2008-12-22
It sounds like you are using the virtual kernel, try hitting esc at the bootup prompt and choose the kernel you used before

---

### Post by MarblePanther on 2008-12-22
It sounds like you are using the virtual kernel, try hitting esc at the bootup prompt and choose the kernel you used before.


sorry for the double-post--    admin delete?

---

### Post by bodhi.zazen on 2008-12-22
If booting to an older kernel does not help, try:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Howitzer777 on 2008-12-22
using wubi :(

---

### Post by bodhi.zazen on 2008-12-22
> **Howitzer777 said:**
> using wubi :(

That should not matter.

---

### Post by Howitzer777 on 2008-12-22
that command didn't work

[QUOTE=terminal]joseph@ubuntu:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
The following packages were automatically installed and are no longer required:
  python-crypto knetwalk kpat libmarble4 libterm-readline-gnu-perl kdepim kolf
  ksystemlog kscreensaver-xsavers krdc krfb kscd kppp kshisen libqca2
  kmahjongg libsbigudrv0 libqimageblitz4 kcharselect kdebase-workspace
  kjumpingcube kdeartwork-style kdeartwork-misc kdessh kanagram libksane0
  libqt4-assistant kdeplasma-addons-data debootstrap knode kblocks katomic
  kdegames-card-data kscreensaver kruler kolourpaint4 pinentry-gtk2 ktux
  python-plasma-examples klettres kgoldrunner libnet-daemon-perl kgeography
  ksnapshot libcfitsio3 libkipi5 python-paramiko kblackbox mplayer-skins
  python-plasma libbeecrypt6 kiriki konsolekalendar libqt4-test kfloppy
  libkleo4 kstars ttf-dustin ksame kbruch kcolorchooser gwenview libdbi-perl
  libdbd-mysql-perl bridge-utils vnstat libkdegames4 kde-core mysql-server-5.0
  kcalc libkipi-common libvncserver0 klipper libmimelib4
  kdemultimedia-kio-plugins parley kdeplasma-addons libqt4-core kontact
  mysql-client-5.0 libfftw3-3 kdeartwork-theme-icon python-dev
  kdebase-workspace-libs4+5 kweather kmplot python-qt4-common kdiamond kalzium
  ksysguard ksirk libmaildir4 ksquares libexiv2-4 libkcddb4 libcln5
  python2.5-dev kde-icons-mono kmouth kalarm kdegames-mahjongg-data
  kalzium-data kdegames libplrpc-perl amor ktouch kgeography-data ktnef
  kdeaccessibility kbreakout kbounce kfourinline libakonadiprivate1
  libqt4-xmlpatterns korganizer kdetoys akregator xfsprogs kollision
  libqt4-help python-qt4 kamera ark sweeper libkpgp4 kwordquiz kcron
  libqt4-webkit libqalculate4 kdebase-workspace-bin bovo librpm4.4 python-rpm
  libkdepim4 kdenetwork libio-stty-perl perl-suid linux-server
  kdeartwork-emoticons step python-qt4-dbus python-sip4 akonadi-kde
  kdewallpapers libksieve4 kuser systemsettings klettres-data
  kimagemapeditor-kde4 kreversi kdf kdm kspaceduel kig gnupg-agent ksudoku juk
  kalgebra klines kdemultimedia kstars-data lskat kdenetwork-filesharing
  knotes kgamma libtunepimp5 kubrick kdeutils rpm libpoppler-qt4-3 kdegraphics
  khangman kaddressbook libzip1 libopenbabel3 marble libplasma2
  kdebase-workspace-data knetworkconf kdeartwork-theme-window ksysguardd
  kdepimlibs5 libio-pty-perl libtext-template-perl parley-data libkholidays4
  kbattleship kdeadmin kdegraphics-strigi-plugins akonadi-server
  libconfig-inifiles-perl libkdeedu4 kwalletmanager libqca2-plugin-ossl
  knewsticker exiv2 ktimetracker kdepim-strigi-plugins kopete libokularcore1
  okteta kdeplasma-addons-libs4 indi kmail kdeedu kpercentage superkaramba
  marble-data kjots kde-printer-applet rinse kmines kget libnova-0.12-2 kgpg
  konquest kdepimlibs-data libterm-size-perl libboost-python1.34.1 okular
  kmousetool kmag libofa0 kdepim-kresources kdepim-wizards ktuberling
  libexpect-perl kturtle ktimer python-kde4 kteatime kmix kdeartwork kode
  libungif4g
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joseph@ubuntu:~$ 
joseph@ubuntu:~$ 
[/QUOTE]

---

### Post by Howitzer777 on 2008-12-22
bump

---

### Post by Howitzer777 on 2008-12-22
bump

---

### Post by Howitzer777 on 2008-12-22
bump h4lp

---

### Post by bodhi.zazen on 2008-12-22
Please do not bump your own threads. In general once every 24 hours at most.

Instead of bumping, tell us what you have done and tried.

Looks like you have installed a lot of software.

Did you try booting to an older kernel ?

---


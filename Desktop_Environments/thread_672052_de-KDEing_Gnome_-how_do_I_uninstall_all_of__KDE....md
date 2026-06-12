---
title: "de-KDEing Gnome -how do I uninstall all of  KDE...?"
date: 2008-01-19
forum: Desktop Environments
---

### Post by seantm on 2008-01-19
Hello all, and thanks in advance... I installed Kubuntu  over gnome using the command line ie.," sudo apt-get..." Actually , it was a bit of an experiment.. I wanted to see how it looked vs standard ubuntu...

So I've determined  that's it's more than I need --I like the streamline feel of standard Ubuntu...I'd like to run it without the all the KDE stuff again...My question is how do I it? I've tired using command line and synaptic package manager to remove everything KDE but there's still tons of "k" stuff in the program files and applications start manager... It's pernicious and stubborn...:confused: Almost like --dare I say it well... Another infamous GUI.... It's seems really hard to clean out all the KDE stuff in there... Including an annoying Kubuntu log-on screen that appeared after I did the install...

Any tips or advice on how to de--KDE the system would be highly appreciated... Thanks in advance once more --S.

---

### Post by Incense on 2008-01-19
Getting your system back to pure Gnome. (Though I don't see why you'd want to do that. ;) )

[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts debtags digikam dolphin enscript fftw3 foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hplip-gui hwdb-client-kde ijsgutenprint k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libclucene0 libcluceneindex0 libdbus-qt-1-1c2 libept0 libexiv2-0 libflac++6 libgmp3c2 libgpgme11 libid3tag0 libifp4 libijs-0.35 libimlib2 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw1 libkdepim1a libkexiv2-1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmimelib1c2a libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0 libopenexr2c2a libopenobex1 libpoppler-qt2 libpq5 libpth20 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsamplerate0 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libungif4g libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 libxvmc1 mysql-common network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-qt4-dbus python-sip4 python2.5-dev qca-tls rdiff-backup restricted-manager-kde ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon && sudo apt-get install ubuntu-desktop
```

---

### Post by seantm on 2008-01-19
Wow --that was helpful and FAST-I'm back where I started and wanted to be... Thanks much...As for the why...hmmm... perhaps it's because I'm new to ubuntu -i want to explore it in it's basic state without having to wade through the layers of KDE stuff..? I've got compiz installed so I can l aready tweak the desktop to almost anything... 

Perhaps as time goes on i'll give the new KDE 4.o a try I do hear it's pretty and pretty impressive...Any thanks again --I LOVE the Ubuntu community! :-)

---

### Post by Incense on 2008-01-19
I'm glad I could help you out. I'm a KDE guy, but Ubuntu clearly shines when you're using Gnome, so I do get it. Have a great day!

---

### Post by Nordfjord on 2008-01-19
I did the same thing a while back. Something you should make note of: you probably installed about 600mb of KDE stuff, but when you removed it only 400mb were cleaned -- that's what I noticed when I did it. You still have Konquerer, Konsole, and a few other K-apps, although the majority are gone.

You probably won't want this stuff anymore, so you should spend a little time doing house-cleaning after sudo apt-get remove.

---

### Post by seantm on 2008-01-19
Thanks for the tip, I alos used  command line, synaptic manager and uninstall and most of it -including Konquerer, konsole and the apps have finally  disappeared --you're right... It took me all those measures to purge the system --the K files hung in there quite stubbornly... Whew...4.0 must really embed itself...

---


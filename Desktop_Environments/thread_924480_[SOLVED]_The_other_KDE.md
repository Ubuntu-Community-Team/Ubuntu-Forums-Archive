---
title: "[SOLVED] The other KDE"
date: 2008-09-19
forum: Desktop Environments
---

### Post by metacognition on 2008-09-19
I finished downloading and installing KDE 4.1 (Woo!), but now I still have all the KDE 3.x stuff now and I don't need them since I have the KDE4 versions. Should I, and How do I get rid of them?

Thanks again.

---

### Post by aysiu on 2008-09-20
Try pasting this into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get remove amarok amarok-xine ark arts brltty cdrdao desktop-effects-kde digikam dmz-cursor-theme dolphin enscript foomatic-db-gutenprint gdebi-core gdebi-kde gtk-qt-engine gwenview hpijs-ppds ijsgutenprint k3b kaffeine kamera katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-qtcurve kde-systemsettings kdeadmin-kfile-plugins kdebase-data kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdeprint kdm kdnssd keep kfind kghostview kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf konq-plugins konqueror konqueror-nsplugins konversation kooka kopete kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-desktop kvkbd kwalletmanager kwin-style-crystal libakode2 libao2 libarts1-akode libbrlapi0.5 libflac++6 libgadu3 libgpod-common libgpod3-nogtk libifp4 libijs-0.35 libjpeg-progs libk3b2 libkbluetooth0 libkcddb1 libkdcraw3 libkexiv2-3 libkipi0 libkscan1 libmeanwhile1 libmtp7 libnjb5 libopenobex1 libpoppler-qt2 libpythonize0 libqt-perl libraw1394-8 librsync1 libruby1.8 libsamplerate0 libsearchclient0 libsgutils1 libsmokeqt1 libstrigihtmlgui0 libvisual-0.4-0 perl-suid poster psutils pykdeextensions python-dev python-kde3 python2.5-dev qca-tls rdesktop rdiff-backup ruby ruby1.8 strigi-applet vorbis-tools xcursor-themes && sudo apt-get install kubuntu-kde4-desktop
```

---

### Post by metacognition on 2008-09-20
Thanks, it works but now the menu has no more icons. They're all folders, is that normal?

---

### Post by benerivo on 2008-09-20
What does your main menu now show? Does it contain any programs at all - eg. konqueror, dolphin, gwenview, or konsole...
Make sure you have logged out and back in, after performing such a large uninstall of packages.

---

### Post by aysiu on 2008-09-20
> **metacognition said:**
> Thanks, it works but now the menu has no more icons. They're all folders, is that normal?
Can you [post a screenshot](http://ubuntuforums.org/showpost.php?p=4527031&postcount=4) of your menu?

---

### Post by metacognition on 2008-09-20
I did a restart and it's all good now. Apparently after the uninstall, it was still riding on KDE 3.x

---

### Post by aysiu on 2008-09-20
By the way, the way I found the solution to this was...

I started the Kubuntu KDE 4 Remix live CD session. I typed in ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
``` and instead of actually going through with the installation, I just copied and pasted all the new packages that would be added to KDE 4 if I were to install KDE 3.*

Then I tacked on ```
sudo apt-get install kubuntu-kde4-desktop
``` just in case something got accidentally removed.

---


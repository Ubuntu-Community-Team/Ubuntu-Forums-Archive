---
title: "fresh breezy-&gt;kde3.5.1"
date: 2006-03-06
forum: Desktop Environments
---

### Post by stoeptegel on 2006-03-06
I have a strange problem. 
I updated my sources.list from kubuntu.org and tried to upgrade to kde 3.5.1.

But kubuntu-desktop got removed and lots of other packages. Kde runs fine though, only adept doesn't work anymore:

Fetsch updates> upgrade>nothing
But when i list on packages on upgrable i have 71 package able to upgrade>i select them all with crtl+a>hit upgrade>almost all have action remove

For information, when i do # apt-get upgrade i get:
```

Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De volgende pakketten zijn achtergehouden:
  akregator ark artsbuilder kaddressbook kamera kappfinder karm kate
  kaudiocreator kcontrol kcron kde-i18n-nl kdeadmin-kfile-plugins kdebase-bin
  kdebase-kio-plugins kdegraphics-kfile-plugins kdelibs kdelibs-bin
  kdelibs4-dev kdelibs4c2 kdemultimedia-kfile-plugins
  kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins
  kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdesktop kdm kfind
  kghostview khelpcenter kicker klaptopdaemon klipper kmenuedit kmilo kmix
  knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole
  kontact kooka kopete korganizer kpdf kpf kppp krdc krfb kscd kscreensaver
  ksmserver ksnapshot ksplash ksvg kuser kwalletmanager kwifimanager kwin
  libkcddb1 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0
  libktnef1
0 pakketten opgewaardeerd, 0 nieuwe pakketten geïnstalleerd, 0 verwijderen en 71 niet opgewaardeerd

```

I'am lost, this is a fresh installation so this shouldn't happen, right?

---

### Post by stoeptegel on 2006-03-06
Okey, just reinstalled and got it working. 
It looks that the standard sources.list + kde 3.5.1 source brakes the system.

Be sure tu use source-o-matic when you want kde 3.5.1 ( genius service btw, give that guy a hug! )

---


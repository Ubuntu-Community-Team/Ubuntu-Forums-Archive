---
title: "how to upgrade kde to kde 4.3.1"
date: 2009-09-04
forum: Desktop Environments
---

### Post by anyone2009 on 2009-09-04
[CENTER]Hi guys ,, 
I'm new on kde ,, i was use gnome ,,
now 
I use kubuntu 9.04 and i want to upgrae kde to kde4.3.1 can any one tell me how to do that plz ,, 

thx 4 everyone
[/CENTER]

---

### Post by Ekeluo on 2009-09-04
The instructions on [www.kubuntu.org](www.kubuntu.org) are easy enough to follow I think. Just post back if ya still need any help.

---

### Post by anyone2009 on 2009-09-04
> **Ekeluo said:**
> The instructions on [www.kubuntu.org](www.kubuntu.org) are easy enough to follow I think. Just post back if ya still need any help.
Ekeluo ,, thank you ,, but i see it before and i need for more explanation plz

---

### Post by Ekeluo on 2009-09-04
Sure thing - basically, you have to add this ```
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
```
to your software repos.

Open Kpackagekit, select Settings on the left, then click 'edit software sources'. Select the 'third party software' tab, then click the 'add...' button. Paste the text above into the box.

Then either copy this text:
```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESgMYswEEAOzc0ePR1UkVIg9dZZgl6exOQlr+pAoDIrlEmv1WX977Ciwh9GI6g2KMf3Ci
8DY2jluksPyNWlAtG9rls0NvFyqWkRnRm68Tm8jy+/X7LTfz1YIixoO6xq+8i8YfXoWg0ZaJ
0MjRm2s+jxZmcx199kLC3CL7sS0ui6ZOzXpuMn7FABEBAAG0GUxhdW5jaHBhZCBLdWJ1bnR1
IFVwZGF0ZXOIRgQQEQIABgUCSk7ndwAKCRAiHJXOgzra07LlAJsH8LkuT9HLmTIeubQbMHhf
NsS1nwCglaeK7K1qBxrS7kTIoqNPOmoDdXOItgQTAQIAIAUCSgMYswIbAwYLCQgHAwIEFQII
AwQWAgMBAh4BAheAAAoJECg2ywqKyT96080EAMrywfPZkEa42ROjm6fiJ6hlNI4umiqJ11Vv
myy7PkFFapzjpFq9dIYRkk23PavTRT9nKa97N8jG+Ef4HpLfrxjAb5q+e7Aj3ykEqNcQWXpJ
ppY0TRQDiTMgBJKz3dLgSHFvRk8Rr6FI1i8ZjnkTGJd7YfkynyhA6ACEHVDDLw+s
=VGz5
-----END PGP PUBLIC KEY BLOCK-----
```

paste in a new text file, save, then import the text file through the authentication tab of the Software Sources dialog window;

OR just run this in a terminal window:
```
gpg --keyserver keyserver.ubuntu.com --recv 2836CB0A8AC93F7A
gpg --export --armor 2836CB0A8AC93F7A | sudo apt-key add -
```
if you're comfortable with it.

Update your packages (Software updates>refresh), then apply all available updates.

P.S. I didn't do mine thru Kpackagekit so if this doesn't work, install synaptic ```
sudo apt-get install synaptic
``` then get back to me.

---

### Post by anyone2009 on 2009-09-04
thank you very much now i can do it 
thx

---

### Post by wersdaluv on 2009-09-04
Sometimes, howtos are really expert-oriented. We need to explain them in ways that are more understandable to most people.

Just tell us if you still have problems upgrading. 

Regards

---

### Post by anyone2009 on 2009-09-05
> **wersdaluv said:**
> Sometimes, howtos are really expert-oriented. We need to explain them in ways that are more understandable to most people.

Just tell us if you still have problems upgrading. 

Regards

yeah it's true ,,

---

### Post by niallabrown on 2009-09-05
Why does it say under synaptic that it can only do a partial upgrade and under Kpacagekit that it has 48 updates but 70 blocked ones?

Have I messed it up?  I dont want to tell it to go ahead untill I know if this is going to mess it up.

Thanks

---

### Post by jacksaff on 2009-09-05
In a terminal run 
sudo apt-get -s upgrade 
and paste the response. This will tell you what apt-get upgrade wants to do, but the -s flag means 'simulate' so it won't actually do anything.

---

### Post by niallabrown on 2009-09-06
> sudo apt-get -s upgrade
and paste the response.

```
The following packages have been kept back:
  akregator amarok amarok-common ark dolphin dragonplayer gwenview
  kaddressbook kamera kate kde-printer-applet kde-window-manager kde-zeroconf
  kdebase-bin kdebase-data kdebase-plasma kdebase-runtime
  kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-workspace-bin
  kdebase-workspace-data kdegraphics-strigi-plugins kdemultimedia-kio-plugins
  kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs5
  kdeplasma-addons kdm kfind khelpcenter4 kjots klipper kmag kmail kmix
  kmousetool knotes konqueror konqueror-nsplugins konsole kontact kopete
  korganizer krdc krfb ksnapshot ksysguard ksystemlog ktimetracker kuser
  kwalletmanager libkcddb4 libkdepim4 libkleo4 libkonq5 libkpgp4 libksieve4
  libmimelib4 neverball neverball-common neverball-data okular
  okular-extra-backends plasma-widget-network-manager python-kde4 python-qt4
  python-sip4 systemsettings
The following packages will be upgraded:
  kde-icons-oxygen kdebase-runtime-data-common kdebase-workspace-libs4+5
  kdelibs-bin kdelibs5 kdelibs5-data kdepimlibs-data ksysguardd
  libakonadiprivate1 libeet1 libkdecorations4 libkexiv2-7 libkipi6
  libkonq5-templates libkwineffects1 libokularcore1 libplasma3 libqedje0
  libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help
  libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql
  libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit
  libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqzion0 libsoprano4
  nexuiz nexuiz-data nexuiz-music python-qt4-dbus qt4-qtconfig soprano-daemon
  system-config-printer-kde teeworlds teeworlds-data
48 upgraded, 0 newly installed, 0 to remove and 70 not upgraded.
Inst libqt4-xmlpatterns [4.5.0-0ubuntu4.1] (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty) []
Inst libqt4-sql-sqlite [4.5.0-0ubuntu4.1] (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty) []
Inst libqt4-sql-mysql [4.5.0-0ubuntu4.1] (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty) []
Inst qt4-qtconfig [4.5.0-0ubuntu4.1] (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty) []
Inst libqt4-qt3support [4.5.0-0ubuntu4.1] (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty) []
Inst libqt4-help [4.5.0-0ubuntu4.1] (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty) []
Inst libqt4-sql [4.5.0-0ubuntu4.1] (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty) []
Inst libqt4-designer [4.5.0-0ubuntu4.1] (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty) []
Inst libqt4-core [4.5.0-0ubuntu4.1] (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty) []
Inst libqt4-script [4.5.0-0ubuntu4.1] (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty) []
Inst libqt4-dbus [4.5.0-0ubuntu4.1] (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty) []
Inst libqt4-xml [4.5.0-0ubuntu4.1] (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty) []
Inst libqt4-test [4.5.0-0ubuntu4.1] (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty) []
Inst libqt4-assistant [4.5.0-0ubuntu4.1] (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty) []
Inst libqt4-webkit [4.5.0-0ubuntu4.1] (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty) []
Inst libqt4-network [4.5.0-0ubuntu4.1] (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty) []
Inst libqt4-svg [4.5.0-0ubuntu4.1] (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty) []
Inst libqt4-opengl [4.5.0-0ubuntu4.1] (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty) []
Inst libqtgui4 [4.5.0-0ubuntu4.1] (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty) []
Inst libqtcore4 [4.5.0-0ubuntu4.1] (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Inst libsoprano4 [2.2.2+dfsg.1-1ubuntu1] (2.3.0+dfsg.1-2~ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty) []
Inst soprano-daemon [2.2.2+dfsg.1-1ubuntu1] (2.3.0+dfsg.1-2~ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Inst kdelibs-bin [4:4.2.2-0ubuntu5.1] (4:4.3.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty) []
Inst libplasma3 [4:4.2.2-0ubuntu5.1] (4:4.3.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty) []
Inst kdelibs5-data [4:4.2.2-0ubuntu5.1] (4:4.3.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty) []
Inst kdelibs5 [4:4.2.2-0ubuntu5.1] (4:4.3.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Inst kde-icons-oxygen [4:4.2.2-0ubuntu1] (4:4.3.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Inst kdebase-runtime-data-common [4:4.2.2-0ubuntu1] (4:4.3.1-0ubuntu1~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Inst kdebase-workspace-libs4+5 [4:4.2.2-0ubuntu2] (4:4.3.1-0ubuntu1~jaunty1~ppa6 Ubuntu:9.04/jaunty)
Inst kdepimlibs-data [4:4.2.2-0ubuntu1] (4:4.3.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Inst ksysguardd [4:4.2.2-0ubuntu2] (4:4.3.1-0ubuntu1~jaunty1~ppa6 Ubuntu:9.04/jaunty)
Inst libeet1 [1.1.0-1] (1.1.0+svn36234-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Inst libkdecorations4 [4:4.2.2-0ubuntu2] (4:4.3.1-0ubuntu1~jaunty1~ppa6 Ubuntu:9.04/jaunty)
Inst libkonq5-templates [4:4.2.2-0ubuntu4] (4:4.3.1-0ubuntu1~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Inst libkwineffects1 [4:4.2.2-0ubuntu2] (4:4.3.1-0ubuntu1~jaunty1~ppa6 Ubuntu:9.04/jaunty)
Inst libqzion0 [0.3.0-0ubuntu1] (0.4.0-0ubuntu4~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Inst libqedje0 [0.3.0-0ubuntu1] (0.4.0-0ubuntu4~jaunty2~ppa1 Ubuntu:9.04/jaunty)
Inst nexuiz [2.4.2-1] (2.5.1-1~getdeb1 GetDeb:9.04/jaunty-getdeb) []
Inst nexuiz-data [2.4.2-1] (2.5.1-1~getdeb1 GetDeb:9.04/jaunty-getdeb)
Inst nexuiz-music [2.4.2-1] (2.5.1-1~getdeb1 GetDeb:9.04/jaunty-getdeb)
Inst python-qt4-dbus [4.4.4-2ubuntu6] (4.5.2-0ubuntu1~jaunty2 Ubuntu:9.04/jaunty)
Inst system-config-printer-kde [4:4.2.2-0ubuntu2] (4:4.3.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Inst teeworlds [0.4.3-3] (0.5.1-1~getdeb1 GetDeb:9.04/jaunty-getdeb) []
Inst teeworlds-data [0.4.3-3] (0.5.1-1~getdeb1 GetDeb:9.04/jaunty-getdeb)
Inst libakonadiprivate1 [1.1.1-0ubuntu3] (1.2.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Inst libkexiv2-7 [4:4.2.2-0ubuntu2] (4:4.3.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Inst libkipi6 [4:4.2.2-0ubuntu2] (4:4.3.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Inst libokularcore1 [4:4.2.2-0ubuntu2] (4:4.3.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Conf libqtcore4 (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf libqt4-network (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf libqt4-xmlpatterns (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf libqt4-sql (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf libqt4-sql-sqlite (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf libqt4-sql-mysql (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf libqt4-xml (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf libqt4-dbus (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf libqt4-script (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf libqtgui4 (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf libqt4-designer (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf libqt4-qt3support (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf qt4-qtconfig (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf libqt4-help (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf libqt4-test (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf libqt4-core (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf libqt4-assistant (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf libqt4-webkit (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf libqt4-svg (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf libqt4-opengl (4.5.2-0ubuntu2~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf soprano-daemon (2.3.0+dfsg.1-2~ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Conf libsoprano4 (2.3.0+dfsg.1-2~ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Conf kdelibs5-data (4:4.3.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Conf kdelibs5 (4:4.3.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Conf kdelibs-bin (4:4.3.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Conf libplasma3 (4:4.3.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Conf kde-icons-oxygen (4:4.3.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Conf kdebase-runtime-data-common (4:4.3.1-0ubuntu1~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf kdebase-workspace-libs4+5 (4:4.3.1-0ubuntu1~jaunty1~ppa6 Ubuntu:9.04/jaunty)
Conf kdepimlibs-data (4:4.3.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Conf ksysguardd (4:4.3.1-0ubuntu1~jaunty1~ppa6 Ubuntu:9.04/jaunty)
Conf libeet1 (1.1.0+svn36234-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Conf libkdecorations4 (4:4.3.1-0ubuntu1~jaunty1~ppa6 Ubuntu:9.04/jaunty)
Conf libkonq5-templates (4:4.3.1-0ubuntu1~jaunty1~ppa2 Ubuntu:9.04/jaunty)
Conf libkwineffects1 (4:4.3.1-0ubuntu1~jaunty1~ppa6 Ubuntu:9.04/jaunty)
Conf libqzion0 (0.4.0-0ubuntu4~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Conf libqedje0 (0.4.0-0ubuntu4~jaunty2~ppa1 Ubuntu:9.04/jaunty)
Conf nexuiz-data (2.5.1-1~getdeb1 GetDeb:9.04/jaunty-getdeb)
Conf nexuiz (2.5.1-1~getdeb1 GetDeb:9.04/jaunty-getdeb)
Conf nexuiz-music (2.5.1-1~getdeb1 GetDeb:9.04/jaunty-getdeb)
Conf python-qt4-dbus (4.5.2-0ubuntu1~jaunty2 Ubuntu:9.04/jaunty)
Conf system-config-printer-kde (4:4.3.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Conf teeworlds-data (0.5.1-1~getdeb1 GetDeb:9.04/jaunty-getdeb)
Conf teeworlds (0.5.1-1~getdeb1 GetDeb:9.04/jaunty-getdeb)
Conf libakonadiprivate1 (1.2.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Conf libkexiv2-7 (4:4.3.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Conf libkipi6 (4:4.3.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)
Conf libokularcore1 (4:4.3.1-0ubuntu1~jaunty1~ppa1 Ubuntu:9.04/jaunty)

```

Thanks

---

### Post by binbash on 2009-09-06
[http://www.ubuntu-inside.me/2009/09/howto-install-kde-431-in-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/09/howto-install-kde-431-in-ubuntu-jaunty.html)

---

### Post by niallabrown on 2009-09-06
Hey Binbash,  I'm not sure what your pointing out.  I am a fairly basic user.  I followed the steps earlier in this thread and it now says it has blocked 70 updates.  I have followed Jacksaff's instructions but I don't know how to read into what the terminal output is telling me.

---

### Post by Ekeluo on 2009-09-07
You probably have dependencies that cannot be satisfied, i.e. a program you installed depends on special version of a package that is not compatible with the upgrade version. Post you /etc/apt/sources.list so we can see.

Alternatively, go to upgradeable packages in synaptic, select all of the updates, click apply and report what it complains about here.

---

### Post by niallabrown on 2009-09-07
> Post you /etc/apt/sources.list so we can see.


```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ jaunty main restricted universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main

```

> go to upgradeable packages in synaptic, select all of the updates, click apply and report what it complains about here. 

It wont let me select the check boxes to upgrade.  I can apply a 'partial upgrade.' Should I try that?

---

### Post by niallabrown on 2009-09-10
Is there more information I can give?

---

### Post by Ms_Angel_D on 2009-09-10
I had this same problem, I just used synaptic and applied all the updates included the 70 that kpackagekit blocked and it worked fine.

From what I found through google there seems to be some errors with kpackagekit and most recommend using synaptic or command line for kubutnu upgrades.

---

### Post by niallabrown on 2009-09-10
Thanks Ill give it a try.

---

### Post by Ekeluo on 2009-10-08
Hey naillabrown, been away from my email for some time, a bit distracted. Might be late , but how's your update coming?

---

### Post by niallabrown on 2009-10-08
Hey Ekeluo,  I'm afraid that install got really messed up and even the regular updates wouldn't install.  Unfortunately due to some other issues in addition to those ones I decided to do a fresh install and will try the latest KDE when the next Ubuntu is released.

Thanks to all those who tried to help.

Niall

---

### Post by Ekeluo on 2009-10-08
Sorry to hear that, I'm sure you'll like Karmic when it's released. L8r then.

---


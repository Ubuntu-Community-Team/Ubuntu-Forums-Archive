---
title: "Updates, notify and update manager"
date: 2009-06-01
forum: General Help
---

### Post by everytimeref on 2009-06-01
I don't seem to get very many Jaunty updates.
My software sources look okay:

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe main #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe main #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe


# deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) jaunty cairo-dock # disabled on upgrade to jaunty
# deb [http://ppa.launchpad.net/andrewsomething/ubuntu](http://ppa.launchpad.net/andrewsomething/ubuntu) intrepid main
# deb-src [http://ppa.launchpad.net/andrewsomething/ubuntu](http://ppa.launchpad.net/andrewsomething/ubuntu) intrepid main
# deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) jaunty main # disabled on upgrade to jaunty
# deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) jaunty main # disabled on upgrade to jaunty
deb-src [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) jaunty main # disabled on upgrade to jaunty
# deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) jaunty cairo-dock #cairo-dock jaunty

I just don't seem to get very many updates (e.g. none for at least a week). I enable Jaunty proposed just to see if everything is all working then it shows my 79 possible udpates...

---

### Post by loneowais on 2009-06-01
I don't get much either. Anyway try mine
> 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free #opera
deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) jaunty main #blueman
deb [http://ppa.launchpad.net/firerabbit/ppa/ubuntu](http://ppa.launchpad.net/firerabbit/ppa/ubuntu) jaunty main #synapse
deb [http://ppa.launchpad.net/get-you-development/ppa/ubuntu](http://ppa.launchpad.net/get-you-development/ppa/ubuntu) jaunty main #Get-You
deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) jaunty main #gnome-globalmenu
deb [http://ppa.launchpad.net/gtg/ppa/ubuntu](http://ppa.launchpad.net/gtg/ppa/ubuntu) jaunty main #gtg
deb [http://ppa.launchpad.net/lidaobing/ubuntu](http://ppa.launchpad.net/lidaobing/ubuntu) jaunty main #chmsee
deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) jaunty main #shutter
deb [http://ppa.launchpad.net/specto/ppa/ubuntu](http://ppa.launchpad.net/specto/ppa/ubuntu) jaunty main #specto
deb [http://ppa.launchpad.net/transmissionbt/ubuntu](http://ppa.launchpad.net/transmissionbt/ubuntu) jaunty main #transmission-gtk
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) jaunty main #ubuntu-tweak
deb [http://ppa.launchpad.net/vperetokin/gnote/ubuntu](http://ppa.launchpad.net/vperetokin/gnote/ubuntu) jaunty main #gnote
deb [http://www.ompolicy.altervista.org/ubuntu/](http://www.ompolicy.altervista.org/ubuntu/) jaunty/ #swiftweasel
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://download.tuxfamily.org/upure64/](http://download.tuxfamily.org/upure64/) jaunty-upure64 main experimental
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free
deb [http://etree.org/debian](http://etree.org/debian) unstable contrib
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) jaunty/
deb [http://linux.getdropbox.com/ubuntu](http://linux.getdropbox.com/ubuntu) jaunty main
deb-src [http://linux.getdropbox.com/ubuntu](http://linux.getdropbox.com/ubuntu) jaunty main
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty non-free free
deb [http://ppa.launchpad.net/anyremote/ppa/ubuntu](http://ppa.launchpad.net/anyremote/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/conduit/ppa/ubuntu](http://ppa.launchpad.net/conduit/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/corenominal/ubuntu](http://ppa.launchpad.net/corenominal/ubuntu) hardy main
deb [http://ppa.launchpad.net/dell-team/ppa/ubuntu](http://ppa.launchpad.net/dell-team/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/dell-team/ppa/ubuntu](http://ppa.launchpad.net/dell-team/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) jaunty main universe
deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/do-testers/ppa/ubuntu](http://ppa.launchpad.net/do-testers/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/elisa-developers/ppa/ubuntu](http://ppa.launchpad.net/elisa-developers/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/gandalfn/ppa/ubuntu](http://ppa.launchpad.net/gandalfn/ppa/ubuntu) intrepid main
deb [http://ppa.launchpad.net/gilir/ppa/ubuntu](http://ppa.launchpad.net/gilir/ppa/ubuntu) jaunty main universe
deb [http://ppa.launchpad.net/glasen/ppa/ubuntu](http://ppa.launchpad.net/glasen/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/gm-notify-maintainers/ppa/ubuntu](http://ppa.launchpad.net/gm-notify-maintainers/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/gm-notify-maintainers/ppa/ubuntu](http://ppa.launchpad.net/gm-notify-maintainers/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/gspreemann/ppa/ubuntu](http://ppa.launchpad.net/gspreemann/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/intuitivenipple/ppa/ubuntu](http://ppa.launchpad.net/intuitivenipple/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/kow/ppa/ubuntu](http://ppa.launchpad.net/kow/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/kow/ppa/ubuntu](http://ppa.launchpad.net/kow/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/mdeslaur/ubuntu/](http://ppa.launchpad.net/mdeslaur/ubuntu/) jaunty main
deb [http://ppa.launchpad.net/mvo/ppa/ubuntu](http://ppa.launchpad.net/mvo/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/teknoraver/ppa/ubuntu](http://ppa.launchpad.net/teknoraver/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/wader/ppa/ubuntu](http://ppa.launchpad.net/wader/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/wader/ppa/ubuntu](http://ppa.launchpad.net/wader/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/wine-doors-dev-team/ppa/ubuntu](http://ppa.launchpad.net/wine-doors-dev-team/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty main
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) jaunty cairo-dock
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main
deb [http://winff.org/ubuntu](http://winff.org/ubuntu) jaunty universe
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse

---

### Post by Soul-Sing on 2009-06-01
This is not exactly a default sources.list......i would not recommend it to copy-paste it....(sorry)

---

### Post by cariboo on 2009-06-01
Updates are done differently in Jaunty, when there are security updates, you are notified right away, regular updates only show up once a week. There is no longer a notification icon, the update manager opens up instead.

---

### Post by everytimeref on 2009-06-02
> **cariboo907 said:**
> Updates are done differently in Jaunty, when there are security updates, you are notified right away, regular updates only show up once a week. There is no longer a notification icon, the update manager opens up instead.

I did a bit of fiddling when Jaunty was first installed because I didn't like the notify thing for updates, so I do get a Notification icon.
But if I run update manager manually, should I see some updates?

I guess my question is ( I do actually have one!) are there many updates for Jaunty so far?

Is there a test I could do to identify a recent security update and find out if I have it?

Thanks to all of you for responding it's very much appreciated.

---


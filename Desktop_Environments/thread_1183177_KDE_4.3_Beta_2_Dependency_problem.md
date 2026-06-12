---
title: "KDE 4.3 Beta 2 Dependency problem"
date: 2009-06-09
forum: Desktop Environments
---

### Post by Naatan on 2009-06-09
Hi, I installed KDE 4.3 Beta 2 yesterday, works extremely smooth and without any bugs so far. Only problem I have now is that some (very few) packages are complaining that libqt4-gui is the wrong version. When I try to update it I get the following error:

"The following packages have unmet dependencies:
  libqt4-gui: Depends: libqtgui4 (= 4.5.0-0ubuntu4.1) but 4.5.1-1ubuntu1~jaunty1~ppa1 is to be installed
              Depends: libqt4-svg (= 4.5.0-0ubuntu4.1) but 4.5.1-1ubuntu1~jaunty1~ppa1 is to be installed
              Depends: libqt4-opengl (= 4.5.0-0ubuntu4.1) but 4.5.1-1ubuntu1~jaunty1~ppa1 is to be installed
              Depends: libqt4-designer (= 4.5.0-0ubuntu4.1) but 4.5.1-1ubuntu1~jaunty1~ppa1 is to be installed
              Depends: libqt4-assistant (= 4.5.0-0ubuntu4.1) but 4.5.1-1ubuntu1~jaunty1~ppa1 is to be installed"

Looks to me like libqt4-gui is the same thing as libqtgui4. So prolly a naming issue?

Anyone know a decent workaround?

---

### Post by Freezewarp on 2009-06-09
> **Naatan said:**
> Hi, I installed KDE 4.3 Beta 2 yesterday, works extremely smooth and without any bugs so far. Only problem I have now is that some (very few) packages are complaining that libqt4-gui is the wrong version. When I try to update it I get the following error:

"The following packages have unmet dependencies:
  libqt4-gui: Depends: libqtgui4 (= 4.5.0-0ubuntu4.1) but 4.5.1-1ubuntu1~jaunty1~ppa1 is to be installed
              Depends: libqt4-svg (= 4.5.0-0ubuntu4.1) but 4.5.1-1ubuntu1~jaunty1~ppa1 is to be installed
              Depends: libqt4-opengl (= 4.5.0-0ubuntu4.1) but 4.5.1-1ubuntu1~jaunty1~ppa1 is to be installed
              Depends: libqt4-designer (= 4.5.0-0ubuntu4.1) but 4.5.1-1ubuntu1~jaunty1~ppa1 is to be installed
              Depends: libqt4-assistant (= 4.5.0-0ubuntu4.1) but 4.5.1-1ubuntu1~jaunty1~ppa1 is to be installed"

Looks to me like libqt4-gui is the same thing as libqtgui4. So prolly a naming issue?

Anyone know a decent workaround?

Try the following commands:
sudo dpkg -r libqt4-gui
sudo apt-get update
sudo apt-get upgrade


This should remove libqt4, then allowing apt to continue. However, if not, post the output. Also, this may not necessarily work if the repository you are downloading KDE 4.3 Beta 2 hasn't yet been updated properly.

---

### Post by Naatan on 2009-06-09
Thanks for your reply Freezewarp.

I got it wrong myself, libqt4-gui is not installed atm, it was required by a different app. When I try to install libqt4-gui I get the error mentioned in my first post.

---

### Post by shadeslayer on 2009-06-14
Im having some problems too.I cant start KDE 4.3 beta 2 as kbuildsycoca4 crashes.Any help would be appreciated.
Also see :
shadeslayer@shadeslayer:~$ sudo apt-get install kdebase-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting kdebase-data-kde4 for regex 'kdebase-*'
Note, selecting kdebase-runtime-data-common for regex 'kdebase-*'
Note, selecting kde-nightly-kdebase-dbg for regex 'kdebase-*'
Note, selecting kdebase-dbg-kde4 for regex 'kdebase-*'
Note, selecting kdebase for regex 'kdebase-*'
Note, selecting kdebase-bin-kde3 for regex 'kdebase-*'
Note, selecting kdebase-bin-kde4 for regex 'kdebase-*'
Note, selecting kdebase-kde4 for regex 'kdebase-*'
Note, selecting kdebase-workspace-bin for regex 'kdebase-*'
Note, selecting kdebase-workspace-dbg for regex 'kdebase-*'
Note, selecting kdebase-workspace-dev for regex 'kdebase-*'
Note, selecting kdebase-i18n for regex 'kdebase-*'
Note, selecting amarok-nightly-kdebase for regex 'kdebase-*'
Note, selecting kde-nightly-kdebase for regex 'kdebase-*'
Note, selecting kdebase-bin for regex 'kdebase-*'
Note, selecting kdebase-dbg for regex 'kdebase-*'
Note, selecting kdebase-dev for regex 'kdebase-*'
Note, selecting kdebase-workspace-data for regex 'kdebase-*'
Note, selecting kdebase-workspace-libs4+5 for regex 'kdebase-*'
Note, selecting kdebase-kio-plugins for regex 'kdebase-*'
Note, selecting kdebase-workspace-wallpapers for regex 'kdebase-*'
Note, selecting kdebase-runtime for regex 'kdebase-*'
Note, selecting kdebase-data for regex 'kdebase-*'
Note, selecting kdebase-dev-kde4 for regex 'kdebase-*'
Note, selecting kdebase-runtime-data for regex 'kdebase-*'
Note, selecting kdebase-plasma for regex 'kdebase-*'
Note, selecting kdebase-runtime-bin-kde4 for regex 'kdebase-*'
Note, selecting kdebase-runtime-dbg for regex 'kdebase-*'
Note, selecting amarok-nightly-kdebase-dbg for regex 'kdebase-*'
Note, selecting kdebase-workspace for regex 'kdebase-*'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdebase-dev: Depends: dolphin (= 4:4.2.4-0ubuntu1~jaunty1~ppa2) but 4:4.2.90-0ubuntu1~jaunty1~ppa1 is to be installed
               Depends: konqueror (= 4:4.2.4-0ubuntu1~jaunty1~ppa2) but 4:4.2.90-0ubuntu1~jaunty1~ppa1 is to be installed
               Depends: libkonq5-dev (= 4:4.2.4-0ubuntu1~jaunty1~ppa2) but 4:4.2.90-0ubuntu1~jaunty1~ppa1 is to be installed
E: Broken packages

---


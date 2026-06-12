---
title: "KDE apps crashing"
date: 2010-11-28
forum: Desktop Environments
---

### Post by nixIT on 2010-11-28
Been a gnome user for years, but decided to try the latest Kubuntu(10.10), looks elegant. However, alot of the KDE apps crash when I went to run them:

-ktorrent crashes when adding a torrent
-dragonplayer crashes while trying to play a ASF file (I have restricted extras installed). VLC plays the file fine.

I also tested another KDE distro (openSUSE), to check and see if it was distro specific, and it's not, same apps in both distros constantly crash when trying to run.

would like to run native installed apps, but they crash.

Any ideas?

I installed Kubuntu from live CD, updated installed nvidia drivers from restricted hardware.

---

### Post by inobe on 2010-11-28
live cd installs are known for these affects, you must take your current install and build/ upgrade packages.


live cd installs only offer kde base packages, quite frankly you will need to build from there.

the base system is always buggy as hell, the same applies to any distribution.


once you've upgraded your package and add kde extras the bugs will disappear for the most part.

if you need help building onto and upgrading to stable releases' let us know and we will try to help.

---

### Post by nixIT on 2010-11-28
so the apt-get update did not do the trick.  Other than that, I'm lost.  Can you help me out, as I am not sure what you mean by build and upgrade.

---

### Post by inobe on 2010-11-28
the best way to upgrade and start building is adding the repository.

[http://www.kubuntu.org/news/kde-sc-4.5.3](http://www.kubuntu.org/news/kde-sc-4.5.3)

here are some important things you should do first.

----------------------------------

backup your data.

understand what you are doing and how to do it before hand.

be sure to have something to fall back on encase something goes wrong, as you know' anything can go wrong.

----------------------------------

here is a site i would follow on exactly how to upgrade 

[http://motersho.com/blog/index.php/2010/11/05/how-to-update-kubuntu-10-10-to-kde-4-5-3/](http://motersho.com/blog/index.php/2010/11/05/how-to-update-kubuntu-10-10-to-kde-4-5-3/)

after the upgrade starts your basically allowing all of kde to be installed, so basically a few hundred extra mb/s in space will be required.

in the upgrade there are something like 16,000 bug fixes, so many things are fixed however this doesn't mean it will be completely bug less.

---

### Post by inobe on 2010-11-28
a side note encase it happens, if you restart after the upgrade and notice missing desktop parts or if things don't look rite, don't try to fix anything, open kpackagekit and click check for updates, if you get more updates install them, restart once again, that should help.

---


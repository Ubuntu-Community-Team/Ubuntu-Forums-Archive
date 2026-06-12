---
title: "KSudoku dependency trouble"
date: 2005-10-17
forum: Gaming &amp; Leisure
---

### Post by shinygerbil on 2005-10-17
I've been trying to install ksudoku from [http://ksudoku.sourceforge.net/](http://ksudoku.sourceforge.net/) and having serious problems getting it to work. If I download the .deb version, it installs, comes up with an error message claiming kdelibs4 and libqt3c102-mt are required, but still allows me to play the game. (I have the breezy versions of both these; kdelibs4c and libqt3c-mt, I believe)

If I download the source and try and compile it, it claims I need a newer version of Qt (message: checking for Qt... configure: error: Qt (>= Qt 3.2) (headers and libraries) not found.) Then it won't let me make the program. Now it's ok for me to stick with the debian version, but it appears to have many problems running the 3D puzzles (i.e. displays glithec graphics for about a second then crashes with SIGSSEV), and besides, every time I try to do anything else with any packages, I can't without having to uninstall ksudoku. And an apt-get -f install doesn't help.

Any ideas on how I can get ksudoku and my system to live together in harmony? There was an official Kubuntu version out a short while ago, but it doesn't work under breezy. Any help would be most appreciated!

Thanks in advance

Steve

---

### Post by Perfect Storm on 2005-10-18
Did you install the -dev packages of the files it says its missing?

---

### Post by No6 on 2005-10-19
Try following my post in this thread, it works perfectly...

[http://ubuntuforums.org/showthread.php?t=76920](http://ubuntuforums.org/showthread.php?t=76920)

---

### Post by shinygerbil on 2005-10-19
It does indeed work perfectly!

Thanks

Steve

---


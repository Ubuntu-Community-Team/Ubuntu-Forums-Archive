---
title: "Unable to change mouse cursor theme and size with Compiz enabled"
date: 2011-05-23
forum: Desktop Environments
---

### Post by Nerotriple6 on 2011-05-23
[I previously filed a bug report at Launchpad.]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/786325") Unaware that Compiz was the culprit.

I disabled Compiz yesterday and this bug just vanished. So I set Compiz as the affected package and Launchpad webiste now says that:
> 'Compiz' is a binary package. This bug has been assigned to its source package 'compiz' instead.
And:
> The bug supervisor for compiz (Ubuntu) has been subscribed to this bug
While the Compiz wiki says that I must make a forum thread and discuss it with others. So here it is. Anyway I wonder, have I done enough?

> Ubuntu 11.04 Natty Narwhale

When attempting to change mouse cursor size and/or theme in Natty the theme and/or size do not change. A workaround for this is entering the following line into a Terminal but the user is still UNABLE to change the size of the cursor.
sudo update-alternatives --config x-cursor-theme

ProblemType: Bug
DistroRelease: Ubuntu 11.04
Package: gnome-control-center 1:2.32.1-0ubuntu15
ProcVersionSignature: Ubuntu 2.6.38-9.43-generic 2.6.38.4
Uname: Linux 2.6.38-9-generic i686
NonfreeKernelModules: fglrx
Architecture: i386
Date: Sat May 21 23:12:18 2011
ExecutablePath: /usr/bin/gnome-appearance-properties
InstallationMedia: Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
ProcEnviron:
 LANGUAGE=nb_NO:en
 LANG=nb_NO.UTF-8
 SHELL=/bin/bash
SourcePackage: gnome-control-center
UpgradeStatus: No upgrade log present (probably fresh install)

> UPDATE:

When cursor is hovering some windows such as Gnome Terminal and Google-Chrome the cursor appears with the correct size as set in Appearance Properties, but over the desktop it is larger than decided in Appearance Properties.

Some areas in Google-Chrome such as this text input field will have the desired cursor size, links in Chrome will also have the desired size, also areas with text will have the desired size but not areas that are empty which now appears to be the only area where the mouse pointer appears with the wrong size in Chrome.

In Ubuntu Calculator the mouse cursor appears as it should when hovering over the display but appears in wrong size when hovering the button area.

> This is a bug in Compiz. Compiz 9 has no option to change mouse themes. I disabled Compiz to play the game Football Manager and the mouse cursor theme and size was correct.

---


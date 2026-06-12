---
title: "updating to kde to 4.5 beta"
date: 2010-06-11
forum: Desktop Environments
---

### Post by test006 on 2010-06-11
Hi,
I have kubuntu running. I have tried updating to KDE 4.5 Beta using the KPackageKit and i now get 118 blocked packages which i cannot install.
I used the CLI and typed apt-get update and apt-get upgrade and this did  not fix the problem.
Is there anyway to find out why those packages are blocked?

Thanks

---

### Post by Zorael on 2010-06-11
Try aptitude and do a full-upgrade. See what solutions it offers. It may want to remove a library or two to meet dependencies (like libqt4-assistant according to [this thread](http://ubuntuforums.org/showthread.php?t=1506275)).
```
$ sudo aptitude full-upgrade
```

---

### Post by PGHammer on 2010-06-12
> **Zorael said:**
> Try aptitude and do a full-upgrade. See what solutions it offers. It may want to remove a library or two to meet dependencies (like libqt4-assistant according to [this thread](http://ubuntuforums.org/showthread.php?t=1506275)).
```
$ sudo aptitude full-upgrade
```

That usually does the trick (especially since the block comes from stuff like libqt4-assistant that hates being replaced with libqt5-assistant, which the 4.5 betas use).

A performance warning - Kwin in the 4.5 betas (both 1 and 2) is not only dog-slow, but extremely crash-happy.  I have found that compiz (if you have 3D acceleration) is not only much more stable than Kwin, but faster besides; further, you don't lose the plasma workspace, which is not Kwin-dependent.  I am running beta 2 of KDE 4.5, but use compiz for window management, and emerald for window decoration.  (For graphics drivers, I'm using the Linux Catalysts, as neither radeonhd nor base radeon xorg servers support 3D on HD5450.)

The combo of compiz+emerald is noticeably quicker than compiz+straight KDE window decorator, and both quicker and less crash-happy than Kwin.

---

### Post by Zorael on 2010-06-13
I can't say I experience any notable performance degradations in KWin in 4.5. I run on Intel graphics though, on my netbook. I've had a plasma crash or two (as well as the usual krunner crashes), but no KWin crash yet.

---


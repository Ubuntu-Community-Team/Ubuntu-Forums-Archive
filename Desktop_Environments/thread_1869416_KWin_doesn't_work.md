---
title: "KWin doesn't work"
date: 2011-10-25
forum: Desktop Environments
---

### Post by ascent1729 on 2011-10-25
I installed Ubuntu 10.10 Oneiric and Unity works without any issues. After this, I tried to install KDE by installing first kde-full and then kubuntu-desktop (I kept LightDM as the login manager though). However, KDE doesn't start up correctly --- on the loading screen for KDE, the first four icons come in, but the fifth one is frozen after partially fading in. Switching to another virtual terminal and switching back results in the KDE screen becoming completely black, although the mouse pointer is still available.

A workaround for this issue is to change KDE's window manager. To do that, I went to another terminal and killed both kwin and plasma-desktop. At that point, on the KDE screen, the Alt+F2 launcher can be seen on the screen, and I can launch plasma-desktop, although since I don't have a window manager, all the windows are stuck in the top-left corner. To really fix the problem, I open systemsettings from the Alt+F2 launcher and go to Default Applications | Window Manager and switch the window manager from KWin to Metacity. At this point, Metacity is able to capture all the windows and give them title bars and such, so the desktop becomes usable at this point. On the other hand, I lose KWin's shortcuts, such as Alt+F2, so I'd really like to be able to run KWin.

I'm on x86_64 and running the NVidia proprietary driver, version 280.13, package nvidia-current-updates, and my graphics card is, according to lspci,
```

01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)

```I can't find any immediately relevant bug reports from the bug tracker, and I want to submit this as a bug, but I don't know if anybody has encountered this or knows a workaround.

---


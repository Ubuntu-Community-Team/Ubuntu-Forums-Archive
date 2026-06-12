---
title: "Display-settings-Notebook-tv"
date: 2015-04-11
forum: Desktop Environments
---

### Post by Freiklite on 2015-04-11
Hi,
My tv screen shows a frame different of the notebook one - (vga output).
I installed kscreen and kde-workspace-randr packages but I didn't have got the display settings GUI.
I ran KRandRTray and it stopped.
In terminal:```
$ krandrtray
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.


```
Can you help me?
Thanks.

Pieces of information:
Linux freiklite-SATELLITE-C70D-B 3.16.0-34-generic #45~14.04.1-Ubuntu SMP Tue Mar 24 11:14:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

[HTML]$ dpkg --status kscreen
Package: kscreen
Status: install ok installed
Priority: extra
Section: kde
Installed-Size: 876
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Architecture: amd64
Version: 1.0.2.1-0ubuntu1
Depends: kde-runtime, libc6 (>= 2.14), libkdecore5 (>= 4:4.5.85), libkdeui5 (>= 4:4.3.4), libkscreen1 (>= 1.0.2), libplasma3 (>= 4:4.5.90), libqjson0 (>= 0.8.1), libqt4-dbus (>= 4:4.5.3), libqt4-declarative (>= 4:4.7.0~rc1), libqtcore4 (>= 4:4.7.0~beta2), libqtgui4 (>= 4:4.8.0), libstdc++6 (>= 4.1.1)
Description: KDE monitor hotplug and screen handling
 The KDE multiple monitor support is trying be as smart as possible
 adapting the behavior of it to each use case making the configuration
 of monitors as simple as plugging them to your computer.
 .
 This package contains the modules and plugins for monitor hotplut and
 automatic screen handling.
Homepage: https://projects.kde.org/projects/playground/base/kscreen
Original-Maintainer: Achim Bohnet <allee@kubuntu.org>

[/HTML]
[HTML]$ dpkg --status kde-workspace-randr
Package: kde-workspace-randr
Status: install ok installed
Priority: optional
Section: kde
Installed-Size: 826
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Architecture: amd64
Source: kde-workspace
Version: 4:4.11.11-0ubuntu0.2
Depends: kde-runtime, libc6 (>= 2.14), libkcmutils4 (>= 4:4.4.95), libkdecore5 (>= 4:4.4.0), libkdeui5 (>= 4:4.4.0), libqt4-dbus (>= 4:4.6.1), libqtcore4 (>= 4:4.7.0~beta1), libqtgui4 (>= 4:4.5.3), libsolid4 (>= 4:4.3.4), libstdc++6 (>= 4.1.1), libx11-6, libxrandr2 (>= 2:1.2.99.3)
Breaks: kde-workspace-bin (<< 4:4.10.1b-0ubuntu2)
Conflicts: kde-workspace-bin (<< 4:4.10.1b-0ubuntu2)
Description: randr tools from kde-workspace
 Screen resize and rotate tools from KDE Workspace.
Homepage: http://www.kde.org/
Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org[/HTML]

---


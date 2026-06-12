---
title: "Qt / KDE applications constantly crashing"
date: 2005-02-27
forum: Desktop Environments
---

### Post by SickBoy on 2005-02-27
As I close any qt/kde application: konsole, kate, kwrite.... it gives a SIGSEV and dies opening KDE error manager. If I start from console it doesn't show any strange message excepting usual kiconloader warning. It's also impossible to create a backtrace. 

I tried dpkg-reconfigure kde, kde-base kde-libs, libqt3-mt ... but no luck

I'm totally clueless about this.

Any ideas?

---

### Post by SickBoy on 2005-02-27
[QUOTE=SickBoy]As I close any qt/kde application: konsole, kate, kwrite.... it gives a SIGSEV and dies opening KDE error manager. If I start from console it doesn't show any strange message excepting usual kiconloader warning. It's also impossible to create a backtrace. 

I tried dpkg-reconfigure kde, kde-base kde-libs, libqt3-mt ... but no luck

I'm totally clueless about this.

Any ideas?[/QUOTE]
 Seems there is an error with "nv" glx. Installed and changed driver to "nvidia" and problem is solved.

Extrange.....

---


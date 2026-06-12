---
title: "Problems with KDE 4 &gt; KDE 3 downgrade"
date: 2008-03-21
forum: Desktop Environments
---

### Post by Bosonator on 2008-03-21
Heya,

_The Problem:_ My desktop background has been reset to the default, and I can no longer change it using "Desktop - System Settings". Plus, right-clicking on the desktop no longer gives me an options menu (although I *can* use right-click on window borders to get window options).

_The Backstory:_ I recently installed KDE 4 alongside my KDE 3 desktop environment just to try it out. I had enough problems with it that I decided to remove it, and did so with 
> sudo apt-get remove kde4-core
That seemed to get rid of most packages, but there were some kde-4 applications left over (like the new Konqueror, for example), and in removing some of those, aptitude reported that I had broken kdm. I fixed that by accepting one of the downgrade options that aptitude suggested, but now I have the problems I mentioned above. Thanks for any help you can offer!

---

### Post by Bosonator on 2008-03-21
Never mind: I just realized that konqueror had been accidentally uninstalled. I just had to first reinstall konqueror, then figure out how to use aptitude to resolve dependencies. Apparently, I had to downgrade some apps to make things work.

---


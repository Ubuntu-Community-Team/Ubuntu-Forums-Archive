---
title: "Kicker won't unhide"
date: 2008-06-20
forum: Desktop Environments
---

### Post by jkugler on 2008-06-20
Have an odd one here.

As of yesterday, kicker (the task bar) has seemed to take a disliking to showing itself.  I have it set to hide, and once it hides, it will not show up.  If I kill it, and run it again, it shows itself, but it won't show when I put the cursor at the bottom of the screen.  I managed to pull up the config (on one of the kill/run cycles) and selected the option to show when I put my cursors in a certain corner of the screen.

But putting my cursor on the bottom of the screen no longer has the proper effect of bringing up kicker.

I found this: [http://ubuntuforums.org/archive/index.php/t-212648.html](http://ubuntuforums.org/archive/index.php/t-212648.html) but configuring to always show, then configuring to hide again does not solve the problem for me.

I also found this bug: [http://bugs.kde.org/show_bug.cgi?id=127466](http://bugs.kde.org/show_bug.cgi?id=127466)

But in kickerrc, XineramaScreen=0, so it's not the XineramaScreen set to -1 bug like in the above KDE bug report.

Has anyone seen this before?

Thanks!

---


---
title: "Kickoff in KDE freezes plasma-desktop"
date: 2013-07-08
forum: Desktop Environments
---

### Post by Stonecold1995 on 2013-07-08
I had just rebooted my laptop after 70 days of uptime, so I'm not sure if it's the large amount of updates to KDE that were installed without rebooting or what, but anyways, when I boot up my computer takes about a MINUTE before plasma-desktop is responsive.  When it finally comes on, the bottom panel works like it should, however when I click Kickoff, plasma-desktop (so wallpaper, the bottom panel, Kickoff menu itself) freezes for about 50 seconds before the menu opens.  When it opens, it is normal and responsive as ever, but when I click somewhere else (causing the Kickoff menu to leave), plasma-desktop freezes for about 50 seconds again...

Everything else seems responsive, but what could this be?

EDIT: Apparently this is caused because my scripts in ~/.kde/Autostart are being opened with Kate, which somehow locks up plasma-desktop when it starts at the same time.  The thread for that is at [http://ubuntuforums.org/showthread.php?t=2160725&p=12722247](http://ubuntuforums.org/showthread.php?t=2160725&p=12722247).

---


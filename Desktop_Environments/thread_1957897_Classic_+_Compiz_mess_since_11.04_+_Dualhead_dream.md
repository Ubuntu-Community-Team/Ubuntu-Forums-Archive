---
title: "Classic + Compiz mess since 11.04 + Dualhead dreaming"
date: 2012-04-13
forum: Desktop Environments
---

### Post by sosostris on 2012-04-13
Hi,

**"solved"**

By downgrading to compiz 0.9.4 again. Following these guidelines:
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)
[http://ubuntuforums.org/showthread.php?t=1817677](http://ubuntuforums.org/showthread.php?t=1817677)



since 11.04 was released I have a lot of major issues with my compiz desktop. After lots of googling around and tampering I managed to fix my classic gnome2 environment in 11.04 with compiz + emerald and dual head configuration to run flawless. 
Back then, considering the full rewrite of compiz, I expected the problems to be solved in time and accepted to live with custom ppas and old versions.

Yesterday night some unnamed daemon ;) tempted me to upgrade to 11.10. After all 1 year has passed and I thought maybe some problems are solved by now. It seems I was wrong, it even seems things got worse. Here are the issues I have:

Since 11.04
 - Random compiz crashes (e.g. segfault when activating cube)
 - Focus jumps to 2nd screen now and then
 - Need to start compiz manually in startup script.

Since 11.10
 - No gnome panel (I wouldn't miss it, I just don't understand where it's gone)
 - Cannot focus/select files on desktop (Probably related to missing gnome-panel and new lightweight nautilus integration)
 - Last active window often jumps to active desktop (e.g. when selecting a desktop from expo view, firefox always appears on the selected desktop)
 - No 2nd screen compiz decoration
 - No 2nd screen wallpaper


From what I can tell, these problems are well known, i.e. nobody gives a damn about the classic desktop being usable.

What I could fix so far:
 - Better stability by cautiously selecting compiz plugins (e.g.: No cube)
 - Better stability by using nilarimogard-webupd8 ppa and ubuntu-desktop-ppa
 - Less focus troubles when deactivating nautilus desktop handling with gnome-tweak-tool. But no I got no shortcuts on my desktop of course :(

Thus, at least no more complete compiz crashes seem to appear.

The best solution for me would be to downgrade compiz to 0.9.4 used in natty, but I did not succeed with the following command:
```
sudo apt-get install compiz=1:0.9.4+bzr20110606-0ubuntu1~natty2 compiz-core=1:0.9.4+bzr20110606-0ubuntu1~natty2 compiz-gnome=1:0.9.4+bzr20110606-0ubuntu1~natty2 compiz-plugins=1:0.9.4+bzr20110606-0ubuntu1~natty2 compiz-plugins-main=0.9.4+bzr20110527-0ubuntu1~natty1 libdecoration0=1:0.9.4+bzr20110606-0ubuntu1~natty2 libcompizconfig0=0.9.4-0ubuntu2 compizconfig-backend-gconf=0.9.2.4-0ubuntu1 compizconfig-settings-manager=0.9.4-0ubuntu2 python-compizconfig=0.9.4-0ubuntu1 compiz-plugins-extra=0.9.4-0ubuntu3
```
compiz wouldn't come up afterwards.

Anyway, maybe someone is experiencing similar issues and has found some fixes or workarounds or just wants to share some thoughts. I find it rather disturbing that my once rock solid "compiz+emerald+docky+dual head" desktop from 8.04 has become more and more unstable over the years.

One more thing, Unity or Gnome3 are no alternative for me atm. LXDE feels good, but since I want to use compiz I run into the same troubles.

---


---
title: "Dead keys not working in KDE apps; &quot;sudo im-switch -s default-xim&quot; not helping"
date: 2010-04-14
forum: Desktop Environments
---

### Post by mutvik on 2010-04-14
Hi. After updating to Lucid Beta 2, dead keys didn't work in KDE apps (as described [_here_]("https://bugs.launchpad.net/kubuntu-ppa/+bug/520408")) regardless of keyboard layout. while trying to fix it, I made matters worse, so I reinstalled Lucid. Same problem. For everyone else "sudo im-switch -s default-xim" fixes the problem, but I get the error

No system wide default defined just for locale nb_NO .
Use "all_ALL" quasi-locale and set IM.
update-alternatives: using /etc/X11/xinit/xinput.d/default-xim to provide /etc/X11/xinit/xinput.d/all_ALL (xinput-all_ALL) in manual mode.

... and dead keys stop working in every app; in gedit (for example), not even æ, ø, å work (I have a Norwegian keyboard layout). This I fixed by running "sudo dpkg-reconfigure xini xserver-xorg" (both are probably not necessary). Had I figured it out before, I wouldn't have had to reinstall, but anyways: Dead keys still doesn't in KDE apps like Anki, and this is a major problem since I have to usa a lot of funny letters with diacritics, umlauts, accents etc.

Does anyone have any idea how this could be fixed. I haven't been able to find any solution if "sudo im-switch -s default-xim" does't fix it.

---


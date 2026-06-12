---
title: "Previously functioning Compiz now not working?!?"
date: 2010-01-29
forum: Desktop Environments
---

### Post by phredbull on 2010-01-29
Not sure if this is caused by the last auto-update, but it happened after a rare Win XP login...
I'm using Ubuntu 9.10, (Wubi install), on a laptop w/an older ATI card. Previously, I had a fully functioning desktop; Compiz effects, (Widget layer, transparency, Emerald), and Cairo Dock. After using XP, I rebooted into Ubuntu, (kernel 9.26.32), and Cairo Dock has a black box around it, my Widget desklets are on the desktop, and any windows I open have no titlebars. (See 1st screenshot.)

When I click the Compiz>Reload WM applet in Cairo, I get titlebars, but no Emerald.

When I manually start Compiz, the desktop goes black, I can still see Cairo Dock, but when I mouse over it, or when I open, close, or move windows, they leave a messy trail. (See 2nd screenshot.)

I tried switching between EXA and XAA in my xorg.conf. Do I need to repair or reinstall Compiz, or my drivers? (I'm using open source drivers.)

I've searched the forums for solutions, but none of them worked for me. Please don't suggest "Disable Compiz" as a solution.

(Strangely enough, "Pop up when mouse hits a corner" now works w/Cairo, while it didn't work when Compiz seemed OK.)

---

### Post by spiderbatdad on 2010-01-29
I have used compiz and cairo-dock successfully for many months at a time and not experienced any breakage. Others have said the two wont run well together.

Your problem was described well. Did you try to fix by rebooting Windows, shutting down cleanly/completely, then restarting. I haven't had experience running Wubi. I'm wondering if the Wubi system is running poorly after resume from suspend.

---

### Post by phredbull on 2010-01-29
I did reboot into Win XP, used it for a while, then did a total power down. I then rebooted into Ubuntu, and am now writing from it. Still the same.

---

### Post by phredbull on 2010-01-30
bump

---

### Post by phredbull on 2010-02-01
I tried resetting Compiz to default settings w/this:
```
gconftool-2 --recursive-unset /apps/compiz
```
But I don't see any change. Any other suggestions?

---

### Post by chriskin on 2011-01-04
did any solution come up? i have the same problem right now

---

### Post by phredbull on 2011-01-09
Oh, this was a long time ago. I think it may have been due to my ATI drivers. I installed the xorg-edgers PPA for cutting-edge OSS drivers. I use that w/the latest kernel, (2.6.37) and everything seems to work quite nicely.

---

### Post by chriskin on 2011-01-09
installing the latest xorg solved it for me as well (i'm on nvidia though)

---


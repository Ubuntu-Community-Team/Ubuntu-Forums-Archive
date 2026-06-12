---
title: "Nexuiz slow after upgrade"
date: 2007-04-30
forum: Gaming &amp; Leisure
---

### Post by jonny_boy27 on 2007-04-30
Having recently upgraded to feisty (and therefore upgraded nexuiz in the process), I found that nexuiz is now unusably slow (slow in menus, slow to connect to server - even localhost!) and, accoring to the fps counter, averages around 2spf, yes indeed seconds per frame! The settings are the same as were and even with the detail/res/AA turned down it's still unusable

spec - athlon xp2500-M overclocked to 220X10.5, radeon 9800pro stock speeds using FGLRX driver

any ideas what might be causing this problem?

---

### Post by igor_nav on 2007-06-09
Same problem here. It looks as if Nexuiz is not using 3D acceleration and is instead in software rendering mode. Even at 640x480, it lags unusably.

---

### Post by timzak on 2007-06-10
I just noticed it's way slower than last week when I last played.  Could it have anything to do with the latest kernel critical update patch that was released this morning?

That's the only major change I can think of that might be related to this.

---


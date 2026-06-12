---
title: "Unity Panel &amp; Nautlius display Bug"
date: 2011-11-29
forum: Desktop Environments
---

### Post by LazyFan on 2011-11-29
Hi,
I am on Ubuntu 11.04 x64 edition. And the unity display seems to have changed to an old style of Ubuntu all by itself. This also affects nautlius and any application when maximised.

At first boot the vanilla Unity display and icons are shown. But once booting is complete something changes it to the display to the one shown in the screen capture.

I have tried sudo apt-get install ubuntu-desktop --reinstall and this did not work.

I would install the latest Ubuntu but there are some apps that I need that are not yet working on that version. So, I am hoping to stay on 11.04 until then.

Any ideas?

---

### Post by stinkeye on 2011-11-30
Happens a lot for me.
You need to kill nautilus.
In terminal 
```
nautilus -q
```

---

### Post by bobsageek on 2011-11-30
Happened to me a few times on an older Intel box with GMA 3150 graphics, has not happened with my new system. What kind of video are you running in that system?

---


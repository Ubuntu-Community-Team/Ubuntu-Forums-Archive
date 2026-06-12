---
title: "2 Unity issues Backlight &amp; Icons size"
date: 2011-10-14
forum: Desktop Environments
---

### Post by hish747 on 2011-10-14
I actually really like the unity interface as it is almost exactly like the way I use mac os x with the dock on the left. But I'm having two issues which are kind of annoying.

1.Despite installing compiz config settings manager and confirming the settings in gconf-editor, I can't get unity icons in the dock not to use the orange background which I find tacky.

2. The settings in gconf-editor indicate that you can control the icon size but no matter what value I use the icons remain the same size.

So is there a way to do this? I am especially interested in having the dock shrink to accomodate more icons instead of scrolling up and down.
Thanks,
Hish

---

### Post by Vtwin on 2011-10-14
To resize the icons, in CompizConfig Settings Manager select Desktop then Ubuntu Unity Plugin, then Experimental Tab and then you can use the slider in Launcher Icon Size. Hope this helps

---

### Post by Blaqksheep on 2011-10-14
Correct.  You can also alter the icon backlight settings in that same place via a dropdown box.  I'm quite fond of Backlight Toggles.  =)

---

### Post by hish747 on 2011-10-14
Right...I wasn't real clear. I tried changing the settings in the compiz settings and confirmed in gconf-editor that the changes stuck but the actual size of the icons hasn't changed and the backlight stays on regardless of what I select.

---

### Post by mc4man on 2011-10-14
Sounds like you're logging into unity-2d instead of unity(3d) or being logged into it as a fallback due to lack of 3d support

what does this show 
```
/usr/lib/nux/unity_support_test -p
```

Lots of ways to tell if on unity-2d, this is pretty straightforward (you'll see unity-2d listed
```
ps aux |grep unity
```

---

### Post by Gs Dewd on 2011-10-15
Yes it does sound like your in 2d mode not 3d. I changed all my settings without issue.

---

### Post by hish747 on 2011-10-16
Thank You, That was it!

---


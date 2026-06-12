---
title: "Compiz Questions"
date: 2007-01-04
forum: Desktop Environments
---

### Post by Lucas0607 on 2007-01-04
Questions for Compiz on Edgy

a) how do you launch compiz automatically upon logging-in?

b) How to get cgwd themer?


Thanks :D

---

### Post by zgornel on 2007-01-04
To add compiz to the gnome startup list, go to System/Preferences/Sessions, Startu Programs tab, click add and insert this: */usr/bin/compiz --indirect-rendering --strict-binding --use-cow --replace gconf*. Dunno about the cgwd themer, i use the default one.

---

### Post by Lucas0607 on 2007-01-05
That startup command didn't work.... Is there another way?

Oh and there's an issue with screen resolution with mine..

So I got it to run at 1440x900 as this is the screen's native resolution at 58 hz (60 hz in windows)... So everytime I restart, starting with the login screen, the resolution shrinks down to I think 1024x768 and there's a huge blank space at the left... So I have to login and reselect the right settings again everytime I start ubuntu from system pref screen resolution. How do I fix this and let it stay at 1440x900?

Thanks

---

### Post by zgornel on 2007-01-05
Try writing down the compiz startup coomand in a terminal a see what it reports. I can't help you too much with the resolution problem, check xorg.conf to see if the resolution is listed.

---

### Post by Lem on 2007-01-05
The current (gandalfn) compiz doesn't use cgwd - it just uses metacity themes instead.

Cgwd was part of the old quinnstorm compiz before it became Beryl.

---


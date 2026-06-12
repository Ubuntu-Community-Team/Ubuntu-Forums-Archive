---
title: "Compiz broke my lockscreen...is there a fix?"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by smitjel on 2007-10-31
I updated from Ubuntu 7.04 to 7.10 recently and it looks like when I have any Visual Effects set (normal or extra), my lock screen doesn't work properly.  I get kicked all the way out to the gnome login screen when I try to lock my screen.  If I turn Visual Effects off, the lock screen works as expected.  I'm running the restricted drivers on an ATI X300 card.

What gives?  Is this a known issue?  Thanks for any help!

---

### Post by scottp26 on 2007-10-31
using ATI proprietary, same problem, lock screen goes out to login screen, turn off proprietary, it works but monitors go back to clone...........any help would be appreciated......gots to have my lock screen here at work.

---

### Post by smitjel on 2007-10-31
> **scottp26 said:**
> using ATI proprietary, same problem, lock screen goes out to login screen, turn off proprietary, it works but monitors go back to clone...........any help would be appreciated......gots to have my lock screen here at work.
I'm at work too and lockscreen is a MUST.  To get my lockscreen back, I found it easier to turn off the visual effects rather than disable the ATI driver.  Have you tried that?

---

### Post by scottp26 on 2007-10-31
yea, tried to disable effects, actually they weren't on.  I found out that I have to use the ATI drivers to get dual screen and big desktop working, when I do that lock screen logs out, I can disable the ATI drivers giving me clone screen and lock screen works.  I've spent all day on this......about to load back up 6.06 that I had working very well and stable, just wanted a fresh install...........i've read and read and tried and tried and still nada.......will holler if I find the answer.....

---

### Post by smitjel on 2007-10-31
You might be able to drop to 7.04....I'm pretty sure this wasn't an issue before I upgraded.

---

### Post by scottp26 on 2007-11-01
smitjel, Figured it out kinda......i reinstalled 7.10, download ati 8.42.3 drivers installed and then ran " sudo aticonfig --initial=dual-head --dtop=horizontal,reverse --screen-layout=right -v"
restarted, screens were right and screen lock works.  It does not work however with a 3D screen saver, it will take me back to the log in screen everytime.  I used blank screen instead of random and no problem,  I have screensaver set to sonar and it works fine too, just can't use any 3D which was cool to set it on random, but at work I just want stuff to work, effects would be nice but they won't get me anywhere.  Hope this helps........

---

### Post by smitjel on 2007-11-01
Thanks for the tip!  I set Visual Effects to "Extra" and just changed my screensaver to blank screen and it works.  I've got compiz and lockscreen.  Thanks!

---


---
title: "Power management not working"
date: 2010-05-07
forum: Desktop Environments
---

### Post by sabersong on 2010-05-07
I upgraded to Lucid a couple days ago, and noticed that my display turns off after 10 minutes of inactivity.  SO I tried adjusting the power management settingds.  But no matter what I do, the display still turns off after 10 minutes of inactivity.  This is really inconvenient when I'm working with the computer AND a book at the same time.  Is there anything I can do about it?

---

### Post by Zorael on 2010-05-08
I can't reproduce this.

And you're sure you're modifying the same power management profile that's in effect?

---

### Post by sabersong on 2010-05-08
Yes, that's exactly the screen I'm working with.  I've changed all the settings for all the profiles, turned Power_Devil off and on, tried everything under power management, and nothing works.

---

### Post by Zorael on 2010-05-08
Hm hmm.

Try removing (or renaming) the **kcmdisplayrc** and all files beginning with **powerdevil** in **~/.kde/share/config/**. This should wipe your power management settings. You'd probably need to log out and back in afterwards for this to have any meaningful effect.
```
$ mkdir ~/settingsbackup
$ cd ~/.kde/share/config
$ mv kcmdisplayrc powerdevil* ~/settingsbackup
```
Once back in, set up your power management settings (again) and see if they stick properly.

---

### Post by sabersong on 2010-05-10
Sorry for the delay , I've been away from the computer for a day or two.
I tried as you suggested, but it doesn't seem to have helped.

---

### Post by jboss1995 on 2012-09-21
I have the exact same problem. No mater what setting I use it still turns off at 10min. i know this is almost 3 years old but hope someone will help.

---


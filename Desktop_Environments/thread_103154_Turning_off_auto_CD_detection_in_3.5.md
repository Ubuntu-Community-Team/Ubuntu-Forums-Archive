---
title: "Turning off auto CD detection in 3.5"
date: 2005-12-13
forum: Desktop Environments
---

### Post by stimpack on 2005-12-13
Upon inserting a DVD I get a bizzare and slightly annoying series of events;

1. Empty Konquerer window pops up (huh?)
2. Open with dialog pops up
3. Windows style what do you want to do with this DVD dialog pops up, but before I can click anything...
4. Kaffine starts and trys to play the movie but crashes.
5. Crash handler dialog pops up

I now have 5 windows to close before i can even think of launching VLC.

I hated, I mean really hated this in Windows and always turned off disc detection upon new installs, this KDE seems even worse!, help me out please, how do I turn this off?.

---

### Post by NeoChaosX on 2005-12-13
System Settings > Storage Media. In the Notifications tab, select "Mounted DVD", select "Do Nothing", and hit the "Toggle as Auto Action" button. I would do the same for the "Unmounted DVD" option just to be on the safe side.

---

### Post by claydoh on 2005-12-13
With KDE 3.5, you should try uninstalling the [ivman package]("http://packages.ubuntu.com/breezy/utils/ivman"), which enables the automount/autorun/autoplay feature for KDE 3.4 but as KDE 3.5 already has its own method of doing this, this is why you are getting the multiple windows. Changing the settings in the Control Panel will not effect ivman's settings anyway.

---

### Post by stimpack on 2005-12-13
NeoChaosX: thanks bud, turned off notifications for both mounted and unmounted DVDs and it worked like a charm!

claydoh: the settings panel did also stop the old notification that was present in 3.4 as well as the new ones, dont know why, but hey :)

thanks both.

---

### Post by patsissons on 2005-12-19
[QUOTE=claydoh]With KDE 3.5, you should try uninstalling the [ivman package]("http://packages.ubuntu.com/breezy/utils/ivman"), which enables the automount/autorun/autoplay feature for KDE 3.4 but as KDE 3.5 already has its own method of doing this, this is why you are getting the multiple windows. Changing the settings in the Control Panel will not effect ivman's settings anyway.[/QUOTE]

Thank you so much, that problem was getting VERY annoying and I never would have thought to uninstall the old ivman package.

---


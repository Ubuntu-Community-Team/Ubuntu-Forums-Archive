---
title: "Bug in Lock screen kde 4.11.5"
date: 2014-02-13
forum: Desktop Environments
---

### Post by Miguel_Antonio_Sit on 2014-02-13
This week (second week in febraury 2014) Kubuntu update KDE, now to version 4.11.5. I have a netbook with plasma netbook. When go to hibernate or suspend, at comeback the lock screen must appear, like others kde version. But now just the wallpaper kde default (not the personal). I must go to a terminal ctr alt F2, log in, do ps -x and kill the last process, kscreenlocker_greet, then i come back to desktop environment (ctr alt F7) and comeback the lockscreen, i do my password on go in again. Obviously this is a bug. I have Kubuntu 13.10 all updated. Lenovo S10-2, no dual boot, just Kubuntu. All works fine. I have not screensaver.

---

### Post by Erik1984 on 2014-02-13
Coincidence... I was about to post the same issue. Thanks for the temporary 'solution' by the way (I stopped and started lightdm but that destroys the desktop session) :P I Googled this issue earlier on the day and found this thread on KDE forums: [http://forum.kde.org/viewtopic.php?f=66&t=119282](http://forum.kde.org/viewtopic.php?f=66&t=119282)

This post [http://forum.kde.org/viewtopic.php?f=66&t=119282&start=15#p301773](http://forum.kde.org/viewtopic.php?f=66&t=119282&start=15#p301773) has an interesting suggestion which I haven't tried yet:
> The login window will only appear after suspend, when I set the  'screen locker setting' -> 'start automatically after' to x minutes,  and the 'energy saving' -> 'suspend session' to a smaller amount of  minutes. E.g. suspend after 30 minutes, lock screen after 31 minutes.  Seems to be interfering.
I'll try this now and report back to this thread.

edit: If like me you don't know where to find the screen locker settings: they are located under "Display and Monitor" in the System Settings. The suspend settings are under "Power Management".

---

### Post by Miguel_Antonio_Sit on 2014-02-13
Obviously is a bug, and someone in KDE or in Kubuntu must chek it. I don't know how contact with someone inside.

Please, post the temporary solution in your kubuntu tread, to others users know it. :)

---

### Post by Erik1984 on 2014-02-15
Setting the screen locker to 31 minutes (1 minute more than suspend) seems to have worked for now.

---


---
title: "Multiple Xorg processes error!!!!"
date: 2009-01-10
forum: General Help
---

### Post by Xamiga on 2009-01-10
:(
Problem started yesterday.  I now am logged in twice after a reboot.

I have 2 Xorg instances, with root as the user and the same command line
'/usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth vt7'

It appears that the instance with the lowest ID is my correct login, but the one that displays is the higher ID.  The higher ID one does not have any of my preferences set correctly (mouse is right-handed where mine is left-handed, background is different).

I am able to Switch to the correct instance by going to System->Preferences->Mouse.

'users' shows al al
After 'switching' to correct Xorg and killing other Xorg CPU usage drops to normal levels ( was running 55% when both were up)

2.24.1 (Ubuntu 2008-10-24)
2.6.27-11-generic (#1 SMP Thu Jan 8 08:38:33 UTC 2009)
All patches up to date.

---


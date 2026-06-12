---
title: "RTCW GOY - Map &amp; sound stutter every 10 seconds!"
date: 2005-11-11
forum: Gaming &amp; Leisure
---

### Post by heftigrat on 2005-11-11
[FONT="Courier New"][COLOR="Black"]Well, I finally got Return to Castle Wolfenstein - Game of the Year edition running in Breezy by:

1.  Installing the legacy Nvidia drivers and changing the graphics card driver in xorg.conf from "nv" to "nvidia".
2.  kill-ing artsd so that it wouldn't monopolize the sound system.
3.  chown-ing the /home/non-root-user/.wolf path from root to non-root.

But now I have this problem where every 10-12 seconds or so the map & sound stutter for a second, which obviously hampers my gameplay.  It doesn't seem to be anything performance related, as it is at very regular intervals.  You can almost time them with a stopwatch (hey, there's an idea I might try).  Can anyone think of any app or daemon that runs in the background by default that might make this happen?  has anyone else had this problem?  Thanks all![/COLOR][/FONT]

---

### Post by heftigrat on 2005-11-11
[FONT="Courier New"][COLOR="Black"]P.S.  I'm a Kubuntu freak, but the user base in that particular forum seems kinda slim compared to this one.  That, and I'm not sure the issue is desktop-specific.  I'm undecided about the following question:
[http://ubuntuforums.org/showthread.php?t=85607](http://ubuntuforums.org/showthread.php?t=85607)
Some seasoned Ubuntu users have already posted, though the issue seems rather split.  Anywho...[/COLOR][/FONT]

---

### Post by Jenga on 2005-11-12
This sounds like a 3ddesktop stutter.  If you use 3ddesktop, this is almost certainly why.  It refreshes your desktops every ~10 seconds, which momentarily hogs your video bandwidth.

---

### Post by heftigrat on 2005-11-12
Thanks for the suggestion, but 3ddesktop isn't even installed.

---

### Post by heftigrat on 2005-11-12
Well, xfce is the sh!t.  I remembered seeing someone post that he/she only plays FPS's in xfce, so I gave that a try and viola!  Perfectly smooth gameplay.  Must be KDE specific, my apologies all for posting in the Gnome forum.

---


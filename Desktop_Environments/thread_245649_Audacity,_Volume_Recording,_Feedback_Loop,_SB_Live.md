---
title: "Audacity, Volume Recording, Feedback Loop, SB Live"
date: 2006-08-28
forum: Desktop Environments
---

### Post by peabody on 2006-08-28
I have an old SP Live card.  It's working fine in dapper, but while trying to record from the volume in Audacity I encountered a nasty feedback loop (SCREEEEEEEEECH!).  I didn't have this Fedora Core 4.  I managed to solve the problem by screwing around in the mixer forever.  I eventually turned everything on in preferences in GNOME mixer.  There were two outputs marked AC97.  Muting the one on the right seemed to stopped the feedback loop.  I was feeling pround of myself until I discovered the feedback loop came around to haunt me again on reboot.  Is there anyway I can save my mixer settings in dapper.  I came across a post on a different forum that talked about an alsactrl store and restore command.  However, alsactrl doesn't appear to be on my system, and apt-cache search alsactrl doesn't turn up anything.  All advice appreciated.

---


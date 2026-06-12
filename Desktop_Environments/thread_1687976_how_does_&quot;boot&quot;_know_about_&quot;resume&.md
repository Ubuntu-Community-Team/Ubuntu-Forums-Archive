---
title: "how does &quot;boot&quot; know about &quot;resume&quot;"
date: 2011-02-14
forum: Desktop Environments
---

### Post by SaintDanBert on 2011-02-14
While GRUB2 is running, is there some file or flag or data item that can be read to learn that a candidate-for-boot has a pending resume-from-suspend?

If you suspend-to-disk (aka, "hibernate") your workstation does a real power-off shutdown. You then activate a real power-on system start to resume-from-suspend (to-disk). Since "hibernate" must begin from a power-off restart, there must be persistent (on-disk?) artifacts available so that the system-start processing becomes aware of a pre-existing "hibernate" state recording and can activate that preserved state. Any hardware experienced a complete power-on-reset and is therefore "cold" until the recorded state gets restored.

If you suspend-to-ram (aka, "sleep") your workstation, you know that a "resume" is pending because you usually have some sort of LED ("new moon" etc) power on indicator. The hardware never loses power and so state recovery is significantly simpler than for the "hibernate" case with full power-off. resume-from-sleep becomes more "begin where you left off" once you get full power (clock rates, etc) restored.

~~~ 0;-Dan

PS/ It might be nice, if the GRUB2 menu could present some on-screen artifact saying that a resume-from-suspend was available on any of the available boot candidates. ~~~ 8d;-}

---


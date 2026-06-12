---
title: "System freezes after upgrade from Ext3 to Ext4"
date: 2009-05-05
forum: General Help
---

### Post by utkjamie on 2009-05-05
I've been using Jaunty since the Release Candidate and haven't had any problems with system freezes. In fact, I can't recall the last time I had a system freeze under Intrepid. I upgraded my filesystem from Ext3 to Ext4 today and since then I have had 4 system freezes that could only be remedied by killing the power to my computer.

One of the freezes happened while watching a video in VLC. The other three freezes happen whenever I click a click to a torrent file in Firefox and have it open the torrent file with Ktorrent. Without exception, the system freezes up every single time. This has never happened before upgrading to Ext4 and Ktorrent runs fine and opens torrents from inside the program without a problem.

I would mark this as a Firefox+Ktorrent+Ext4 problem except that the freeze also took place in VLC, which leads me to believe that it is probably just a matter of time before I get another random freeze in some other app.

Anyone else having these problems or have suggestions for fixing them?

---

### Post by utkjamie on 2009-05-15
I haven't had a freeze in several days, which may mean that some of the recent updates have fixed the problem (fingers crossed). Other people are still reporting freezes, but I don't know if my problem and these other problems are related.

---

### Post by utkjamie on 2009-05-15
> **utkjamie said:**
> I haven't had a freeze in several days, which may mean that some of the recent updates have fixed the problem (fingers crossed). Other people are still reporting freezes, but I don't know if my problem and these other problems are related.

I spoke too soon. Went out for a bit after posting this last message and came home to a frozen computer. Tried to reboot but am getting *kernel panic* errors and:

```
Not syncing VFS: unable to mount root fs on unknown block (0,0)
```I think I may have even bigger problems now.

**UPDATE:** Turns out the problem is trying to boot with the newly upgraded 2.6.28-12 kernel. Booting with 2.6.28-11 works fine so I don't know if this is a buggy kernel or the upgrade itself was bad.

---


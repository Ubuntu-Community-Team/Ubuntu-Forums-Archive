---
title: "Won't restore from hibernation... sometimes."
date: 2011-11-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by johnathanamber on 2011-11-27
Hey everyone,

I've been having an ongoing issue with restoring the system from hibernation... sometimes.

Looking in my kern.log for 24NOV11, I see 6 entries for going into hibernation:
> PM: Marking nosave pages: 000000000009d000 - 0000000000100000
PM: Basic memory bitmaps created

The above was created at these times:
> Nov 24 03:15:41
Nov 24 04:41:28
Nov 24 11:23:09
Nov 24 12:04:59
Nov 24 21:54:02
Nov 24 23:57:19

But I only see 5 entries for restoring from hibernation:
> PM: Syncing filesystems ... done.

The above was restored at these times:
> Nov 24 10:17:29
Nov 24 11:50:37
Nov 24 21:11:30
Nov 24 22:59:50
Nov 25 00:15:10

In the above times, the only one that didn't restore from hibernation was the first instance of hibernation @ 03:15:41 and the next entry is as follows:
> Nov 24 03:47:49          imklog 4.6.4, log source = /proc/kmsg started.

What logs can I provide that would help in figuring out why the system won't restore from hibernation but then just restart as if the system was shutdown?

System Specifications:
Dell Vostro 3700
Xubuntu 11.04 32bit
Intel and NVidia Graphics adapters
Plugged into the AC adapter the entire time with the battery charged.

Thank you and God bless,
Johnathan

---

### Post by NickCarriere on 2011-12-02
Don't recommend the use of hibernate or suspend. Just use shutdown and you should be fine. I don't ever need my computer fast enough to not be able to wait 1 second longer, hibernate takes just as long to come up as a full power on plus you have a fresh start when you shutdown. If you need something open. IDK. I just keep a server running so i dont shutdown anyway. I guess i am not help to your issue but to tell you to not care. Meh. I tried :P Good luck.

---

### Post by johnathanamber on 2012-01-17
Hello everyone,

I've reinstalled with the 64bit version and everything is working fine.

Thanks gor the help.

God bless,
Johnathan

---


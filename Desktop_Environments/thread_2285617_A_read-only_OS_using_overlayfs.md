---
title: "A read-only OS using overlayfs?"
date: 2015-07-07
forum: Desktop Environments
---

### Post by tony14 on 2015-07-07
I need to emulate what is the [windows' Enhanced Write Filter](https://msdn.microsoft.com/en-en/library/bb499244(v=winembedded.51).aspx):  a layered filesystem where all write operations go to a RAM-based storage so that changes DO NOT persist through reboots.However, for reasons of OS updates and|or software re-configurations - some selected changes should be manually made to stick (i.e. be made permament).I found this [How To: Build A Read-Only Linux System](http://www.logicsupply.com/blog/2009/01/27/how-to-build-a-read-only-linux-system/) with the **aufs** and tested it.It does sort of "work" but gives lots of undesired issues:1) DHCP broke (only manual network setup is possible);2) USB-flash disk's automount broke.Also, it is not so user-friendly if you need to make some changes to persist the reboots...Is there a (novice-level) How-To on using the **overlayfs** to achieve a read-only OS?

---

### Post by v3.xx on 2015-07-07
I don't know my way around overlayfs, but thought this thread may give you some ideas.

[http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694)

Good luck

---

### Post by tony14 on 2015-07-07
Thanks, **v3.xx**. German Ubuntu community has an [article](https://wiki.ubuntuusers.de/Nur-Lesen_Root-Dateisystem), tried its' script but it does not work for me: the **overlayfs** does not appear in the **mount**'s output.

---

### Post by v3.xx on 2015-07-07
Is overlayroot of any use to you?

[https://www.google.com/search?client=ubuntu&channel=fs&q=overlayroot&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=overlayroot&ie=utf-8&oe=utf-8)

Again, this is something I know of, but have not used.

---


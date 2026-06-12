---
title: "Format of PS3 internal drive"
date: 2009-12-09
forum: Gaming &amp; Leisure
---

### Post by wesg on 2009-12-09
I have a PS3 and Ubuntu 9.04 server. My friend also has a PS3, and he's removed the internal drive to upsize it. I want to try to transfer some files to and from this internal drive, but I haven't been able to access. Does anyone have the format of the internal drive and can confirm that it will mount on a Ubuntu system?

---

### Post by beastrace91 on 2009-12-10
[This post](http://www.ps3news.com/forums/playstation-3-news/playstation-3-hdd-file-system-details-direct-sony-92825.html) claims it is a fat32 drive how ever [this thread](http://boardsus.playstation.com/playstation/board/message?board.id=ps3&thread.id=3842541) debates that point some.

All in all just hook it up and see if it automounts/reads what do you have to loose?

Regards,
~Jeff

---

### Post by wesg on 2009-12-12
Thanks for the reply, Jeff. That was my plan, but I wanted to see if someone else had done the same, and maybe save me the trouble. I will definitely post the results when I try, though.

---

### Post by mister_playboy on 2010-02-05
The PS3 uses filesystem encryption, so the drive should not be readable in anything other than the PS3 it belongs to.  This is why it's important to use the built-in backup tools to copy your PS3's data elsewhere when swapping HDDs.

EDIT: Wikipedia lists the filesystem on the PS3 as being UFS2.  You would want to install [FONT="Courier New"]ufsutils[/FONT] and [FONT="Courier New"]libufs2[/FONT] for your backup attempt.

---


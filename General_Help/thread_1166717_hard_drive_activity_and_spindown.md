---
title: "hard drive activity and spindown"
date: 2009-05-22
forum: General Help
---

### Post by olivine on 2009-05-22
I have a 200 GB Seagate (Barracuda 7200.7) in a no-name USB enclosure that I want to use for storage as part of a home server (nslu2). I've been having trouble controlling its spindown frequency. I'm getting increasingly confused about this and have several newbie questions...

When spinning down the disk manually, I assume the correct procedure is to check lack of activity, unmount it, and spin it down. How can I tell that the drive is spun down successfully other than from the  noise?

I've tried using several tools (e.g. scsiadd). I *think* it works (the box still makes noise, but I think it's mostly the box fan). However, the disk makes clicking noises (for 30-60s) every 7 minutes or so. Is this due to the disk itself or to the enclosure? It happens even when it's not connected to a PC. Is hdparm the solution? I'm confused about that tool.

More generally, is there a way to monitor/record disk activity and spindown frequency over a long time? Using smartmontools with this drive gives errors (drive too old?).

Thanks in advance for any help!

---

### Post by khelben1979 on 2009-05-22
```
man hdparm
```

---

### Post by olivine on 2009-05-22
I have not so far been able to prevent the drive spinning up again every 7 minutes using hdparm. So, no, that doesn't help.

---

### Post by moster on 2009-05-22
Maybe this is what you need:
[http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking]("http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking")

In other hand, I had previously serious clicking noise from my former usb disk enclosure. Problem was in that cheap enclosure, I change it to new one and more quality one, and after that it work fine... To be more confusing, that faulty enclosure worked fine with another disk... very strange..

---

### Post by olivine on 2009-05-22
Thanks for the advice, moster. I've tried to follow some of the advice in the link you gave, but I haven't gotten anywhere. The link and your experience show that there isn't always an easy solution. I'll mess with things a bit more and post here if I get any further.

---


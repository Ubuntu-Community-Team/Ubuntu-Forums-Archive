---
title: "Incorrect time"
date: 2009-03-27
forum: General Help
---

### Post by reabralop on 2009-03-27
I've been looking all over for this and can't find it. Given how simple this is I'm surprised I can't find it. 

I have three different machines running Ubuntu and none of them seem to be able to hold the correct time since Daylight saving. I've changed the time in the time/date but it doesn't stick. 2 of the machines are older home built ones but the third is a brand new Mini 9. I could understand if the bios was out of date (older machines) but I've updated that. 

What am I doing wrong?

---

### Post by Iowan on 2009-03-27
Are they all set in the same time zone or GMT (UTC)? Is it just the hour that slips (changes), or are they changing minutes, too.  There were some updates awhile back to accommodate the "new" DST.

---

### Post by reabralop on 2009-03-27
They are all set to the same time zone and it is just the hour that's affected. I keep my machines up to date. Are the updates you mentioned not part of the normal update manager?

---

### Post by reabralop on 2009-03-30
Bringing this back to the top in hopes someone can help me get this fixed. Anyone, anyone...

---

### Post by |Porsche on 2009-03-30
Are you using the same time servers on all boxes?

---

### Post by martinbaselier on 2009-03-30
I had the same problem and solved by changing UTC=no to UTC=yes in /etc/default/rcS

---

### Post by reabralop on 2009-03-30
I had it set to a time zone in Mexico. I changed that to one in Canada and it seems to be fixed. I'll try that with my other machines now.

---

### Post by DGortze380 on 2009-03-30
> **reabralop said:**
> I had it set to a time zone in Mexico. I changed that to one in Canada and it seems to be fixed. I'll try that with my other machines now.

Not all time zones utilize Day Light Savings Time... I believe Mexico would be one of them, it being so close to the equator.

---

### Post by aspora.isernia on 2009-04-01
> **martinbaselier said:**
> I had the same problem and solved by changing UTC=no to UTC=yes in /etc/default/rcS

Same here: I solved with that change. Now the clock tooltip shows 'CEST' after the time.

Thanks

a.i

---


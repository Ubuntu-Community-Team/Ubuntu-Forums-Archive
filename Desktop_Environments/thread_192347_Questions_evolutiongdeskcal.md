---
title: "Questions evolution/gdeskcal"
date: 2006-06-08
forum: Desktop Environments
---

### Post by Tym on 2006-06-08
Hi everyone,

I have a few questions:

**Gdeskcal**
In Windows XP I used rainlendar to orden my appointments. On the internet I found a way to share these appointments with linux, I only had to save them in an iCal file (in rainlendar). After that, I created a symlink to this file in /home/tym/.evolution/calendar/local/system/calendar.ics. All my appointments appear perfectly in evolution. But when I start Gdeskcal, it has a CPUload of 100% and doesn't seem to stop. I only get a grey plane where gdeskcal is loading. Does anyone know why this could happen? Perhaps there are some lines in the file which gdeskcal can't handle?

**Evolution**
I want to use evolution to access an exchange server. I understoud that there are some problems using evolution shipped with Ubuntu 6.06. To solve this, I have to force an older version of evolution in synaptic, but when I select the package 'evolution', the option 'Force version' is greyed out.
I added every source in the list, but that doesn't work.
Can anyone help me with this?

Thanks in advance!

Tym

---

### Post by Scunizi on 2006-06-08
I'm taking a guess here, but if your iCal file is on a NTFS partition that may be your problem.  Linux won't write to NTFS

---

### Post by Tym on 2006-06-09
Thank you for your reply Scunizi, but the iCab file is on a fat32 partition, I do have sufficient rights, because everything works fine in evolution.

---

### Post by Tym on 2006-06-09
Are there perhaps other desktop calendars which can read and write the iCal format?

---

### Post by Tym on 2006-06-09
*bump*

---

### Post by jandi on 2006-10-13
Rainlendar has now a version for linux :)

---


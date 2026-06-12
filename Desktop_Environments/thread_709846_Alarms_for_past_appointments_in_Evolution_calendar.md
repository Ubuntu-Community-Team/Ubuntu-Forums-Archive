---
title: "Alarms for past appointments in Evolution calendar"
date: 2008-02-27
forum: Desktop Environments
---

### Post by Patb on 2008-02-27
With apologies for my ignorance, I would like to know if Evolution can issue an alarm for appointments which have already passed but which have not yet been subject to an alarm.  For example, if my computer was not switched on till lunch time today and there was an appointment at 10:00 am this morning, no alarm is given (even though evolution-alarm-notify is running in the background).  Is there a way to change this so that an alarm is given for past appointments that have not yet been brought to my attention?  Or have I missed something obvious?  

Thank you for any assistance.  Cheers, Pat.

---

### Post by Patb on 2008-03-18
Apologies but "Bump".

---

### Post by ACGarland on 2008-04-10
Not sure I understood the previous post (about "Bump").  Did you get any responses (offline) on this?  I have the same concern/desire.  Seems like it should at least be configurable ([x] issue missed alarms).

---

### Post by ACGarland on 2008-04-10
OK - so now I've found out two additional items since my previous post.

I ran "evolution --force-shutdown" and then when I restarted evolution:

1. Previous alarms that expired when evolution was not running did in fact appear.

2. Alarm sounds associated using 'aplay my-sound.wav' did in fact get played.

So it would appear that something was amiss with the evolution-related daemons and restarting them 'fixed' the problem (at least for now).

---


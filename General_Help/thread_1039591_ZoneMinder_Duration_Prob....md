---
title: "ZoneMinder Duration Prob..."
date: 2009-01-14
forum: General Help
---

### Post by amoeba13 on 2009-01-14
Using Ubuntu server 8.10 and ZoneMinder 1.23.3x (from Repositories). All is working except I can not get it to mocord to record in 600 second blocks (varies greatly from 300 seconds in length to over 32000; set to 600 in ZM settings). Has anyone else seen this? If so, what am I missing?

Thanks,
Ray

---

### Post by amoeba13 on 2009-01-26
Turns out all that was missing was setting the ZM_FORCE_CLOSE_EVENTS in the options. fyi...:p

---


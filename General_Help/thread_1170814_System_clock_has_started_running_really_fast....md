---
title: "System clock has started running really fast..."
date: 2009-05-26
forum: General Help
---

### Post by bmturney on 2009-05-26
We are running an old Linux server (Ubuntu 6.06.1).  Up until about a week ago it was running just fine.. then we started having some weird things start happening... today I started looking into it and noticed the system clock was set to this coming Thursday.  So I reset the system clock to the current time... this was about 4 hours ago... and it now is about an hour and 15 minutes ahead again.

What could cause this, is there a fix for it?  We will be replacing this server soon with a newer one, but in the mean time I need to see if I can get this fixed because we have some time sensative jobs that run on this server.

Any ideas?

---

### Post by Kareeser on 2009-05-26
That's odd... I would suggest a faulty CMOS battery, but usually, the time goes backwards, not forwards. In any case, you could check that out. Replacement batteries, you can get from Radioshack, etc...

I'd suggest running "ntpdate" in a cronjob to keep the time in check in the interim, but that requires root acces... argh.

---

### Post by bmturney on 2009-05-27
this is an old machine anyway and we are about to take it out of service... I will probably just run the ntpdate via cron until we make the switch...

---


---
title: "Backup Issue Solution Needed !"
date: 2005-12-21
forum: General Help
---

### Post by ksudbury on 2005-12-21
OK heres my situation. 

Windows 2000 server running Exchange Active Directory and running as a file server. 

I have a admin who cant backup with tapes he forgets or the tape drive errors and it would be alot tidier if it was done remotely. 

Now here is my ideal 

I want to run it remotely, now this would have to be done as a differential backup as i only have a limited amount of bandwidth, after the first backup is done i only want to add what has changed (its round 80gigs of data). 

Now i need some thing that understands MS exchange to bk it up i was thinking about running backup's locally to bk up exchange then rsyncing it over. 


All solutions welcome !

Thanks! :KS

---

### Post by waster on 2005-12-23
so where does Ubuntu come into it? My recommendations? Shitcan the win2k server install and discipline your system administrator.

---

### Post by dcraven on 2005-12-23
I'm with waster on this one.

~djc

---

### Post by rcerreto on 2005-12-23
As long as I agree with waster and dcraven, I still think that this forum spirit is to help whenever possible. :) 

I'm not a backup expert but I think that amanda ([www.amanda.org](www.amanda.org)) could be helpful.

---


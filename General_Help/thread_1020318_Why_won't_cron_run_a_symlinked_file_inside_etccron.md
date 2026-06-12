---
title: "Why won't cron run a symlinked file inside /etc/cron.d/ ?"
date: 2008-12-24
forum: General Help
---

### Post by dgath on 2008-12-24
I've tried creating a symlink (ln -s) inside /etc/cron.d/ to a file that resides in my home directory, and it doesn't appear to actually run.  But, when I copy that file into /etc/cron.d/ it appears to work fine.  

I've tried this on two boxes, one running Ubuntu 8.10 and the other running RHEL 4, and it works on the RHEL4 box, but not on the Ubuntu box. Any ideas as to why it doesn't work?

---

### Post by dcstar on 2008-12-24
> **dgath said:**
> I've tried creating a symlink (ln -s) inside /etc/cron.d/ to a file that resides in my home directory, and it doesn't appear to actually run.  But, when I copy that file into /etc/cron.d/ it appears to work fine.  

I've tried this on two boxes, one running Ubuntu 8.10 and the other running RHEL 4, and it works on the RHEL4 box, but not on the Ubuntu box. Any ideas as to why it doesn't work?

AFAIK cron requires exclusive access to a file when it is running it and that may not be possible using a symlink, if that is the case then the Ubuntu version may be the one that works as it is supposed to.

---


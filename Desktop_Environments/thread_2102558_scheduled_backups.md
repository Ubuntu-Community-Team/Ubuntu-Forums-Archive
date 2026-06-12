---
title: "scheduled backups"
date: 2013-01-07
forum: Desktop Environments
---

### Post by cybergalvez on 2013-01-07
I just set up a home nas built around freenas. I am connecting via ssh (samba seems a little slow) so far making my inital full backup seems to be taking quite a long time, going on 3 days now, which I am attributing to my computer being wireless (the nas is wired), and so far one failed backup attempt. 

Once the initial backup is done, I am going to set it up for daily backups, which I think happen at midnight, so I will have to keep my computer on, but do I have to stay logged in? can I log out and just leave it running, will deja dup still do my daily backup even if I am not online?

I am also going to set up a more limited offsite backup using either straight duplicity  or time back (another duplicity gui) using a cron job. Will the cron job trigger again if I am not logged in?

thanks in advance for the info

---

### Post by cybergalvez on 2013-01-09
reading up on deja dup it does not use Cron to do its scheduling so I do need to be logged in for my daily backups, but for my remote set, which I will use Cron for I apparently would not have to be logged in

---


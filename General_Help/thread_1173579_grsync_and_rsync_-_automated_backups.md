---
title: "grsync and rsync - automated backups?"
date: 2009-05-29
forum: General Help
---

### Post by infinitejones on 2009-05-29
I've used grsync to set up a simple backup of a few folders in my home directory to a remote folder (mail, settings etc). 

It seems to be working fine on a one-off basis, ie. I open grsync, hit execute, and the process runs with no errors.

I know that grsync just offers a useful GUI for rsync but my question is - now that I've set up the process with grsync, is there some kind of rsync daemon that will run it all automatically (eg. at a certain time every day) or do I have to open grsync and execute it myself every time?

---

### Post by Legace on 2009-05-30
You can add it to cron:

[http://www.linuxbasement.com/content/backups-using-rsync-bash-cron](http://www.linuxbasement.com/content/backups-using-rsync-bash-cron)

---

### Post by infinitejones on 2009-05-30
That's great, thanks - that whole linuxbasement site looks really good too!

---

### Post by colau on 2009-06-04
> **legace said:**
> you can add it to cron:

[http://www.linuxbasement.com/content/backups-using-rsync-bash-cron](http://www.linuxbasement.com/content/backups-using-rsync-bash-cron)
+1

---


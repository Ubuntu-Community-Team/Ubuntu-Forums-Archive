---
title: "Rsync Errors on Backup?"
date: 2010-06-07
forum: Desktop Environments
---

### Post by linux4me on 2010-06-07
I'm using Grsync to synchronize my home directory between two Ubuntu Lucid machines. I've done this for years, and rarely had a problem. However, after a recent crash of Evolution, I now get the following error messages when I run the Grsync command to do the backup:
> rsync: send_files failed to open "/home/myusername/.evolution/mail/local/Outbox.ibex.index": Input/output error (5)
rsync: send_files failed to open "/home/myusername/.evolution/mail/local/Outbox.ibex.index.data": Input/output error (5)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]

I have verified that the two files actually exist and that the permissions for them are the same as other files that transfer correctly. 

What's the best way to repair the files so that the files can be transferred without errors?

TIA

---


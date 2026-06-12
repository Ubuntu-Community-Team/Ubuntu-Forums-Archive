---
title: "Good Backup Application"
date: 2009-06-22
forum: General Help
---

### Post by chetancrasta on 2009-06-22
Can anyone recommend a good backup utility? I tried duplicity and deja dup but they didn't work.
I need to backup my documents to a remote server (godaddy.com) using FTP or SSH. I would like the files to be encrypted and the backups to be incremental. I should also be able to schedule backups.

---

### Post by kpkeerthi on 2009-06-22
**Hint: **rsync + SSH + cron. Google should get you more on this (I don't think its possible to post the entire instruction in one post. sorry).

---

### Post by chetancrasta on 2009-06-22
> **kpkeerthi said:**
> **Hint: **rsync + SSH + cron. Google should get you more on this (I don't think its possible to post the entire instruction in one post. sorry).

I'll try that and post the instructions here if I can get it to work.

It would be great if there's a single graphical utility, though.

---

### Post by Lampi on 2009-06-22
> **chetancrasta said:**
> I would like the files to be encrypted and the backups to be incremental. I should also be able to schedule backups.
What about bacula?

This one is really powerful, but it looks like a handful to make it work properly.

---

### Post by Healey on 2009-06-22
Hi

I use Unison - Its in the repos

Its more of a synchronization tool but as I only backup selected folders it works well for me

Easy to use as well

Regards

Healey

---

### Post by kpkeerthi on 2009-06-22
Try **g**rsync

---

### Post by mike555 on 2009-06-22
I have tried most and found "Back in Time" to be the best .........

---

### Post by Cheesemill on 2009-06-22
+1 for Back in Time
[http://backintime.le-web.org/](http://backintime.le-web.org/)

---


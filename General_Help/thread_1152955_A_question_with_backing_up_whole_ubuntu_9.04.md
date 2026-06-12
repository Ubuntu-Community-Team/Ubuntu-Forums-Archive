---
title: "A question with backing up whole ubuntu 9.04???"
date: 2009-05-08
forum: General Help
---

### Post by colau on 2009-05-08
Hi,
If I want to backup the whole ubuntu 9.04 only copying the /home directory in other partition will do the job for this?

---

### Post by Legace on 2009-05-08
Nope.
/home would only backup your documents and local settings.

To backup the whole system, you'd need to backup everything except the following:
```
/proc/
/dev/
/lost+found/
/sys/
/media/
/tmp/
```

---

### Post by colau on 2009-05-08
What is the best and easy way to do this?
Is it possible to backup after a certain period of time automatically?

---

### Post by Legace on 2009-05-08
> **colau said:**
> What is the best and easy way to do this?
Is it possible to backup after a certain period of time automatically?

Maybe you could use rsync, like this:

```
sudo rsync -av --delete --exclude-from="***PATH***/exclude" / /backup
```

Where ***PATH*** is the directory where exclude is saved.

exlude should be like this:

```
boot/
proc/
dev/
lost+found/
sys/
media/
tmp/
backup/
```

Note that /backup is the folder your system will be backed up to. If you decide to change that location, do so in the exclude file aswell.

To restore the backed up files, you would use:
```
sudo rsync -av --delete --exclude-from="***PATH***/exclude" /backup /
```

Note that this will take a while to complete.
Also note that after doing this once, the following times will be much faster :)


You could use cron to do this periodically.
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by mike555 on 2009-05-08
---   reconstructor can make an bootable/installable backup , and can be set to include your settings, etc.
      [http://tinyurl.com/3x23ry](http://tinyurl.com/3x23ry)

---

### Post by colau on 2009-05-08
> **mike555 said:**
> ---   reconstructor can make an bootable/installable backup , and can be set to include your settings, etc.
      [http://tinyurl.com/3x23ry](http://tinyurl.com/3x23ry)
Many thanks mike555.

---


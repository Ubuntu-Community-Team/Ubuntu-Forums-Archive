---
title: "&quot;Simple Backup&quot; is Simply Not Backing Up"
date: 2009-04-28
forum: General Help
---

### Post by umechanism on 2009-04-28
System:  Ubuntu 8.10, Dell Studio Desktop, and latest version of Simple Backup from Repos.

Simple Backup is not backing anything up.  I've tried the custom settings and standard settings.  I've tried saving to a remote drive, local drive, desktop, etc...but nothing ever gets backed up.  I get a message stating that the process number is "5644" or something like that but no evidence of backed up files exist.  Not after one hour or two days of waiting.  Nothing.

Is this a bug or am I going insane?

Thanks!

---

### Post by Ugluk on 2009-04-28
In case of successful backup you should see one or more folders with names like
2009-04-08_08.12.21.123456.computer-name.ful
 (or .inc)
in your specified destination. Have you checked whether you can write to destination directory? Do you have conflicting settings? If you look into running tasks, will there be a process with specified pid?

---

### Post by suresh_vandiyur on 2009-04-28
> **Ugluk said:**
> In case of successful backup you should see one or more folders with names like
2009-04-08_08.12.21.123456.computer-name.ful
 (or .inc)
in your specified destination. Have you checked whether you can write to destination directory? Do you have conflicting settings? If you look into running tasks, will there be a process with specified pid?
how to backup using the simple backup restore and simple backup config. plz guide me.

---

### Post by umechanism on 2009-04-28
> **Ugluk said:**
> In case of successful backup you should see one or more folders with names like
2009-04-08_08.12.21.123456.computer-name.ful
 (or .inc)
in your specified destination. Have you checked whether you can write to destination directory? Do you have conflicting settings? If you look into running tasks, will there be a process with specified pid?

Thanks for the reply.  There are no folders with ".ful" or ".inc" extensions.  I do have write permissions to the folders I'm saving into.  I even tried to create a backup to my local desktop but that did not work either.  I also checked for the process ID but it was not found (I looked for it right after I initiated the backup command).

---


---
title: "please clue-by-four me re: duplicity"
date: 2009-06-24
forum: General Help
---

### Post by IvoLucien on 2009-06-24
I think I have a decent duplicity script in cron.daily, but I'm missing some basic clue as to how to list-current-files or verify the archive. I could well be doing everything wrong...

```
ivo@www:/var/backups/duplicity# duplicity list-current-files --no-encryption file:///var/backups/duplicity
No signatures found, switching to full backup.
No signature data found, unable to list files.
```

The duplicity manifest and .gz files are in /var/backups/duplicity, and I'm currently doing everything locally until I get this working. Here's more info:

Ubuntu Server edition / Hardy Heron / ext3 filesystem / minimal laptop

excerpt from backup script:
```
duplicity --allow-source-mismatch --no-encryption --exclude-globbing-filelist /etc/backup/local-excludes --include-globbing-filelist /etc/backup/local-includes --exclude '**' --full-if-older-than 1W --time-separator='.' /  file:///var/backups/duplicity >>/var/log/duplicity.log
```

The include and exclude files above are populated as needed for the project.  The backup seems to work fine, as the backup file sizes vary with how much has changed, and the log file gives reasonable summary info.  I have deleted some older backup files, but do have a few recent sets (full and incr files.)

I hope I'm just failing to do something basic.

Thank you kindly,

Ivo in Seattle

---


---
title: "rdiff-backup target already exists"
date: 2009-05-19
forum: General Help
---

### Post by roel46 on 2009-05-19
Coming from ubuntu 8.04 I installed ubuntu 9.04 (fresh install on a new partition). I restored my 8.04 homedir to my new homedir in 9.04. Now rdiff-backup seems to dislike my old backups: it complains about the directories it finds there. More details:
[LIST]
[*]my backup goes to an usb stick which automounts to /media/disk/
[*]it contains backups from my work in ubuntu 8.04
[*]rdiff-backup now complains when I try to make a backup: Fatal Error: Restore Target /media/disk/home/roel already exists, specify --force to overwrite.
[*]I tried the --force option, but that doesn't change anything (it still advises me to use the --force option)
[/LIST]

Any ideas about making a nice backup without deleting my old backups? Thanks in advance.

---

### Post by roel46 on 2009-05-20
Aha, problem solved:
[LIST]
[*]rdiff-backup keeps its administration on the mirror in <target directory>/rdiff-backup-data
[*]if you copy that one to the source directory (what I did) rdiff-backup will refuse to backup; that makes sense: this would overwrite the administration on the mirror
[*]unfortunately the error message it gives is rather misleading: "Fatal Error: Restore target /media/disk/home/roel already exists, specify --force to overwite"
[*]I would have preferred a message like:       "Fatal Error: I (rdiff-backup) refuse to overwrite  my administration in /media/disk/home/roel/rdiff-backup-data/
[/LIST]
Anyway thanks to all of you who gave my problem thought. Groeten, Roel.

---


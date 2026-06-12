---
title: "9menu won't run backup script"
date: 2008-12-30
forum: General Help
---

### Post by Bubnoff on 2008-12-30
A 9menu puzzler:    [ Hardy Heron ]

I've been using 9menu for the past 2 years now and am
somewhat of a 9menu fanatic ...however.

I am currently using it to launch my backup scripts [ for testing
purposes ], view logs ...etc.

Problem:
When I manually run my backup.sh ( standard fare - nothing fancy ) it
runs like a champ - as expected. When I launch it from 9menu it runs
but doesn't create the logs or tar-ball. I watch it in the system monitor
and it slogs through the tar process then pops up a message box letting me
know it's complete ...yet no logs or tar-balls.

I use 9menu to launch my perl scripts and other stuff with no problems. Is
there some limit to 9menu such as: it can't create or modify files. This is the only thing that distinguishes this script from others I launch. If I 'touch' the files first, they aren't modified/updated.

Anyway ...details:

I run 9menu with:

 ```
9menu -geometry 150x66-4+200 -label "Backups" -bg "#000000" -fg "#F2EDD7" -font "-*-nu    -*-*-*-*-*-*-*-*-*-*-*-*" -file /media/disk/shermanBackups/.9menurc
```

Current .9menurc:

```
Full:/media/disk/shermanBackups/backup.sh
Incremental:sh /media/disk/shermanBackups/backupIncremental.sh
Full_Log:gvim /media/disk/shermanBackups/backup.log
Errors:gvim /media/disk/shermanBackups/error-log
Incremental_Log:gvim /media/disk/shermanBackups/incrementalBkup.log 
Deleted_Archives:gvim /media/disk/shermanBackups/deleted_archives
```

Any fellow 9menu fans out there with some advice?

Thank you -

Bubnoff

---


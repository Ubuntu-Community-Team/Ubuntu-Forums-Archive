---
title: "Backup script not running from crontab"
date: 2009-01-26
forum: General Help
---

### Post by wimmelis on 2009-01-26
Dear all,


My limited linux knowledge combined with my internet searching, does not quite get me out of this one, so I hope anyone does understand why this happens. If I run my self-made script for backup, then it runs fine from the terminal, but it does not do anything when run from crontab. As you can see, I tried to amend to cover for possibly different environment variables. I also tried running the script in "sh" shell terminal and that also works, but still not when run from crontab.

```

#!/bin/bash

# ---- Setting of environment variables which are different when run from crontab ----
HOME=/home/xxx
LOGNAME=xxx
PATH=/usr/bin:/usr/sbin:.
SHELL=/usr/bin/bash

# ------------- system commands used by this script --------------------
TAR=/bin/tar;
GPG=/usr/bin/gpg;

# ------------- file locations -----------------------------------------
DESTINATION=/media/BCKP_Daily;
INCLUDES=/home/xxx/backup_include;

# ------------- the script itself --------------------------------------
$TAR czf >($GPG -c --passphrase mypassphrase > $DESTINATION/test.tgz.gpg) -T $INCLUDES ; 
```

---

### Post by wimmelis on 2009-01-26
Dear all, 


Meanwhile done quite some debugging, but it seems the culprit is gpg when run from crontab. It seems to want access to /dev/tty and that is not available when run from cron .... (don't quite get what it means, but that was what the location offering the solution mentioned) so the solution is to add --batch to gpg and then it works like a charm.


WM

PS: If there is ever a price for answering your own questions, I'd probably get it hands down ;) ... or maybe I just pose my questions too early ... :o

---


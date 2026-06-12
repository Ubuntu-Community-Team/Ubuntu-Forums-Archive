---
title: "Locking screen via script with cron doesn't work"
date: 2009-02-27
forum: General Help
---

### Post by a person on 2009-02-27
I am trying to create a script that locks my screen based on if a file exists on a sama share.  This script works fine when executed in a terminal, though doesn't when ran through cron.  Anyone know how to get this to work?
```

#!/bin/bash

filel="/home/zach/.gvfs/public on nas/.screensavercontrol-l"
filed="/home/zach/.gvfs/public on nas/.screensavercontrol-d"
filep="/home/zach/.gvfs/public on nas/.screensavercontrol-p"
if [ -e "$filel" ]
	then
		/usr/bin/gnome-screensaver-command -l
elif [ -e "$filed" ]
	then
		/usr/bin/gnome-screensaver-command -d
elif [ -e "$filep" ]
	then
		/usr/bin/gnome-screensaver-command -p
fi

```

Output from a tail -1 /var/syslog:
```

Feb 27 04:54:01 Blue /USR/SBIN/CRON[19404]: (zach) CMD (/home/zach/Scripts/screensavercontrol >/dev/null 2>&1 # JOB_ID_4)

```

---

### Post by a person on 2009-02-27
Solved.  Adding: export DISPLAY=:0.0 solved it.

---


---
title: "Bash script to automatically restart a crashed process"
date: 2009-03-08
forum: General Help
---

### Post by samgreen on 2009-03-08
Hey guys, I'm trying to write a bash script that checks to see if a process is running. If the process is not running, it should restart this server. Similar to init.d, but this is NOT a system process. This code never outputs anything. 

```

#!/bin/bash
if [ -z `pidof -s samp02Xsvr` ]; then
    exec /home/samp/samp02Xsvr &
    echo "Restarted SA:MP Server."
fi
```
Once the script is fully functioning, the plan is to put it in crontab and run it every minute. I understand this is rather brute force, and probably the least elegant solution. I looked into Monit, but I was unable to determine how to make my server generate a pid file. I was therefore unable to write a Monit script to check this process as well.

---


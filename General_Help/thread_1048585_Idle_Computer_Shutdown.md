---
title: "Idle Computer Shutdown"
date: 2009-01-23
forum: General Help
---

### Post by felipefoz on 2009-01-23
I'm having a problem in my house. My brothers keep leaving the computer on, for a long period. I was thinking about creating a script to check if there is any user logged (usually they log off), and then shutdown.
I thought something with cron, every x minutes to check, and the command who

something like
if who returns any user logged, do nothing else shutdown
I want some help with the scripts as I am not expert with it

Thanks in advance....

---

### Post by unutbu on 2009-01-23
Hello felipefoz, save this in a file called autoshutdown.sh
```

gksu gedit /usr/local/sbin/autoshutdown.sh
```
```

#!/bin/sh
num_users=$(who --count | awk 'BEGIN{ FS="=" } /users/{print $2}')
if [ "$num_users" = 0 ]; then
    # Wait for 5 minutes
    sleep 300 
    # Check that there is still no one logged in
    num_users=$(who --count | awk 'BEGIN{ FS="=" } /users/{print $2}')
    if [ "$num_users" = 0 ]; then
	shutdown -h now
    fi
fi
```

Make it executable:
```

sudo chmod 755 /usr/local/sbin/autoshutdown.sh
```

Now edit /etc/crontab:
```

gksu gedit /etc/crontab
```
```

*/10   *     * 	 *   *   root /usr/local/sbin/autoshutdown.sh

```
This crontab entry will make the machine run autoshutdown.sh every 10 minutes.

Note that it is good to check that there is no one logged in twice. Otherwise, when you initially turn on the machine, if you are unlucky and the cron job executes before you get to log in, the machine will shutdown immediately. The reason why the script waits for 5 minutes and checks again is to prevent that from happening.

---

### Post by felipefoz on 2009-01-24
Thanks for the quick reply, very quick by the way. I'll try it out tonight, and then I'll tell you the results. I've thought about this problem in turning on, and the script would run right after it, shutting down, but you came across with a good solution.
See ya, and thanks again...

---

### Post by felipefoz on 2009-02-12
I put this script in test, but it is not working by me!
is there anything I could've done wrong?
cheers

---


---
title: "[SOLVED] cron job failing in midstream!"
date: 2008-12-21
forum: Desktop Environments
---

### Post by Barriehie on 2008-12-21
Hello Everyone,  I've got a bash script that's called twice a week to back my machine up.  It never worked in 7.10 and after upgrading to 8.04 it worked until something was upgraded... :(  I've been messing around with it and this AM I got it to run, somewhat.  The script started and then stopped after putting about 108 Mbytes into the backup file.  The backup file size isn't consistent either.  I'm confused / don't know on this one.

Anyone have any idea or how to enable some sort of logging so I can determine the why?

Here's the line from my /etc/crontab

```

0 6 * * 0 root exec > /home/barrie/Desktop/backedup; /bin/bash < /backmeup.sh

```Many Thanks,
Barrie

Okay, now I've tried it like this:
```

0 6 * * 0 root exec > /home/barrie/Desktop/backedup; /backmeup.sh

```and still the same thing.  The backedup file on the desktop is showing the last file as being /bin/perform_recipe.

Then I tried replacing /backmeup.sh with the line in the script that is the tar command; same behavior.

Edit: The cron log just indicates that the job was started.

---

### Post by hictio on 2008-12-21
> **Barriehie said:**
> Hello Everyone,  I've got a bash script that's called twice a week to back my machine up.  It never worked in 7.10 and after upgrading to 8.04 it worked until something was upgraded... :(  I've been messing around with it and this AM I got it to run, somewhat.  The script started and then stopped after putting about 108 Mbytes into the backup file.  The backup file size isn't consistent either.  I'm confused / don't know on this one.

Anyone have any idea or how to enable some sort of logging so I can determine the why?

Here's the line from my /etc/crontab

```

0 6 * * 0 root exec > /home/barrie/Desktop/backedup; /bin/bash < /backmeup.sh

```Many Thanks,
Barrie

Okay, now I've tried it like this:
```

0 6 * * 0 root exec > /home/barrie/Desktop/backedup; /backmeup.sh

```and still the same thing.  The backedup file on the desktop is showing the last file as being /bin/perform_recipe.

Then I tried replacing /backmeup.sh with the line in the script that is the tar command; same behavior.

Edit: The cron log just indicates that the job was started.

You can log the output of the execution, adding this:

```

0 6 * * 0 root exec > /home/barrie/Desktop/backedup; /backmeup.sh 1>/tmp/_cron.debug.1.log 2>/tmp/_cron.debug.2.log

```

This will rewrite the output files every time the cron gets executed.
If may I suggest something, I would put all the crontab commands on a shell script, and call that shell script from a crontab.

Like this:

```

#!/bin/sh

## backuScript.sh
## This script executes backedup and then backmeup.sh

/full/path/to/interpreter/used/to/execute/backedup /home/barrie/Desktop/backedup
/bin/sh /backmeup.sh 

```

And then, add a crontab like this:

```

 0 6 * * 0 root /bin/sh /full/path/to/backuScript.sh

```

---

### Post by Barriehie on 2008-12-21
Thank you hictio, I will implement the logging scenario.  And yes I've got a shell script, /backmeup.sh that was being called from /etc/crontab.  It was working wonderfully until after Hardy upgraded something.  I will run it with the logging enable and see what surfaces.

Thank You,
Barrie

---

### Post by Barriehie on 2008-12-21
Got me???  I changed the /etc/crontab entry to:
```

37 12 * * 0 root /backmeup.sh 1>/home/barrie/Desktop/_cron.debug.1.log 2>/home/barrie/Desktop/_cron.debug.2.log

```and it worked.  That's the same as it was before except for the redirection of the log file.

Thank You hictio,
Barrie

---


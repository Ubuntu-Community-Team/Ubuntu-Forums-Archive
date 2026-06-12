---
title: "Alarm Clock Script Not Working w/ Cron"
date: 2009-03-06
forum: General Help
---

### Post by mcjilton on 2009-03-06
The following little script works perfect when I run it directly from a terminal but when I schedule it to be run only the first line of the script executes.  Here is the full script:

```
#!/bin/sh

# Set Master Volume
/usr/bin/amixer -c 0 sset Master,0 85% 

# Launch Radio Stream
/usr/bin/amarokapp -p http://azulweb.streamguys.com/kut1.m3u
```

It looks like no matter what I do, the amarok command just doesn't want to execute from cron.

Any thoughts?

---

### Post by heindsight on 2009-03-06
When a command runs under cron, it does not get the same environment variables as when you run it interactively. Very likely the problem is that the DISPLAY variable is not set, so amarokapp doesn't know which X display to connect to. Try adding a line like:
```
DISPLAY=:0
```
to your script, before you try to launch amarokapp.

Another possibility is that you made a mistake in setting up the crontab.
Could you post your crontab line here?

I'd recommend you install the mailx package:
```
sudo apt-get mailx
```
Then any output or error messages from commands run with cron will be emailed to your user email account, which you can check by running:
```
mail
```
in a terminal.

---

### Post by mcjilton on 2009-03-06
WORKED!! The DISPLAY was the missing piece of the puzzle. THANKS!

For reference, here is the update crontab entry I'm now using to kick of the same script:

```

 35 07  *  * 1-5    export DISPLAY=:0 && /home/josh/Scripts/alarm.sh > /home/josh/Scripts/cron_log
```


Thanks again

---


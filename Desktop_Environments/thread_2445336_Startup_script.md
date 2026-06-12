---
title: "Startup script"
date: 2020-06-12
forum: Desktop Environments
---

### Post by daithi_dearg on 2020-06-12
Hello,

I have a startup script in startup.script as follows:
sudo -- sh -c 'apt-get update; apt-get upgrade -y; apt-get dist-upgrade -y; apt-get autoremove -y; apt-get autoclean -y'

I was using this to apply updates on the restart.

I can run the script fine.

Tried adding it to crontab with entry:
@reboot /home/david/startup.script

Also tried adding this file in /etc/init
update.conf 
start on startup
task
exec /home/david/startup.script

Is there another way I should be doing this?

---

### Post by TheFu on 2020-06-12
a) no need to do both upgrade AND dist-upgrade. The "upgrade" is redundant.

b) never trust the PATH in scripts, especially with sudo. All apt-get should be **/usr/bin/apt-get**. It would be really easy to sneak in a change to your PATH so "my" version of apt-get is called, does what normal apt-get does, but also does some other things for me, as a bonus.

c) automatically patching can be dangerous. Every few years some package gets pushed that has a dependency mistake and either removes a critical package necessary for the purpose of the system or creates a non-booting system.  Consider this your warning.

I can only say what I do.  I patch weekly, Saturday mornings, when I'll have time to address any problems.  There are seldom issues, but when there are and I need 2 hrs to hunt down an answer or decide to restore from a backup (takes 30-45 min) and try again a week later, when I have some time.

BTW, when do you run backups?  Hopefully, just before any dist-upgrade patching.

As for autoremove and autoclean, I only need to run those every 2-4 weeks and not usually at the same time as patching.

I love automation, but there are limits.

The correct way to control system-level program runs and startups is to use a **Systemd Unit** file. [https://wiki.debian.org/systemd/Services](https://wiki.debian.org/systemd/Services) They run as root, so no need for sudo and in some environments, root isn't allowed to use sudo.

There are many different crontabs too. Most run as root, so sudo isn't needed/desired.  There's the /etc/crontab. There's the different tasks in /etc/cron.d/ which get symlinked into the cron.daily/.hourly/.monthly/.yearly directories. There's root's crontab, which can be accessed using **sudo crontab -e** and there's your crontab accessed w/ **crontab -e**.  The last 2 have a slightly different format than the /etc/crontab file.

IMHO.

---

### Post by daithi_dearg on 2020-06-26
Created file update.service in /etc/systemd/system/
```
# Contents of /etc/systemd/system/myservice.service
[Unit]
Description=My Service
After=network.target

[Service]
Type=simple
WorkingDirectory=/home/david
Restart=always
ExecStart=/home/david/startup.script

[Install]
WantedBy=multi-user.target
```

Have following:
```
david@david-N7x0WU:/etc/systemd/system$ systemctl status update.service
&#9679; update.service - My Service
     Loaded: loaded (/etc/systemd/system/update.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Thu 2020-06-25 09:11:18 IST; 24h ago
   Main PID: 1337 (code=exited, status=203/EXEC)

Jun 25 09:11:18 david-N7x0WU systemd[1]: update.service: Scheduled restart job, restart counter is at 4.
Jun 25 09:11:18 david-N7x0WU systemd[1]: Stopped My Service.
Jun 25 09:11:18 david-N7x0WU systemd[1]: Started My Service.
Jun 25 09:11:18 david-N7x0WU systemd[1]: update.service: Main process exited, code=exited, status=203/EXEC
Jun 25 09:11:18 david-N7x0WU systemd[1]: update.service: Failed with result 'exit-code'.
Jun 25 09:11:18 david-N7x0WU systemd[1]: update.service: Scheduled restart job, restart counter is at 5.
Jun 25 09:11:18 david-N7x0WU systemd[1]: Stopped My Service.
Jun 25 09:11:18 david-N7x0WU systemd[1]: update.service: Start request repeated too quickly.
Jun 25 09:11:18 david-N7x0WU systemd[1]: update.service: Failed with result 'exit-code'.
Jun 25 09:11:18 david-N7x0WU systemd[1]: Failed to start My Service.
```

Also looked in /var/log/syslog but see nothing of note

---

### Post by TheFu on 2020-06-26
NEVER, EVER, put a script that runs with root privilege in a normal user's control.  If that user account gets compromised, the entire system will be lost.  Move the script into /usr/local/sbin/.

Also, while not as important, using a HOME directory for input/output by the script is not the best choice.  I'd use /opt/{something unique}/ unless there was some excellent, secure, reason not to.

```
Restart=always
```
Will run the script over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over and over ....
I'm guessing that isn't really what you want. Looks like systemd saw 5 restarts and quit.

Shouldn't you look for myservice in the logs?

> c) automatically patching can be dangerous. Every few years some package gets pushed that has a dependency mistake and either removes a critical package necessary for the purpose of the system or creates a non-booting system. Consider this your warning.
Last weekend, all the kernels on my 20.04 system were removed due to a dependency failure somewhere in APT. I'll say it again, automatically running updates is dangerous.  To recover, I ended up wiping the system and restoring from overnight backups.

---

### Post by daithi_dearg on 2020-06-29
I'll take it that you have more experience and I'll stay away from automating this although if it breaks dependencies I'd argue that even if I'm to do it manually that can still happen.

I'll bow to your greater knowledge though.

Still getting an error:
```
david@david-N7x0WU:/etc/systemd/system$ sudo systemctl status update.service
&#9679; update.service - My Service
     Loaded: loaded (/etc/systemd/system/update.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Mon 2020-06-29 13:18:59 IST; 12s ago
    Process: 6950 ExecStart=/usr/local/sbin/startup.script (code=exited, status=203/EXEC)
   Main PID: 6950 (code=exited, status=203/EXEC)

Jun 29 13:18:59 david-N7x0WU systemd[1]: Started My Service.
Jun 29 13:18:59 david-N7x0WU systemd[6950]: update.service: Failed to execute command: Exec format error
Jun 29 13:18:59 david-N7x0WU systemd[6950]: update.service: Failed at step EXEC spawning /usr/local/sbin/startup.script: Exec format error
Jun 29 13:18:59 david-N7x0WU systemd[1]: update.service: Main process exited, code=exited, status=203/EXEC
Jun 29 13:18:59 david-N7x0WU systemd[1]: update.service: Failed with result 'exit-code'.
```

Change in config file:
```
# Contents of /etc/systemd/system/myservice.service
[Unit]
Description=My Service
After=network.target

[Service]
Type=simple
WorkingDirectory=/home/david
#Restart=always
ExecStart=/usr/local/sbin/startup.script

[Install]
WantedBy=multi-user.target
```

I'm happy to leave this be and do these updates manually.

---

### Post by TheFu on 2020-06-29
> **daithi_dearg said:**
>  
I'm happy to leave this be and do these updates manually.

I have no issue using a script, provided everything is logged. I have a script that pauses for my "ok" between each system while the prior system's results are displayed on the screen.

The issue is with that script being run automatically when we aren't paying attention.  If I don't have time to patch my systems on Saturday morning, I'll wait until Sunday morning.  If I'm traveling over a weekend, I'll either skip the patching that weekend completely or do it a few days before or a few days after returning.  Regardless, it has to be started by me.

I like automation.
Backups are automatic.
All sorts of data gets pulled from the internet, automatically every few hours, for my use.
But patching systems is manual.

I don't recall seeing the script or the permissions on the script file. The 'exec format error' could be any of some really simple things - like not having the execute permission bit set or editing it using a non-Unix editor and getting CRLF added to the end-of-lines.

If **sudo -- sh -c 'apt-get update; apt-get upgrade -y; apt-get dist-upgrade -y; apt-get autoremove -y; apt-get autoclean -y'** was the start of the script, I'd rewrite it as :
```
#!/bin/bash
DATE=$(date "+%F")
APTG=/usr/bin/apt-get
TEE=/usr/bin/tee
LOG="$HOME/logs/weekly.patches-$DATE"
/bin/mkdir  "$HOME/logs"

echo "INFO: Patching $HOSTNAME "  | $TEE -a $LOG

$APTG update    | $TEE -a $LOG
$APTG dist-upgrade | $TEE -a $LOG
$APTG autoremove | $TEE -a $LOG
$APTG autoclean  | $TEE -a $LOG

```
Since the sudo is outside the script, I'd put it in ~/bin/.  Run it as **sudo ~/bin/my-patching**  

Should clean up the log files or they'll be left over.  I'd keep no more than 2 weeks of them.
**/usr/bin/find "$HOME/logs" -iname weekly\* -mtime +14 -delete**
That should work. Add that to the bottom of the script or put into some other daily-cleanup script that gets run just before backups. No need to backup extra junk, right?

There are lots of other things to be added/changed.  I'm not really happy assuming that HOME is set. In older versions of cron, that was not true.

A few key ideas for all scripts.
[LIST]
[*]NEVER trust the PATH environment variable. Use full paths to all programs, so the wrong command doesn't get run.
[*]Automatically answering any questions can lead to disaster.
[*]NEVER assume any PWD. Create the script so it can be run from anywhere on the system. Same for log output.
[*]Include simple logging.
[*]Clean up the logs.
[*]If commands are likely to fail, catch the failure and handle it.
[*]If a command can only be safely run on/from 1 system, do some simple checking that the system hostname or all dependent programs are available at the beginning.
[*]Carefully consider whether having sudo inside a script is a good idea. Who will enter the password and 2nd factor auth data?
[/LIST]

---

### Post by daithi_dearg on 2020-07-05
Thanks for the details in the script.

I'm not sure why I had run this in the home directory initially and I have changed my logs to go into /var/log

I have the script located in the /bin directory

I have added this as a Service under systemctl and looks to be working fine.

Thanks

---

### Post by TheFu on 2020-07-05
> **daithi_dearg said:**
> Thanks for the details in the script.

Happy to help.

> **daithi_dearg said:**
> 
I'm not sure why I had run this in the home directory initially and I have changed my logs to go into /var/log

Excellent.

> **daithi_dearg said:**
> I have the script located in the /bin directory

There are reasons NOT to put your stuff there.  You should put the script where I said it should go above - but go ahead and learn from this mistake. 
> **daithi_dearg said:**
> I have added this as a Service under systemctl and looks to be working fine.

It has been so long, I don't remember the purpose anymore.  Ah ... automatic patches.  I've said my peace. I hope you never have a broken system.

---


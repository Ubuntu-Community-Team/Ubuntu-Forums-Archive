---
title: "Cron installed but broken?"
date: 2008-12-31
forum: General Help
---

### Post by Scruffynerf on 2008-12-31
I've been running ubuntu for a while now, and have only just started to explore the benefits of the Cron scheduler.

Except, I have a problem. It's installed, but doesn't appear to work at all.

I'm currently trying to use GAdmin-Rsync (hereafter abbreviated to GR) to set up a regular backup script to an external hard drive, and GR is reporting that:

```
Error: The time schedule server "cron(d)" does not seem to be running.
```

Checked synaptic, and cron is installed.

Checked Services, which shows 'anacron' as starting and enabled, and 'atd' as disabled. No mention of cron itself.

Checking the Bootup Manager, cron appears to be activee (lightbulb is on) and Activate is checked on teh Summary tab, on the Services tab cron is reporting
```
Single User: K11
Run Level 2: S89
Run Level 3: S89
Run Level 4: S89
Run Level 5: S89
Reboot: ---
Halt: ---
```

Now, the command "crontab -l" reports "No crontab for <user>", whilst the command "service cron status" reports that cron is running.

And now I'm confused. can anyone offer any advice?

Thanks in advance,

---

### Post by eBoxNet on 2008-12-31
its installed but the cron deamon is down,try :


```
/etc/init.d/cron start
```

you can read more here : [http://www.cyberciti.biz/faq/howto-linux-unix-start-restart-cron/](http://www.cyberciti.biz/faq/howto-linux-unix-start-restart-cron/)

---

### Post by drs305 on 2008-12-31
To check if cron is running, you can use the command:
```

ps -U root -u root u | grep "cron"

```

You should get results for cron and anacron. 

If cron is running and "crontab -l" doesn't show anything scheduled, there is nothing scheduled for the user. You can also check "sudo crontab -l" for root's cron jobs..

---

### Post by Scruffynerf on 2008-12-31
> **eBoxNet said:**
> its installed but the cron deamon is down,try :


```
/etc/init.d/cron start
```

you can read more here : [http://www.cyberciti.biz/faq/howto-linux-unix-start-restart-cron/](http://www.cyberciti.biz/faq/howto-linux-unix-start-restart-cron/)

Ok, read through the link, however it doesn't seem to help me. 

The command ```
/etc/init.d/cron start
``` gives a result of "[fail]", but doesn't indicate why. Prefacing the command with sudo also fails.

----

> **drs305 said:**
> To check if cron is running, you can use the command:
```

ps -u root | grep "cron"

```

You should get results for cron and anacron. 

If cron is running and "crontab -l" doesn't show anything scheduled, there is nothing scheduled for the user. You can also check "sudo crontab -l" for root's cron jobs..

That command gives an odd result: "19936 ?        00:00:00 cron"

System monitor also doesn't show a process with that number as a pid.

---

### Post by drs305 on 2008-12-31
> **Scruffynerf said:**
> 
That command gives an odd result: "19936 ?        00:00:00 cron"
System monitor also doesn't show a process with that number as a pid.

That is a normal result - 19936 is the PID number and the time reference is correct. System Monitor doesn't show cron running on my computer but all my cron jobs run without problem.

There is a gui app for establishing cron jobs if you would like to try that method. It is called 'gnome-schedule'.

---

### Post by dblslash on 2009-01-04
I have the same problem with cron. I also tried the gui gnome-schedule, but it didn't work. I put the full path name of a working script in the command field to have it run every minute, but it never did.

---

### Post by tatt on 2009-04-30
BUMP...


I have this exact same problem.....

I am using gadmin to schedule some backups but when i try to save the job i get the following error from gadmin.

Error: The time schedule server "cron(d)" does not seem to be running.


chris@ubuntu:~$ /etc/init.d/cron start
 * Starting periodic command scheduler crond                             [fail] 
chris@ubuntu:~$ sudo /etc/init.d/cron start
[sudo] password for chris: 
 * Starting periodic command scheduler crond                             [fail] 
chris@ubuntu:~$ ps -u root | grep "cron"
 2575 ?        00:00:00 cron
 3968 ?        00:00:00 cron
chris@ubuntu:~$ crontab -l
no crontab for chris
chris@ubuntu:~$ sudo crontab -l
no crontab for root
chris@ubuntu:~$

---

### Post by mikepixie on 2009-07-15
Bump
I have the same problem using GAdmin Rsync. I  can easily schedule using crontab -e or gnome-schedule but GAdmin Rsync still gives the error:
```
Error: The time schedule server "cron(d)" does not seem to be running.
```

Its not a huge problem because I can set up an rsync another way. However it would be convenient for people in the office with less technical knowledge. 

Thanks in advance for any help :guitar:

---

### Post by vega77 on 2009-08-25
Hi 

I found out how to get around it.
The gadmin package is version 0.1 if you use synaptic to install.

I tried to download the source code and compile it.
Then i got no error.
The version i'm using now is 0.1.4

[http://mange.dynalias.org/linux/gadmin-rsync/gadmin-rsync-0.1.4.tar.gz](http://mange.dynalias.org/linux/gadmin-rsync/gadmin-rsync-0.1.4.tar.gz)

---


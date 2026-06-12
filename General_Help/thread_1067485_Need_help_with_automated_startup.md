---
title: "Need help with automated startup"
date: 2009-02-11
forum: General Help
---

### Post by laffinet on 2009-02-11
I'm after some help with automating start up of my computer.

Here's what I'm trying to do: I'd like my computer to shut down at certain times of the day and start up a few hours later. 
Times need to be different depending on the weekday.

So, I thought the following will do:

1. combination of ```
shutdown -h now
``` & ```
/sys/class/rtc/rtc0/wakealarm
``` in different scripts for the different days

2. schedule cron jobs that call up those scripts

I'm alright with the cron jobs, but I've never written a script.

Can someone give me a simple noob explanation on what I need to do to write a script and make it usable ?

I suppose in the script I don't need much more than:
```
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo `date '+%s' -d '+ 3 hours'` > /sys/class/rtc/rtc0/wakealarm
cat /sys/class/rtc/rtc0/wakealarm
shutdown -h now

```

Or am I going about it the wrong way completely ?

---

### Post by punx45 on 2009-02-11
nevermind   :oops:

---

### Post by laffinet on 2009-02-11
That's why I'm using

```
/sys/class/rtc/rtc0/wakealarm

```

to write a startup time to the bios ;)

---

### Post by punx45 on 2009-02-11
check out this entry in the mythtv wiki, looks like what you are trying to accomplish.   looks like you arer on the right track.

[http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)

---

### Post by laffinet on 2009-02-11
Thanks, that's where I got most of my information from. 

What I need help with is the actual scripts.

As I said, I've never written a script, so have no idea how to do it (format, permissions, whatever).

I'm guessing I just whack those lines of code into a file, but what then ? How do I turn it into a script ?

Sorry if this is a stupid question, as mentioned, not exactly an expert on scripts...

---

### Post by laffinet on 2009-02-12
Okay, done a bit of digging, from what I can tell this is what I have to do:

Create empty file with following lines:

```
#!/bin/sh
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo `date '+%s' -d '+ 3 hours'` > /sys/class/rtc/rtc0/wakealarm
cat /sys/class/rtc/rtc0/wakealarm
shutdown -h now
# end script

```

Save file: usefulname.sh

```
sudo chmod +x /path/to/usefulname.sh

```

Setup cron job(s) to execute script(s) at certain times.

Bob's your uncle.

---

### Post by punx45 on 2009-02-12
you got it.   a shell script is just a list of commands.   the #! /bin/sh tells the script which shell to use to execute it.   thats it!

---

### Post by laffinet on 2009-02-12
Just one more question:

where do I save this script so it can be executed with just the script name from anywhere (ie I don't have to be in the folder the script is saved in).

At the moment I have to put 

```
bash /path/to/usefulname.sh
```

to run the script, when I want it to be just

[HTML]usefulname[/HTML]

---

### Post by e1mer on 2009-02-12
It looks like the time is Zulu time (GMT).

I think this because it says so when you
```
cat /sys/class/rtc/rtc0/time
```

Maybe that has to do with how you install tho.

---

### Post by punx45 on 2009-02-12
do 
```
echo $PATH
```
and put the script in one of the listed directories.   not sure which is the "proper" one, probably one of the /usr/local ones.

not sure if that is recommended though.

you can also add new directories to $PATH

[http://kb.iu.edu/data/acar.html](http://kb.iu.edu/data/acar.html)

---

### Post by laffinet on 2009-02-12
Thanks. Will try that.

---

### Post by laffinet on 2009-02-13
Aaaargh, I can't get the combination of the script and the cronjob to work.

Here's the script (which I called shutdowntest.sh):

```
#!/bin/sh
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo `date '+%s' -d '+ 3 minutes'` > /sys/class/rtc/rtc0/wakealarm
cat /sys/class/rtc/rtc0/wakealarm
shutdown -h now
# end script
```

which when started via

```
sudo shutdowntest.sh
```

works fine from anywhere (because I put a symbolic link in /usr/sbin)

I then edited crontab via

```
sudo crontab -e
```

and added the following line

```
45 9 * * * shutdowntest.sh
```

When 9:45 came around, nothing happened. I tried all sorts of things, added the full path in front of "shutdowntest.sh", added sudo, nothing worked.
I've tried the same crontab line replacing "shutdowntest.sh" with "/sbin/shutdown -h now" and it worked fine, so I know my crontab line is ok. 

So in summary I believe my script is ok, the crontab line is ok, but together the two don't want to play. 

Any ideas someone ???

---

### Post by punx45 on 2009-02-14
got this from the cron man page

BUGS
       Although cron requires that each entry in a crontab end in a newline character, neither the crontab command nor the cron daemon will detect this error. Instead, the  crontab
       will appear to load normally. However, the command will never run. The best choice is to ensure that your crontab has a blank line at the end.

---

### Post by laffinet on 2009-02-14
Tried this, doesn't change a thing.

As mentioned, I don't think it's the crontab (or the scripts), it seems the two don't want to play together.

For example, at 11.03am I create the following crontab (notice the blank line at the end):

```
# m h  dom mon dow   command
5 11 * * * shutdowntest.sh


```

shutdowntest:

```
#!/bin/sh
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo `date '+%s' -d '+ 3 minutes'` > /sys/class/rtc/rtc0/wakealarm
cat /sys/class/rtc/rtc0/wakealarm
shutdown -h now
# end script
```

11.05am, nothing happens.

On the other hand:

```
sudo crontab -l
# m h  dom mon dow   command
10 11 * * * /sbin/shutdown -h now


```

shuts down at 11.10am just fine.

No idea what's going on...

---

### Post by punx45 on 2009-02-15
> **laffinet said:**
> 
When 9:45 came around, nothing happened. I tried all sorts of things, added the full path in front of "shutdowntest.sh", added sudo, nothing worked.


was the full path to the actual script, or the link?

also, check the log to see if you are getting any error messages from cron

```

sudo grep CRON /var/log/syslog
```

---

### Post by laffinet on 2009-02-15
Path was to the actual script.

Here's the crontab line when I tried last:

```
# m h  dom mon dow   command
47 11 * * * /home/laffi/shutdownscripts/shutdowntest.sh


```


That's the path to the actual script, not the link.

ls -l in that directory (to check permissions, which I believe are correct)

```
laffi@laffi-mythbox:~/shutdownscripts$ ls -l
-rwxrwxrwx 1 laffi laffi 179 2009-02-12 17:06 shutdowntest.sh

```

I also checked the log. Only entries I could find in relation to the script are these, which don't tell me anything.

```
Feb 15 11:41:01 laffi-mythbox /USR/SBIN/CRON[6903]: (root) CMD (/home/laffi/shutdownscripts/shutdowntest.sh)
Feb 15 11:43:01 laffi-mythbox /USR/SBIN/CRON[6967]: (root) CMD (/home/laffi/shutdownscripts/shutdowntest.sh)
Feb 15 11:47:01 laffi-mythbox /USR/SBIN/CRON[7037]: (root) CMD (/home/laffi/shutdownscripts/shutdowntest.sh)

```

---

### Post by punx45 on 2009-02-15
well im running out of ideas.. heres one more though:

i noticed that your cron didnt declare any system variables, so it may be defaulting to bash as a shell and you are declaring sh in your script.   see here for more info.

[http://blog.spikesource.com/crontab.htm](http://blog.spikesource.com/crontab.htm)

---

### Post by heindsight on 2009-02-15
When cron runs a job the environment for that job isn't the same as when you run it by hand. In particular, you can't assume that the PATH is the same as when you run the script by hand. I suggest you put the full paths to all commands (except shell builtins) in your script and see if that helps.

---

### Post by laffinet on 2009-02-15
OK, I know the path for shhutdown is

/sbin/shutdown

Where are the others located. I think echo is

/usr/bin/echo

Not sure though.

cat ?

---

### Post by punx45 on 2009-02-15
as in?
```
 /sbin/shutdown -h 
```

---

### Post by heindsight on 2009-02-15
echo is a shell builtin command so you don't need a path for that. cat should be at /bin/cat date should be at /bin/date. You can use which to obtain the full path for any command.

For example:
```
which cat
``` should print ```
/bin/cat
```

---

### Post by laffinet on 2009-02-15
Thank you. I will change shutdowntest.sh to:

```
#!/bin/sh
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo `*/bin/date* '+%s' -d '+ 3 minutes'` > /sys/class/rtc/rtc0/wakealarm
*/bin/cat* /sys/class/rtc/rtc0/wakealarm
*/sbin/shutdown* -h now
# end script
```

and try again later today. Fingers crossed.

---

### Post by laffinet on 2009-02-16
Success at last !

The absolute path for all commands in the script finally did it.

Thanks a lot heindsight and punx45 !

---


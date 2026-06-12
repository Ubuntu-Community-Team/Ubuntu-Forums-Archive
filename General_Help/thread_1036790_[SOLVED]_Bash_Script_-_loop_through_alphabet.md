---
title: "[SOLVED] Bash Script - loop through alphabet"
date: 2009-01-11
forum: General Help
---

### Post by Kissell on 2009-01-11
I wrote a script that I have a cronjob for, the script goes out and checks the temperature of any possible hard disks in the server and e-mails me a warning if the temperature of any of the drives exceeds a warning threshold, and it goes as far as shuting off the server if the threshold continues to climb into being extremely excessive and nobody did anything about it after being notified.

The script works great, but I'm not happy with its repetition.  I repeat the code for every letter of the alphabet, that way it can test for a drive "/dev/sdt" just in case you have one, then it'll check it's temperature.  

Can someone help me out with how to make this code shorter?  I have tried to create a "for" loop that would step through the alphabet, but I haven't been able to get it to work.

> 
#! /bin/sh
#
warning_trigger=0;
warning_threshold=45;
error_trigger=0;
error_threshold=55;

if test $(ls /dev |grep sda |wc -l) != 0; then
  [ $(hddtemp -n /dev/sda) -ge $warning_threshold ] && warning_trigger=1 || :
  [ $(hddtemp -n /dev/sda) -ge $error_threshold ] && error_trigger=1 || :
fi

if test $(ls /dev |grep sdb |wc -l) != 0; then
  [ $(hddtemp -n /dev/sdb) -ge $warning_threshold ] && warning_trigger=1 || :
  [ $(hddtemp -n /dev/sdb) -ge $error_threshold ] && error_trigger=1 || :
fi

if test $(ls /dev |grep sdc |wc -l) != 0; then
  [ $(hddtemp -n /dev/sdc) -ge $warning_threshold ] && warning_trigger=1 || :
  [ $(hddtemp -n /dev/sdc) -ge $error_threshold ] && error_trigger=1 || :
fi

if test $(ls /dev |grep sdd |wc -l) != 0; then
  [ $(hddtemp -n /dev/sdd) -ge $warning_threshold ] && warning_trigger=1 || :
  [ $(hddtemp -n /dev/sdd) -ge $error_threshold ] && error_trigger=1 || :
fi



---

### Post by ajcham on 2009-01-11
> **Kissell said:**
> I have tried to create a "for" loop that would step through the alphabet, but I haven't been able to get it to work.

How were you constructing the loop? It should just be:
```
for x in {a..z}
do
if test $(ls /dev |grep sd$x |wc -l) != 0; then
[ $(hddtemp -n /dev/sd$x) -ge $warning_threshold ] && warning_trigger=1 || :
[ $(hddtemp -n /dev/sd$x) -ge $error_threshold ] && error_trigger=1 || :
fi
done

```

---

### Post by Kissell on 2009-01-11
Yeah, I think I was constructing the loop correctly, but I'm having trouble utilizing the variable inside the loop.

Like, how do I use that variable to replace the "a" in sda with subsequent sequential letters of the alphabet?

> 
if test $(ls /dev |grep sda |wc -l) != 0; then
  [ $(hddtemp -n /dev/sda) -ge $warning_threshold ] && warning_trigger=1 || :
  [ $(hddtemp -n /dev/sda) -ge $error_threshold ] && error_trigger=1 || :
fi


---

### Post by Kissell on 2009-01-11
Oops, i didn't see your code, let me go try that.

---

### Post by ajcham on 2009-01-11
> **Kissell said:**
> Oops, i didn't see your code, let me go try that.

No worries - I didn't originally demonstrate using the variable, but edited the code afterwards. You probably saw my first reply.

A point of note - if I'm seeing this correctly, in the event of a hot disk the script will tell you that one of your disks is in danger of overheating, but won't report which one.  Is that right?

---

### Post by Kissell on 2009-01-11
Awesome, that totally works...  although, it is exactly as I thought I had tried to code it the first time, before I tried a bunch of things that didn't work...  I must have fat fingered the original attempt.

Anyway, here's the code if anyone else will find it useful.  It uses hddtemp and crontab to check drive temperatures...  I find this very useful because my new server/desktop has a noisy fan-wall, so I'm unplugging some of the fans which I consider to be overkill on cooling...  but I want to be notified if temperatures get too high, and shut off the system if they get excessive while I'm away...  I want things to be quiet, but don't want to cause damage...  

There may be a better way of doing this, but I didn't know how, so I made it up as I went.

> 
#! /bin/sh
#
# requires: sudo apt-get install hddtemp
#
# This script is intended to be run in crontab, to perform actions if temperatures of hard disks exceed thresholds.
#

warning_trigger=0;
warning_threshold=45;
error_trigger=0;
error_threshold=60;

for x in {a..z}
do
if test $(ls /dev |grep sd$x |wc -l) != 0; then
[ $(hddtemp -n /dev/sd$x) -ge $warning_threshold ] && warning_trigger=1 || :
[ $(hddtemp -n /dev/sd$x) -ge $error_threshold ] && error_trigger=1 || :
fi
done

if test $warning_trigger = 1; then
  echo "WARNING: A hard disk exceeds temperature threshold!"
  echo "WARNING: Notifying Administrator!"
  /usr/bin/smtpmail-drive-temp.py
fi

if test $error_trigger = 1; then
  echo "ERROR: A hard disk exceeds maximum temperature!"
  echo "ERROR: SHUTTING DOWN!!!"
  /sbin/shutdown -h 0
fi


---

### Post by ajcham on 2009-01-11
> **Me]A point of note - if I'm seeing this correctly, in the event of a hot disk the script will tell you that one of your disks is in danger of overheating, but won't report which one.[/QUOTE]

[QUOTE=Kissell said:**
> I find this very useful because my new server/desktop has a noisy fan-wall, so I'm unplugging some of the fans which I consider to be overkill on cooling...  but I want to be notified if temperatures get too high, and shut off the system if they get excessive while I'm away...  I want things to be quiet, but don't want to cause damage...

Okay, fair enough - for your purposes it doesn't matter which disk in particular is in trouble, you just want to know to plug the fans back in.

Also, you should use the CODE tag instead of the QUOTE tag in your last post.

---

### Post by Smjork on 2009-01-11
I'm not a Bash guru but ...

a. As stated the script does not tell which drive is causing problems.
b. What if there's not only one drive causing problems ?

It would be much usefull to just insert the notification message inside the if .. fi loop, something like 

if bla-bla-bla
   .....
   .....
   echo "Warning: Drive /dev/sd$x went nuts" | sendmail [email]johndoe@thedomain.net[/email]
fi 

# Warnings being already given it is now time to take measures
if bla-bla-bla
   echo "Shutting down the junkyard"
   shutdown -h
fi

... and of course you may customize the message to suit your needs, let's say what exact temperature was the drive reporting.

---

### Post by Kissell on 2009-01-11
Yeah, I thought about incorporating "which" drive died...  but I'd really already had that problem solved, because I have the program call a python script that send me an e-mail when any drive is too hot, and in that e-mail it sends a copy of the temperatures of all the drives.

I prefer to use python scripts to send e-mail, because they're just so easy to use...  you just use them...  and can use existing ones as templates.  I've found that many unix/linux servers don't have sendmail or any MTA setup on them, and using the python script works on pretty much any Ubuntu box.  I find it easy, when I reformat a server and the only reason it needs e-mail is to send me trouble notifications, that python scripts are easiest for me.

Anyway, here's the one I'm using with this

> 
#!/usr/bin/python
import sys
import smtplib
import commands

################################
# Edit the following variables #
################################
smtpserver = 'smtp.host.net:25' # SMTP server
username = 'user'               # for SMTP AUTH, set SMTP username here
password = 'password'           # for SMTP AUTH, set SMTP password here
sender = 'server@office.net'
to = 'your@email.address.com'
################################

# Setup email
subject = 'WARNING: DISK TEMPERATURE VERY HIGH'
server = 'SERVER-NAME'
hddtemp = commands.getoutput('sudo hddtemp -w /dev/sd*')

text = "YOU ARE RECEIVING THIS MESSAGE BECAUSE A DISK HAS EXCEEDED THE WARNING THRESHOLD TEMPERATURE.\n\n"

text = "A HARD DISK HAS EXCEEDED THE THRESHOLD.\n\n"

text = text + "--------------------------------------------------------------------------------\n"
text = text + "BEGINNING OF DIAGNOSTIC INFORMATION\n"
text = text + "--------------------------------------------------------------------------------\n\n"

text = text + "HOST: " + server + "\n\n\n"

text = text + "--------------------------------------------------------------------------------\n"
text = text + "Output from the command: 'sudo hddtemp -w /dev/sd*' \n\n" + hddtemp + "\n\n"
text = text + "--------------------------------------------------------------------------------\n\n\n"

text = text + "--------------------------------------------------------------------------------\n\n\n"
text = text + "END OF DIAGNOSTIC INFORMATION\n"
text = text + "--------------------------------------------------------------------------------\n\n"
headers = "From: %s\r\nTo: %s\r\nSubject: %s\r\n\r\n" % (sender, to, subject)

message = headers + text

#Send the email
session = smtplib.SMTP(smtpserver)
session.login(username, password)
session.sendmail(sender, to, message)
session.quit()



---

### Post by Kissell on 2009-01-14
so weird, now the script isn't working anymore...  

i copied and pasted it from what I posted in this forum thread, and it still doesn't work...  

I put a "echo $x" inside the for loop, and it's outputting "{a..z}" instead of "a" like it should... 

this is what it was doing to me the first time I wrote this...  then later it started working when I wrote it the second time...  but I know it's the same code this time, because I was able to copy what I posted in this thread...

so any ideas why the for loop isn't working anymore to step through the alphabet?  and now it's just outputting "{a..z}"???

---

### Post by Kissell on 2009-01-14
okay, if I type in "bash myscript.sh" then it runs just fine...  but if i just try to run it via "./myscript.sh" then it doesn't work... 

my shell is set to /bin/bash...  so why can i no longer run this script without typing "bash" first?

Just curious, obviously I have a workaround, but I've seen this many times before.

---

### Post by Slim Odds on 2009-01-14
> **Kissell said:**
> okay, if I type in "bash myscript.sh" then it runs just fine...  but if i just try to run it via "./myscript.sh" then it doesn't work... 

my shell is set to /bin/bash...  so why can i no longer run this script without typing "bash" first?

Just curious, obviously I have a workaround, but I've seen this many times before.

/bin/sh and /bin/bash will behave differently.

/bin/sh is more primitive.

You have ```
!# /bin/sh
``` at the start of your script. So when you run it directly (i.e., with ./myscript.sh), it runs under /bin/sh and not /bin/bash. You might want to change it to ```
!# /bin/bash
```The {a..z} construction is ONLY in bash and not sh.

P.S. You might want to check into the Advance Bash Scripting guide. [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---


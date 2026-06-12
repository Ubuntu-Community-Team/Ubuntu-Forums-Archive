---
title: "&quot;For&quot; loop not working in Crontab"
date: 2009-05-14
forum: General Help
---

### Post by ogen on 2009-05-14
I have a slight problem when running a script with crontab. The other parts of it run normally but, the main part of it that consists of the loop does not seem to run at all while the smaller "id" loop works.

This is a script that I wrote for a computer lab running Edubuntu that is supposed to run every 1:00 AM:
```
#!/bin/bash
DATE=$(date +%F_%R)
PASS=$(mkpasswd user)
PRIVS=adm,dialout,fax,cdrom,floppy,tape,audio,dip,plugdev,scanner,fuse

for IDSEQ in `seq -w 01 29`; do
	id user$IDSEQ &> /dev/null
done
if [ $? -eq 0 ]; then
	for UVAR in `seq -w 01 29`; do
		pkill -u user$UVAR
		sleep 5
		userdel -r user$UVAR &> /dev/null
		rm -r /tmp/*user$UVAR* &> /dev/null
		useradd -p $PASS -d /home/user$UVAR -k /home/syeung/Desktop/skelbase/ -s /bin/bash -m -G $PRIVS user$UVAR
		touch /home/user$UVAR/Touch$DATE
		chown user$UVAR:user$UVAR /media/user$UVAR &> /dev/null
	done
	echo "Replace on $DATE successful." >> /home/syeung/Desktop/rlog.txt
	fi
else
	echo "Replace on $DATE failed." >> /home/syeung/Desktop/rlog.txt
fi

```

In the rlog.txt, I find that that the script keeps saying that the script ran successfully (due to that line that I could have wrote better...) but, the users are not deleted and re-added and the touch file is not added. If I run this script manually (not on cron), then I get perfect results in logging out the user and recreating it.

Anyone have any clues as to why the for loop doesn't work?

---

### Post by ogen on 2009-05-18
Bump.

---

### Post by ghostdog74 on 2009-05-19
you have extra "fi". use set -x in your side next time for debugging

---

### Post by geirha on 2009-05-19
The problem is probably that it can't find all the commands you are using. cron runs the script with a very limited set of environment variables. If you make a cronjob like this
```
* * * * * /usr/bin/env >/tmp/env.txt
```
Wait for it to run once, then look at /tmp/env.txt. You'll see that PATH=/usr/bin:/bin.

Furthermore:
```
$ which pkill
/usr/bin/pkill
$ which sleep
/bin/sleep
$ which userdel
/usr/sbin/userdel

```
userdel is found in /usr/sbin/, which is not in PATH, so you'll have to go through all the commands you run, and either set your own PATH at the start of the script, or supply the absolute path to all the commands

---

### Post by geirha on 2009-05-19
Also
```

for IDSEQ in `seq -w 01 29`; do
	id user$IDSEQ &> /dev/null
done
if [ $? -eq 0 ]; then

```

Is the idea with that code to check if user01 to user29 exist? If so, it doesn't do that. It only checks if user29 exist ...

Perhaps try with something like
```

if /usr/bin/getent passwd user0{0..9} user{10..29} >/dev/null; then
   # recreate the users
else
   # something's wrong
fi

```
The getent command will only return 0 if all the 29 users exist in /etc/passwd

---

### Post by ogen on 2009-05-19
**@ghostdog74**
Actually... That was from me messing up in cutting and pasting the code... That was not part of the actual script.

This is what I revised it slightly to:
```
#!/bin/bash
DATE=$(date +%F_%R)
PASS=$(mkpasswd user)
PRIVS=adm,dialout,fax,cdrom,floppy,tape,audio,dip,plugdev,scanner,fuse

for IDSEQ in `seq -w 01 29`; do
        id user$IDSEQ &> /dev/null
done
if [ $? -eq 0 ]; then
        for UVAR in `seq -w 01 01`; do
                pkill -u user$UVAR
                sleep 5
		userdel -r user$UVAR &> /dev/null
		rm -r /tmp/*user$UVAR* &> /dev/null
		useradd -p $PASS -d /home/user$UVAR -k /home/syeung/Desktop/skelbase/ -s /bin/bash -m -G $PRIVS user$UVAR
		touch /home/user$UVAR/Touch$DATE
		chown user$UVAR:user$UVAR /media/user$UVAR &> /dev/null
	done
	if [ $? -eq 0 ]; then
		echo "Replace on $DATE successful." >> /home/syeung/Desktop/rlog.txt
	else
		echo "Replace on $DATE failed (Loop did not run)." >> /home/syeung/Desktop/rlog.txt
	fi
else
	echo "Replace on $DATE failed (ID check failed)." >> /home/syeung/Desktop/rlog.txt
fi
```

**@geirha**
I think the problem it might be what you said about the path.

This is what I got from the /usr/bin/env:
```
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
```
Not to sure on this but, doesn't that mean that the path does look in /usr/sbin?

EDIT: And I just checked... Yes, you are right about the id loop, I'll have to change that along with the other loops.
EDIT2: Gonna change the userdel command to /usr/sbin/userdel. Hope that works out better.

---

### Post by geirha on 2009-05-19
> **ogen said:**
> 
This is what I got from the /usr/bin/env:
```
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
```

That looks like the default PATH you have in a regular interactive bash shell. If that was the output of env run by cron, then your crontab must have a line adding those extra paths to the PATH environment. Does your crontab have a line like this?
```
PATH = /usr/local/sbin:/usr/local/bin:...
```

---

### Post by ogen on 2009-05-19
Ye, actually it does. In /etc/crontab, it contains the same line for the PATH.

---

### Post by geirha on 2009-05-19
Ah, it does so in my /etc/crontab too. I usually use the crontab command to set cronjobs, and that uses a different crontab file which does not have variables set from the default configuration.

Well, I don't see any apparent errors that should cause the script to not run properly. I think the best bet is to (temporarily) remove all the redirects to /dev/null in the script, and then redirect the output of the whole script to a file. Hopefully there'll be a useful error message in there somewhere. Preferably one that will make us slap our heads and shout, "Of course!" ;)

```
0 1 * * * root /path/to/script >/tmp/script-output.log 2>&1
```

You'll need to redirect stdout and stderr seperately, since the command is run with /bin/dash, which does not understand &>.

Another option, which I would recommend you do anyway, is to install the [mailx](apt:mailx) package. After that package is installed, cron will send you a system mail if the script produces any output. You read such mails by running the "mail" command.

---

### Post by ogen on 2009-05-21
Changing the commands to /usr/sbin/[COMMAND] didn't seem to work...

Gonna try to redirect the stuff like you said and post up the results tomorrow (Can't really run cron whenever I want to because the computers are in constant use and I'm busy a lot of the time with other stuff).

---

### Post by ogen on 2009-05-22
Hmm...

```
user01:x:1128:1128::/home/user01:/bin/bash
userdel: unable to lock password file
rm: cannot remove `/tmp/*user01*': No such file or directory
useradd: user user01 exists
touch: cannot touch `/home/user01/Touch2009-05-22_01:00': Permission denied
chown: changing ownership of `/media/user01': Operation not permitted
user01:x:1128:1128::/home/user01:/bin/bash
Replace on 2009-05-22_01:00 successful.

```

So... Should I be blame not using sudo/root?

EDIT: Ah... That was the problem. Not being root...

/facepalm

---


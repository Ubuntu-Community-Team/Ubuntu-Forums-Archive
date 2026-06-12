---
title: "BacupPC install fails"
date: 2006-08-30
forum: Desktop Environments
---

### Post by vrtisworks on 2006-08-30
I tried downloading BackupPC with Adept.  It appears to download ok, then starts the install process.  Unfortunately, that just stalls.  The Percent complete is 0% and it doesn't move.

I clicked on Details, and it shows an install screen that looks like it is waiting for a response (OK?).

Any ideas on what is going on, or if there is another way to install it?

Thanks.

Nick

---

### Post by ahood on 2006-09-15
same problem. When I install backuppc, I get the following error

'Subprocess post-installation script returned error exit status 1'

:-(

---

### Post by artinla on 2006-09-17
Same thing here, can someone help with this?

Every time that I run apt:

> 
art@fettbauch:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up backuppc (2.1.2-2ubuntu5) ...
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
 * Starting backuppc... 2006-09-17 21:18:24 $Conf{SendmailPath} = '/usr/sbin/sendmail' is not a valid executable program
invoke-rc.d: initscript backuppc, action "start" failed.
dpkg: error processing backuppc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 backuppc
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have tried:

sudo apt-get remove --purge backuppc
sudo apt-get install backuppc
and
sudo apt-get install --reinstall backuppc

the error still occurs.

---

### Post by artinla on 2006-09-18
It sucks that threads get pushed off of the front page within an hour.  I think it is time for the moderators to think about adding some subforums.  This is ridiculous.  Ubuntu support used to be very good, and I have helped as many as have helped me... but lately I can't even BEG for an answer to any real problem.   Sad.

---

### Post by lamego on 2006-09-18
artinla,
Go into /var/lib/dpkg/info .
There should be an backuppc.postint file, delete it.
You should now be able to remove and reinstall the backuppc .

---

### Post by artinla on 2006-09-18
I deleted the file that you recommended, removed and purged backuppc and reinstalled.  Same exact error.

Thanks anyway.

Art

---

### Post by pyrokenx on 2006-09-23
Edit /var/lib/dpkg/info/backuppc.prerm

change 
```

if [ -x "/etc/init.d/backuppc" ]; then
        if [ -x "`which invoke-rc.d 2>/dev/null`" ]; then
                invoke-rc.d backuppc stop || exit $?
        else
                /etc/init.d/backuppc stop || exit $?
        fi
fi

```

to ...

```

if [ -x "/etc/init.d/backuppc" ]; then
        if [ -x "`which invoke-rc.d 2>/dev/null`" ]; then
                invoke-rc.d backuppc stop || true
        else
                /etc/init.d/backuppc stop || exit $?
        fi
fi

```

The difference is changing the first **'exit $?'** to **'true'**


Should now be able to remove.

---

### Post by ahood on 2006-09-23
I received this error too. After manually installing backuppc and not getting it quite functional, I realized that backuppc installed with apt-get is installed okay. 


_The Problem:_
The problem (I think) is that backuppc won't start because sendmail isn't configured....

> 
Starting backuppc... 2006-09-17 21:18:24 $Conf{SendmailPath} = '/usr/sbin/sendmail' is not a valid executable program



_Fix:_
I got backuppc to start by editing the /etc/backuppc/config.pl file and commented out, i.e., put a hash (#) in front, the line 

$Conf{SendmailPath} = '/usr/sbin/sendmail';

*Note: Edit the above file with the 'sudo nano /etc/backuppc/config.pl' command.*

_Test:_
Execute the command below to test that backuppc will run.

> 
sudo /etc/init.d/backuppc start


A message should appear stating that it is starting.....[ok]

Hope this helps.

Al

---

### Post by artinla on 2006-09-23
Thanks, that did it.

Art

---


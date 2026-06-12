---
title: "can't get gvfs-mount to work within cron job"
date: 2012-02-21
forum: Desktop Environments
---

### Post by graham.s on 2012-02-21
Background to this is that a task I want to complete requires mounting (gvfs) of remote samba share on a NAS. I want to automate the mount as part of the task but it doesn't work when cron runs it at a scheduled time.

I can manually run the gvfs command in a terminal as in
```
~$ gvfs-mount smb://nas-name/sharename
```and it works fine.
In Gnome Scheduler, I've created a task using the same command. It appears in the scheduler listing and
```
~$ crontab -l
```lists it as (with example time slot)
```
00 21 * * * gvfs-mount smb://nas-name/sharename # JOB_ID_14
```If I use Gnome Scheduler's "Run Selected Task" it works fine, but if I schedule for a couple of minutes hence and wait, nothing happens.
Yet /var/log/syslog states
```
Feb 21 21:00:01 DEEPTHOUGHT CRON[8470]: (graham) CMD (gvfs-mount smb://nas-name/sharename # JOB_ID_14)
```Any help with why it won't run a scheduled gratefully appreciated.

---

### Post by Cheesehead on 2012-02-21
First, cron doesn't have your environment variables, and only a limited set of default paths to look for a command.

So try full paths: /usr/bin/gvfs-mount

Second, crontabs work best for complex tasks if you move all that complexity into a script, and use the crontab simply as a trigger. Put all your commands, debugging, error-catching, logging, and exit codes into a script.```
10 10 * * * /path/to/my/script
```

Any script triggered by cron should also have full paths, and not require environment variables that cron cannot access.```
# This is /path/to/my/script, which does stuff

share_drive="smb://nas-name/sharename"
/usr/bin/gvfs-mount $share_drive
# do stuff
/usr/bin/gvfs-mount -u $share_drive
exit 0
```

---

### Post by efflandt on 2012-02-22
It is always a good habit to include a shebang line as the first line of a script to tell the system what to use to interpret it.  Although, the default is currently sh (dash), it does not hurt to specify it:

```
#!/bin/sh
```

Or if you use something bash specific not included in dash, you would need to specify it:

```
#!/bin/bash
```

Note that whitespace is optional between **#!** and the interpreter.

---

### Post by graham.s on 2012-03-04
Thanks guys, but that's not the fix

I agree with the scripting stuff, but gvfs-mount not working there so was trying to cut out other possible causes of problems and just run the command through cron. It's not a path problem - i've tried running gvfs-mount with full path specified as in
```
/usr/bin/gvfs-mount smb://nas-name/sharename
```I suspect it could be environment variables (thanks for the hint) - in particular the fact that the share is passworded and I'm guessing my environment knows my share password (as stored under Password & Encryption Keys). Might this be the cause? If so, how can I get cron to use my password given that gvfs-mount doesn't take a password option?

As ever, help most gratefully received

---

### Post by Cheesehead on 2012-03-17
I suggest using smbclient instead of gvfs-mount. It can use passwords.
Try 'man smbclient' to see if it does what you need.

---

### Post by graham.s on 2012-03-20
> I suggest using smbclient instead of gvfs-mount

Methinks you're right. Tried a solution using that - works fine. Thanks muchly for the suggested workaround.

---

### Post by apjjr on 2012-04-08
> **graham.s said:**
> Tried a solution using that - works fine.

Graham.S, I am having a similar problem with gvfs-mount.  Could you please post your mount solution using smbclient.

Many thanks,
Alex

---

### Post by graham.s on 2012-04-14
Hi Alex

Basically, I used smbclient as a workaround. I originally wanted to use grsync as my method of backup but I can't work out how to set it up to work between the smbclient client connection and the local machine. Hence, I adopted a workaround which connects to the share and then use tar to backup the files. I use a credentials file for authenticating the connection so the code is

```
smbclient //servername/sharefolder --authentication-file=/home/myusername/pathtofile/credentialsfile
tar c backup.tar
```

cheers
Graham

---

### Post by apjjr on 2012-04-16
> **graham.s said:**
> 
```
smbclient //servername/sharefolder --authentication-file=/home/myusername/pathtofile/credentialsfile
tar c backup.tar
```


Graham,
I take it that in your example, sharefolder is copied into the tar file named backup.tar on the local computer,  effectively pulling the backup data to the backup server.
I have my clients pushing their backup data to my backup server.
I guess I could create a tar file on the client and use the smbclient put command to copy to the backup server.
Now, that I've said it, I think that will work.  I could also do the following to push a backup of indivual files:
```
smbclient -N //servername/sharefolder -c 'recurse; cd my_dir_on_servershare; mput *;'
```
Although it would be nice just to run rsync to do incremental backups instead of full backups.  I'll have to look into the rsync man pages to see if it can connct to an smb share, although I don't think it can.
I could also go back to having root use smbmount to do the backup, which is what I used to do, but I liked the idea of having the user connect themself with gvfs-mount.
I need to backup Windows and Linux clients.  Amazingly, the Windows clients are not giving me the trouble here.
Thanks for the suggestion,
Alex

---


---
title: "Crontab | Root | Shell Script"
date: 2009-02-26
forum: General Help
---

### Post by ethos84 on 2009-02-26
Hi guys

Bit confused here... 

Trying to run this shell script:

#!/bin/bash
tar -cvzf /home/administrator/www.tgz /var/www
mount -t cifs //server/company /mnt/remotebackup -o username=administrator,password=xxx,domain=xxx
cp /home/administrator/www.tgz /mnt/remotebackup/
umount /mnt/remotebackup

It works fine if I sudo ./backup.sh but if I don't sudo I get " mount: only root can do that" and "cp: cannot create regular file `/mnt/remotebackup/www.tgz`: Permission denied"

I'm guessing I need to use the root account's crontab, so I sudo crontab -e and add the entry to run this script:

30 19 * * * /home/administrator/backup.sh

But it doesn't work...

How do I set it up so the script has full sudo when running with crontab?

Thanks in advance.

---

### Post by DagMan on 2009-02-26
you can add the script to the sudoers file so it will run using sudo without needing to type the password, then put it in your user's cron.

```
sudo su
EDITOR=nano visudo
```
then add to the part where it says 'user privelege specifications'
```
<your username>  ALL=NOPASSWD: <full path to script>
```so it will end up looking like this in that section, using 'ethos' as the user
```
# User privilege specification
root	ALL=(ALL) ALL
ethos  ALL=NOPASSWD: /home/administrator/backup.sh
```

then you'd have to change your cron to your user and have it use sudo.
```
su ethos
crontab -e
```then add sudo
```
30 19 * * * sudo /home/administrator/backup.sh
```

More on sudoers file [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by Lars Stokholm on 2009-02-26
One possibility is to put the script in /etc/cron.hourly, cron.daily, cron.weekly or cron.monthly.

Also, from /etc/crontab:> # /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

---

### Post by ethos84 on 2009-02-26
Thanks guys :)

DagMan, the user account is actually administrator (just running the intranet so no need for additional users).

I've added:
administrator  ALL=NOPASSWD: /home/administrator/backup.sh

Then crontab -e as administrator and added the lines.

I scheduled it for a couple minutes and it still didn't run... I will schedule it for tonight and see what happens.

Thanks for the input.

---

### Post by unutbu on 2009-02-26
Here is yet another alternative:
```

gksu gedit /etc/crontab
```

Add this:```

#min hr    day   mon dow user command
30   19    *     *   *   root /home/administrator/backup.sh
```

This runs backup.sh as root, avoiding the need to edit /etc/sudoers.

---

### Post by ethos84 on 2009-02-26
I get:

(gksu:5771): Gtk-WARNING **: cannot open display:

If I try and run that command (freshly install gksu).

I've tried sudo in front and also from root, same thing.

---

### Post by unutbu on 2009-02-26
I'm not sure what's going on with gksu -- are you ssh'ing to a server perhaps?

If so, try 
```

sudo nano /etc/crontab
```

---

### Post by ethos84 on 2009-02-26
I was ssh'ing :)

Ok, so i've added that line to etc/crontab and it does the same thing. It starts but stops at a certain point (when the access denied starts). 

I'm assuming even though it's in /etc/crontab as root, somehow it isn't being run as root.... 

The plot thickens!

---

### Post by unutbu on 2009-02-26
This is probably the line that is failing:
```

mount -t cifs //server/company /mnt/remotebackup -o username=administrator,password=xxx,domain=xxx

```
I'm not sure why this line fails, but here is something you might want to try:

Go to [https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide) and follow the guide (2/3 of the way down) on "Automatically Mounting the Shares". The guide will show you how to move your username/password to /etc/smbcredentials.  Follow the guide's instructions on "Registering Our Shares" too. If you don't want the samba share to be mounted at boot, be sure to use the "noauto" (rather than "auto") option:

```
//server/company     /mnt/remote        cifs   [COLOR="Red"]noauto[/COLOR],credentials=/etc/smbcredentials,workgroup=XXX,gid=smb,uid=1000,file_mode=770,dir_mode=770,rw       0       0
```

By editing /etc/fstab, you will be able to mount the Samba share using the command
```

mount -t cifs /mnt/remotebackup
```

Maybe cron will work with this simpler mount command.

---

### Post by DagMan on 2009-02-26
Another thing to consider is that if you run the script at the shell without using cron, and it has ouput to the terminal, then this is something that can cause a crontab command to fail, so if there's output it needs to be redirected to a file or to /dev/null by putting at the end, using /dev/null as the example :it
```
sudo /path/to/command >/dev/null 2>&1
```

I didn't notice it before, but your tar command has the v paramater asking for verbose output, so its likely not to work unless you either remove that, the v, or direct output as shown above putting this at the end...  >/dev/null 2>&1

so like this
```
30 19 * * * sudo /home/administrator/backup.sh >/dev/null 2>&1
```

---


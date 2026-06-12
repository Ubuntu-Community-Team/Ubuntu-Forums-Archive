---
title: "Reccommend a backup program"
date: 2006-07-18
forum: Desktop Environments
---

### Post by mwdowns on 2006-07-18
Hello all.

I'm looking for a nice little backup progam that I can set up to run daily.  I don't need anything heavy duty.  I just want to back up a couple of folders (like my mozilla folder and my mozilla-thunderbird folder, for example) that I need whenever I do a reinstall.  I keep copies of these folders on a Storage partition, so bascially what I need the program to do is make a copy of a particular folder from my /home partiton onto my /Storage partion.  It doesn't need to be compressed or anything; just a copy of the folder.

Is there something out there to do this that you can reccommend?

Thanks.

---

### Post by cstudent on 2006-07-18
I use rsync and crontab to backup files to my server machine. You can learn more on each by using the man pages. Enter the following commands from a terminal window. (Applications menu>>Accessories>>Terminal)

```

man rsync

```
```

man crontab

```

This is bash script I wrote for backing up my Evolution folder and using rsync to send it to my server. I have my server drive mounted, so it's like passing it to another folder.

```

#!/bin/bash

## Evolution backup script

## Copy backup log to previous log
cp $HOME/Logs/evolution_bkup.log $HOME/Logs/evolution_bkup.log_prev
rm $HOME/Logs/evolution_bkup.log

## Start backup routine
echo "Starting backup of Evolution files" >> $HOME/Logs/evolution_bkup.log
echo " " >> $HOME/Logs/evolution_bkup.log
date >> $HOME/Logs/evolution_bkup.log
echo " " >> $HOME/Logs/evolution_bkup.log
echo " " >> $HOME/Logs/evolution_bkup.log

## Shutdown servers that can block files
echo "Shutting down services that can block files" >> $HOME/Logs/evolution_bkup.log
gconftool-2 --shutdown
evolution --force-shutdown

## Remove old backup file
echo "Removing old backup file" >> $HOME/Logs/evolution_bkup.log
echo " " >> $HOME/Logs/evolution_bkup.log
rm $HOME/Backups/evolution-backup.tar.gz

## Backup up files & log changes
tar -cvzf $HOME/Backups/evolution-backup.tar.gz \
	$HOME/.evolution $HOME/.gconf/apps/evolution $HOME/.gnome2_private/Evolution \
	>> $HOME/Logs/evolution_bkup.log
echo " " >> $HOME/Logs/evolution_bkup.log
echo "Backup completed" >> $HOME/Logs/evolution_bkup.log
date >> $HOME/Logs/evolution_bkup.log
echo " " >> $HOME/Logs/evolution_bkup.log

## Copy backup to server
echo "Copy backup to server" >> $HOME/Logs/evolution_bkup.log
echo " " >> $HOME/Logs/evolution_bkup.log
rsync -avr $HOME/Backups/evolution-backup.tar.gz /media/FileServer/Backups/ >> $HOME/Logs/evolution_bkup.log
echo " " >> $HOME/Logs/evolution_bkup.log

## Restart services
echo "Restarting gconftool-2" >> $HOME/Logs/evolution_bkup.log
gconftool-2 --spawn
echo "Backup routine done!" >> $HOME/Logs/evolution_bkup.log
## End backup script

```

You can probably use some of the code in it to build a bash script for your folders. Hope this is of some help to you.

cstudent

---

### Post by Thund3rstruck on 2006-07-18
The industry standard is tar, it can compress and archive your data

```

tar -zcvf mybackup.tar.gz /home/*
mv mybackup.tar.gz /media/storage

```

---

### Post by John.Michael.Kane on 2006-07-18
This may help [**[COLOR="Blue"]A simple Linux backup method[/COLOR]**]("http://www.desktoplinux.com/articles/AT2280165098.html") . you may want to look into this [**[COLOR="Red"]Scheduling Backup Jobs using at and crontab[/COLOR]**]("http://www.debianhelp.co.uk/schedulejobs.htm").

---

### Post by yopnono on 2006-07-18
Other one is sbackup easy and it has a GUI.

---

### Post by jordilin on 2006-07-18
You can use the very easy to use "Simple Backup". Go to synaptic and search for sbackup. It has two frontends in System->Administration-> Simple backup Config and Simple Backup Restore. It does incremental backups of whatever you want. Very nice soft, which if I'm not wrong was developed specifically for Ubuntu in the last year Google's Summer of Code.

---

### Post by cstudent on 2006-07-18
I experimented with Sbackup about six months ago. It was nice having a GUI to setup a backup. The one drawback for me was it keeps adding files to the backup directory. There was no way to tell it to only keep X many. So the backup directory kept growing and growing. I had to remember to go in periodically and clean it manually. 



cstudent

---


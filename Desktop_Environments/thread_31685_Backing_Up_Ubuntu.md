---
title: "Backing Up Ubuntu"
date: 2005-05-04
forum: Desktop Environments
---

### Post by KrazyPenguin on 2005-05-04
Just wondering what program is best for Backing-Up Ubuntu so it does it automatically.

When I was using Mepis, I had Konserve set up so it would back up my system, and then I could just burn it to a cdrom or dvd.

From my own notes:
> 
Directories to backup:
/home of course holds all the files of each user 
/etc holds all of the configuration information 
/usr/local normally holds any extra programs added since install 
/opt is also commonly used by applications to install files 
/var holds all data of a variable nature 
/root belongs to the root user and has essential customizations 
/boot has all the files for booting the system and boot .conf files 
 
Directoried NOT to backup:
/proc --- should never be backed up. It is not a real-file system, but rather a virtualized view of the running kernel and environment. It includes files such as /proc/kcore, which is a virtual view of the entire running memory. Backing these up only wastes resources. 
/dev --- contains the file representations of your hardware devices. If you are planning to restore to a blank system, then you can back up /dev. However, if you are planning to restore to an installed Linux base, then backing up /dev will not be necessary. 

Thanks ;-)

---

### Post by deception on 2005-05-04
I would also be interested in this  :smile:

---

### Post by KrazyPenguin on 2005-05-04
I did a search but couldn't find anything on these forums.

I can't believe this question hasn't been asked before, and it doesn't seem Ubuntu has a tool included to do this.

I know what I want to back-up, but I need an easy, fast, good way to do it with Ubuntu.

---

### Post by deception on 2005-05-04
I'll do some in-depth googling for you sir  :-P

Edit: 

[http://www.setcolor.de/sc_scripts/](http://www.setcolor.de/sc_scripts/)
(for networks) [http://www.bacula.org/](http://www.bacula.org/)

---

### Post by deception on 2005-05-04
This is also something I found, on the gnome cvs: 

[http://cvs.gnome.org/viewcvs/gnome-backup/](http://cvs.gnome.org/viewcvs/gnome-backup/)

---

### Post by shakin on 2005-05-04
You can install Konserve using Synaptic. May as well keep using what you're used to.

For remote backups of my important server files I have a server-side shell script that creates datestamped tgz archives of important files (and stops mysql before tgzing the database). Then I have a script on my backup server that rsyncs the file over to me. In some cases I just use rsync to keep one server in sync with the other, so only the changes are downloaded, while for things like the database I prefer to have an archive so I can roll back to any date.

server script:
```

#!/bin/bash
# creates a backup of the mysql database running at /var/lib/mysql

# get current datestamp
DATESTAMP="`date '+%d%m%Y'`"

# change to working directory
cd /var/lib

# stop mysql
/etc/init.d/mysql stop

# tar the /var/lib/mysql directory
tar -zcf /home/backup/mysql/mysql-${DATESTAMP}.tgz mysql/

# start mysql
/etc/init.d/mysql start

```

Download script on my backup server:
```

#!/bin/bash
# download backup archives from live server

# setup datestamp
DATESTAMP="`date '+%d%m%Y'`"

#backup live db
cd /home/backup/mysql/
rsync -v -u -a -z --rsh=ssh backups@mydomain.com:/home/backup/mysql/mysql-${DATESTAMP}.tgz .

```

---

### Post by KrazyPenguin on 2005-05-04
K thanks.

I wasn't sure I could use Konserve with Gnome since it is a KDE program.

Ok I'll give it a shot.

THanks ;-)

---

### Post by tread on 2005-05-04
Well, I don't have code for you, but I do have a suggestion: 

1. Write a script to backup the folders you need, and make an iso image of them with the name you want.
2. Add that to cron.
3. Burn them whenever you have time :)

I'll try to put together some scripts if I get time, though I guess you are likely to find scripts on the net to do the backup. You'll just have to add it to crontab.

---

### Post by Ronbo on 2005-05-04
I haven't tried it yet, but the Oreilly book "The Linux Cookbook" says to use a program called 'Mondo'.  From what I read it will allow you to create a bootable backup CD or DVD to restore your system or individual files.  I have been meaning to play around with it but haven't had the time.  I did apt-get the program though.

---

### Post by c_dog on 2005-05-04
[QUOTE=Ronbo]I haven't tried it yet, but the Oreilly book "The Linux Cookbook" says to use a program called 'Mondo'.  From what I read it will allow you to create a bootable backup CD or DVD to restore your system or individual files.  I have been meaning to play around with it but haven't had the time.  I did apt-get the program though.[/QUOTE]

The "Linux Cookbook" has a really nice section on using rsync scripts to do backups too. This book is highly recommended addtion to your library.

---

### Post by Gandalf on 2005-05-04
[QUOTE=shakin]You can install Konserve using Synaptic. May as well keep using what you're used to.

For remote backups of my important server files I have a server-side shell script that creates datestamped tgz archives of important files (and stops mysql before tgzing the database). Then I have a script on my backup server that rsyncs the file over to me. In some cases I just use rsync to keep one server in sync with the other, so only the changes are downloaded, while for things like the database I prefer to have an archive so I can roll back to any date.

server script:
```

#!/bin/bash
# creates a backup of the mysql database running at /var/lib/mysql

# get current datestamp
DATESTAMP="`date '+%d%m%Y'`"

# change to working directory
cd /var/lib

# stop mysql
/etc/init.d/mysql stop

# tar the /var/lib/mysql directory
tar -zcf /home/backup/mysql/mysql-${DATESTAMP}.tgz mysql/

# start mysql
/etc/init.d/mysql start

```

Download script on my backup server:
```

#!/bin/bash
# download backup archives from live server

# setup datestamp
DATESTAMP="`date '+%d%m%Y'`"

#backup live db
cd /home/backup/mysql/
rsync -v -u -a -z --rsh=ssh backups@mydomain.com:/home/backup/mysql/mysql-${DATESTAMP}.tgz .

```[/QUOTE]

i just have a question, why you use rsync since for that (to do it automatic) your user must be passwordless which mlake the system less secure unless you give it /dev/null as terminal, i personnaly don't do it like this, but i mount using nfs a directory (ONE DIRECTORY) using NFS which is used only to backup and then on the server i just CP the backup file, better no??

---

### Post by kiddo on 2005-05-04
I use rsync to backup to an external USB2 drive. I exchanged quite a few mails with "Chris", he did a translation of a german article about this on osnews. Here it is: 
[http://www.osnews.com/story.php?news_id=9681](http://www.osnews.com/story.php?news_id=9681)

---

### Post by 23meg on 2005-05-04
> 
I did a search but couldn't find anything on these forums.

I can't believe this question hasn't been asked before, and it doesn't seem Ubuntu has a tool included to do this.

i posted the exact same question yesterday; have a look: [http://www.ubuntuforums.org/showthread.php?t=31595](http://www.ubuntuforums.org/showthread.php?t=31595)

---


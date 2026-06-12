---
title: "back up solutions"
date: 2009-02-21
forum: General Help
---

### Post by DarinB on 2009-02-21
i have been floundering on back up solution.
i tried sback up back on feisty but it didn't work well.
i have an external usb hd i would like to backup my docs and some other basic files regularly with out having to think about it. any ideas????

---

### Post by yeleek on 2009-02-21
Hi,

Depends what you want...  I personally have two backup methods I'm using

1) Rsync - which keeps an up to date version of my /home backed up to an external usb.  Rsync is good because it will only copy the files that are new or changed since last backup.

2) I also use this [http://clonezilla.org/](http://clonezilla.org/) to backup my main partition (i.e. /).

I'd recommending giving rsync a try in a simple script that you run every 'x' or better schedule it with cron.

---

### Post by nbo10 on 2009-02-21
I use rsync to backup my home dir. 

I guess I should backup / also, but I haven't.

---

### Post by Lars Stokholm on 2009-02-21
I too use rsync. I wrote a script to fit my needs:```
#!/bin/sh
DESTINATION=/media/Backup
BACKUPDIR=${DESTINATION}/$(date +%Y-%m-%d)
LOGFILE=${HOME}/Desktop/rsync-backup-$(date +%Y-%m-%d).log
if [ -d ${DESTINATION} ]
then
  touch ${LOGFILE}
  sudo rsync --archive --backup --backup-dir=${BACKUPDIR} --delete --human-readable --log-file=${LOGFILE} --progress \
             --exclude "/home/*/.gvfs" \
             --exclude "/home/*/.mozilla/firefox/*/Cache" \
             --exclude "/home/*/.thumbnails" \
             /home /media/Backup
fi
```Backs up entire /home to /media/Backup excluding some bogus and unneeded crap. Deletes from the backup what was deleted from /home (but backs that up too, in case it was deleted from /home by accident). It might be of some inspiration to you.

---

### Post by DarinB on 2009-02-22
I like the idea of rsync but i want to only back up my doc and a few folders in my home folder.
I don't know how to write scripts, and i would like to send it to an external usb but i don't want it to take a long time. not sure maybe a full back up followed by incrementals not sure how the restore would be.

---

### Post by UbuntuNerd on 2009-02-22
check this guide maybe is what you looking for:
[http://my.opera.com/ubuntunerd1/blog/h-5]("http://my.opera.com/ubuntunerd1/blog/h-5")

---

### Post by DarinB on 2009-02-22
what percent of the original used hd space is necessary for a clone and can i clone to a usb hard drive and can i do incremental

---

### Post by Lars Stokholm on 2009-02-22
> **DarinB said:**
> I like the idea of rsync but i want to only back up my doc and a few folders in my home folder.
I don't know how to write scripts, and i would like to send it to an external usb but i don't want it to take a long time. not sure maybe a full back up followed by incrementals not sure how the restore would be.rsync works exactly that way. Full backup followed by incremental backups. I suggest starting with this for backup:```
rsync --archive /home/me/docs /home/me/music /backup
```
Have a look at the --delete option in man 1 rsync to see if that's for you. To restore your music files, you could do this:```
rsync --archive /backup/music /home/me
```

---

### Post by yeleek on 2009-02-23
> **DarinB said:**
> what percent of the original used hd space is necessary for a clone and can i clone to a usb hard drive and can i do incremental


Clonezilla site does explain re use of a USB hard disk - its how I'm using it.  As for space requirements - Clonezilla will let you backup the whole disk or a parition and does support compression.  As for how much disk space you need - as per dealing with any compression, depends on the data you are compressing.  Give it a try and see.

[http://clonezilla.org/clonezilla-live/](http://clonezilla.org/clonezilla-live/)

I don't understand why you'd want an incremental image.  Images are normally used in the IT industry to bring a system back to a base working state - you'd then as per suggestion use the rsync copy to pull your folders back from your external usb to your homedrive.

---

### Post by bhoth on 2009-02-23
Hi all,

I am looking to use rsync to backup one Ubuntu desktop to another, both on the same LAN in my home. I do not need to use SSH or any other encryption method.

I just need to do backups from one to the other.  It seems that every example I have found searching uses SSH and backups a remote location.

I want a simple example that just works.

Thanks,

---

### Post by Lars Stokholm on 2009-02-23
> **bhoth said:**
> I am looking to use rsync to backup one Ubuntu desktop to another, both on the same LAN in my home.What do you mean backup? To copy one home folder to another or to clone the entire disk? You should be able to do the first with a command similar to that of my previous example.

> **bhoth said:**
> I just need to do backups from one to the other.  It seems that every example I have found searching uses SSH and backups a remote location.Start an rsync daemon on one of the machines and connect to it from the other. See the man page for rsync for a further explanation.

---

### Post by bhoth on 2009-02-23
I am clear on how to use rsync on a stand alone box, but what I don't get is how to use it in daemon mode.

Here is what I have in a rsyncd.conf file

motd file = /etc/rsyncd.motd
log file = /var/log/rsyncd.log
pid file = /var/run/rsyncd.pid
lock file = /var/run/rsync.lock

[home]
   path = /home/bhoth
   comment = My Very Own Rsync Server
   uid = nobody
   gid = nobody
   read only = no
   list = yes
   auth users = bhoth
   secrets file = /etc/rsyncd.scrt

Does this look okay?

then from the other linux box, what do I type to connect to the linux box running the daemon?

say I have two boxes in my house one is 192.168.1.2 and the other is 192.168.1.3

Both of them have /home/bhoth/ directories. If I want to backup /home/bhoth on 192.168.1.3 to the other box with 192.168.1.2 what is the rsync command to type?

Thanks for your help!

---

### Post by Lars Stokholm on 2009-02-24
I have to be honest and say that I haven't tried, but it seems overly complicated to achieve what you could easily do by using ssh.

That being said, I guess you'd use something like:```
rsync --archive --delete 192.168.1.3::home /home
```
from 192.168.1.2. I'm afraid I have to leave further guidance to others, but in the mean time, have a look at 'man rsync'. Good luck.

---


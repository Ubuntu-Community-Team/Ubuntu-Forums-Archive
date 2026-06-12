---
title: "Synapse and NAS mount"
date: 2013-12-07
forum: Desktop Environments
---

### Post by massimo.cristofoli on 2013-12-07
Hi everyone.
I've installed Synapse for the first time, and I think I can't live without it nomore :)
The only problem I'm facing so far is that my mounted partitions in network NAS aren't indexed, so I can't use Synapse to search documents there.
THe partitions are mounted on startup via fstab using cifs.
Any hint?

Thanks
MIX

---

### Post by LewisTM on 2013-12-08
Hi there,
Synapse is awesome indeed. It uses the[FONT=Courier New] locate[/FONT] command to find files, which in turn depends on [FONT=Courier New]updatedb[/FONT] to index and update the database. What you need is to edit /etc/updatedb.conf (as root) to make changes to the indexing process in order to include you NAS.
First, make sure your NAS mount point does not fall under one of the PRUNEPATHS, and if so remove the directory entry.
Then, do the same for the PRUNEFS. For instance, if your NAS uses CIFS, you want to remove cifs from the PRUNEFS list.
Save the file and run
```
sudo updatedb
```
(Note: updatedb is scheduled daily in Ubuntu)

Cheers!

---

### Post by massimo.cristofoli on 2013-12-09
Hi **LewisTM**,
thanks for the infos. I will try your suggestion.
Side question. I get some errors/warnings during boot about the cifs mount, due to the fact the networking isn't alreay up and the NAS can't be reached so the OS can't mount the folders. By the way, after login the folders are there. Is it possible that updatedb tries to update the db during boot, so the folders aren't reachable? Or does it start working after login? Or maybe I can set a sort of delay?
Note that I haven't made any tests yet. Just asking.

Thanks
MIX

---

### Post by LewisTM on 2013-12-09
Don't worry about the networking error. It happens all the time since Network Manager is run after login. The successful connection triggers autmounting for all network drives in fstab.
As for the run time, it defaults to once per day, allowing a 5-minute delay (for booting). 
The settings are in /etc/anacrontab, the commands in /etc/cron.daily

---

### Post by massimo.cristofoli on 2013-12-09
Tested it. It works. Actualy, the access of documents on NAS is slower, not immediate like document on PC. Is it right? I thought that, since everything is indexed on the PC, retrieving data locally and remotely will take the same amount of time.

The PRUNEPATH includes /media, that is where Imount my NAS folders. By the way, is quite right to prune that path, since it's where USB pens, cd and so on will be mounted, and these are things that I don't want to track. I tried to change the mount point to /mnt, but than the folders aren't shown in nautilus under "Network".
Any hint about where to mount the NAs folders? A folder in my home could be a solution, but I find more "elegant" to have something like a /media path, that I don't really see in my personal folders.

Thanks again!
MIX

---

### Post by LewisTM on 2013-12-09
Indexing the filename won't cache the file contents on your hard drive, so it won't make access faster.
Starting from Ubuntu 12.10, hot-plugged media are mounted in /media/<yourname> instead of just /media
So a trick would be to list /media/<yourname> (and any other user) in PRUNEPATHS, but leave out /media per se. If your NAS is mounted under /media/<cifs-nas>, you should be home free.

Cheers!

---

### Post by massimo.cristofoli on 2013-12-10
Good to know.
So, issue resolved! Thanks LewisTM.

Just another "the more you know" question.
I have a single user system, so it's no big deal to add to PRUNE list "/media/my-name". In a multi user environment, how to set to prune all users media folders? Do I need to set all names ("/media/joe /media/jenny /media/so-and-so") or is there a more clever way?

---

### Post by LewisTM on 2013-12-10
I don't know of any clever way. I think it stems from the fact that we're just not supposed to mount anything in /media from fstab, it's reserved for hot-plugged devices. Although I will agree that being able to see the drive in the file manager is a plus for many users.

In theory, you're supposed to mount network drives somewhere out of the way (which CAN be indexed, provided its fs is not in PRUNEFS). If there are parts of the drive you want to use often, you create symlinks in your home directory, pointing to those directories. Another approach is to use Gigolo to autoconnect network locations at login, they will appear as shares on your desktop and file manager. No need for fstab then.

Cheers!

---


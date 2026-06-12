---
title: "Hard Drive Full - FIles in dir / are over 200GB"
date: 2009-02-19
forum: General Help
---

### Post by redfred on 2009-02-19
Hi,

New to Ubuntu...great stuff.

I have a 250GB drive. My Disk Usage Analyzer says:

Total filesystem is 215GB used but only 24GB in the home folder.

The other 190GB is in the / folder (which I assume is root?)

What do you think the problem may be? Or how do I delete these files?

Thanks in advance.

---

### Post by mikewu on 2009-02-19
I'm guessing that you made your partitions a bit too big.

run 
df -h 

That will show partition sizes and consumption. Post that back here.

---

### Post by heindsight on 2009-02-19
It would help if you could find out exactly where the space is being used.

Open a terminal and run:
```
sudo du -hx --max-depth=1 /
```
and post the output here.

---

### Post by redfred on 2009-02-19
Can do:

kieran@kieran-xeon:~$ sudo du -hx --max-depth=1 /
4.0K	/mnt
7.7M	/root
65M	/boot
0	/dev
du: cannot access `/home/kieran/.gvfs': Permission denied
4.7G	/home
8.0K	/media
208G	/var
7.1M	/sbin
16K	/lost+found
505M	/lib
84K	/tmp
200K	/srv
6.1M	/bin
4.0K	/initrd
4.0K	/opt
0	/sys
0	/proc
16M	/etc
2.8G	/usr
216G	/

It all seems to be in the Var folder. The properties of that folder include files that are unreadable? Have a look at the screenshot.

Thanks again fellas.

---

### Post by taurus on 2009-02-19
```
sudo du -h /var
```

---

### Post by heindsight on 2009-02-19
> **redfred said:**
> 
It all seems to be in the Var folder. The properties of that folder include files that are unreadable? Have a look at the screenshot.

Thanks again fellas.

Yes, many files under /var can only be read by root. One possible contributor to the problem could be your local repository of retrieved packages (your package managers automatically keep a copy of each .deb you install from the repositories) you can clean this out by doing
```
sudo apt-get clean
```
That should free up some space.

After apt-get clean, try doing ```
sudo du -h --max-depth=1 /var
``` to see how much space /var is using now.

If it's still very big, the problem may be in /var/log. I seem to recall recently reading something somewhere on the forums about a bug in Intrepid that causes some files in /var/log to get very big. So if your /var/log is taking up a lot of space you may want to have a look at [thread=853347]this thread[/thread] and [thread=984941]this thread[/thread], and delete some files under /var/log

---

### Post by Slim Odds on 2009-02-19
> **heindsight said:**
> If it's still very big, the problem may be in /var/log. I seem to recall recently reading something somewhere on the forums about a bug in Intrepid that causes some files in /var/log to get very big. So if your /var/log is taking up a lot of space you may want to have a look at [thread=853347]this thread[/thread] and [thread=984941]this thread[/thread], and delete some files under /var/log

When I install Ubuntu, even for desktop machines, I put /var and /tmp in their own partitions. That way, they never get out of hand.

---

### Post by redfred on 2009-02-20
Sorry for my newbieness here. I have had a long look at these posts and I am not having any success. I ran the: sudo du -h /var command to check the folder and I can't see where the files are. Everything in the var folder is less than 30MB and doesn't add up to 200GB. The log folders are only 15MB.

You can see that the last screenshot that in the VAR folder some of the files are unreadable. Even with the du -h command I can't see where the big files are.

Thanks again for the dig out.

---

### Post by heindsight on 2009-02-20
If that screenshot was made running nautilus as a normal user, then it is no surprise that it told you there are unreadable files, since many files under /var can only be read by root.

Also, since a normal user cannot read some files, running du (or looking at the directory properties in nautilus) won't tell you the real amount of space being used.

However, running ```
sudo du -h /var
``` should give you the same size for /var as running ```
sudo du -hx --max-depth=1 /
``` if that's not the case, then something very strange is happening. So run ```
sudo du -hx --max-depth=1 /
``` again just to make sure it's still reporting 208G used in /var and then post the output of ```
sudo du -h --max-depth=1 /var
``` here.

---

### Post by redfred on 2009-02-20
Making progress. That worked. It seems its my backup folder:

584K	/var/spool
208G	/var/backup
6.3M	/var/backups
308M	/var/lib
4.0K	/var/crash
2.4M	/var/tmp
320K	/var/run
4.0K	/var/local
15M	/var/log
4.0K	/var/mail
0	/var/lock
4.0K	/var/opt
48M	/var/cache
8.0K	/var/games
209G	/var

---

### Post by heindsight on 2009-02-20
OK, I assume you're using Simple Backup (as described here:[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite))?

I've never used it, so I'm not sure how it works, but perhaps you can tweak the backup configuration to use less space (perhaps by purging old backups), or backup to an external device (or maybe you could even just burn your backups to DVDs and delete them from the hard drive).

---

### Post by Tony Flury on 2009-02-20
> **heindsight said:**
> OK, I assume you're using Simple Backup (as described here:[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)?](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)?)
.


Corrected Link : [https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

---

### Post by heindsight on 2009-02-20
> **Tony Flury said:**
> Corrected Link : [https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

hehe, yes. thanks.

---

### Post by redfred on 2009-02-22
Ok I have a new problem - I cannot open the Simple backup config or restore. I get this:

Failed to run /usr/sbin/simple-backup-config as user root.

Unable to copy the user's Xauthorization file.

At this stage I am perfectly happy to uninstall simple backup as I can't do anything with the PC at the moment. Its completely full!

Thanks again for the help.

---

### Post by Slim Odds on 2009-02-22
> **redfred said:**
> 
At this stage I am perfectly happy to uninstall simple backup as I can't do anything with the PC at the moment. Its completely full!

There are a couple of things that you can do.

1) Boot into recovery mode and go delete some of those backups that are hogging all of your space.

2) Modify the reserved space on the ext2/3 partition to free up some space to that you can delete the backups that are hogging all of your space.

First one is the easiest.

Second one: ```
sudo tune2fs -m 1 /dev/{put your partition here}
```

---

### Post by redfred on 2009-02-23
Sorry I am probably ruining your day here. Its one after another. I have reboot to go into recovery mode and its stuck on a drive scan at 33.5%. Can I bypass this to get back in?

---


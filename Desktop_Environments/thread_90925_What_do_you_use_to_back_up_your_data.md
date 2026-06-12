---
title: "What do you use to back up your data?"
date: 2005-11-16
forum: Desktop Environments
---

### Post by megamania on 2005-11-16
I have two twin hard disks. The first one runs Ubuntu, and the second one is on a removable rack (i.e. IDE and not USB) and I use it as a backup device.

What I need is a program that makes a full mirror of my /home directory on the second hard disk:

- the first time I run it, it should simply copy all the files (which takes a lot of time)
- afterwards, it should delete on the backup disk the files that I deleted on the primary hard disk, add the new ones and replace the modified ones (thus taking only a few minutes a day)

I don't want / can't use incremental backup because I don't have enough disk space, and running a full backup of my data every day is not possible (it takes more than one hour!).

In windows, I used to do this very easily with xxcopy and ViceVersa Pro, but I still haven't found a solution on Linux (but I know it is my fault!).

I think my requirements are quite common, so I'd be happy to know what you're using to satisfy your backup needs. :-)

---

### Post by megamania on 2005-11-16
Well, before I make you waste your time replying to me, I thought I should tell you that I found on these forums that rSync is probably what I need.

Sorry for asking *before* searching...  :-!

---

### Post by shof2k on 2005-11-16
No problem....it's good using your own initiative.  You might also want to try DAR.  It's killer feataure is that you can 'slice' up your backups so fit a DVD or CD.

---

### Post by nocturn on 2005-11-16
I use Bacula ([www.bacula.org)](www.bacula.org)), but it is a complex system.

---

### Post by megamania on 2005-11-16
thank you shof2k and nocturn.

I'll check both apps, but I guess if I'm able to create a mirror with rsync I'll keep it simple and stick to that! I still have so many things to learn with Linux...  :)

Thanks again,
gianfranco

---

### Post by Original Brownster on 2005-11-16
I use rsync with anacron to do backups at regular intervals and it works a charm only it can be running whilst your doing something this way.
Probably better to create a script that runs as you shut down, I guess this is possible I just haven't got around to sorting it yet :-)

---

### Post by megamania on 2005-11-16
[QUOTE=Original Brownster]I use rsync with anacron to do backups at regular intervals and it works a charm only it can be running whilst your doing something this way.
Probably better to create a script that runs as you shut down, I guess this is possible I just haven't got around to sorting it yet :-)[/QUOTE]

Well, since I would backup to a removable disk in an Ide rack, it would be great if I could put in a cronjob (is that what it is called?) something like this:

----
if /backup is NOT mounted -> EXIT
backup script follows...
----

that would be just perfect, but have no idea how to do the "if is not mounted" part...

---

### Post by anthro398 on 2005-11-16
This won't exactly fit your situation, but I thought I'd post it anyway.  I back up my Documents directory to a remote Windows share at work.  I don't want admins to access to my work so I use gpg to encrypt it.  As you can see I grab a few profiles and configuration files and copy them to the Documents directory before I back up.  You see, I have encrypted partitions due to the sensetive nature of some of my work and this allows me to back up remotely without exposing anything.  Prior to that I used rsync, which is awesome.  I run this nightly with as a cron job.

```
#/bin/bash

# Script to backup system to h drive

BACKUPDIR="/home/me/Documents/work/Random/Computer-setup/backups"
WORKDIR="/home/me/Documents/work"
COPY="cp -av"

				# Copy disparate files into backup directory
echo "Collecting files to backup directory."
$COPY /home/me/.mozilla/firefox/*.default/ $BACKUPDIR/firefox/
$COPY /home/me/.mozilla-thunderbird/*.default/ $BACKUPDIR/thunderbird/
$COPY /home/me/.gaim $BACKUPDIR/gaim/
$COPY /home/me/.ssh/known_hosts $BACKUPDIR/
$COPY /etc/hosts $BACKUPDIR/
$COPY /etc/hosts.allow $BACKUPDIR/
$COPY /etc/hosts.deny $BACKUPDIR/
$COPY /etc/apache2/httpd.conf.local $BACKUPDIR/
$COPY /home/me/.scripts/* $BACKUPDIR/scripts/
$COPY /etc/apache2/apache2.conf $BACKUPDIR/


				# Create tar file and pipe through gzip for compression
echo "Creating and compressing tar file."
tar cvf - $WORKDIR | gzip > /home/me/me-backup.tar.gz

				# Use Gnupg to encrypt backup
gpg -r me@me.org -e me-backup.tar.gz
echo "Backup encrypted."

				# rename *.tar.gz.gpg to *.tar.gz -- keep going back and forth about this one
#mv me-backup.tar.gz.gpg me-backup.tar.gz



				# Mount H drive to filesystem (will fail if unable to mount)
/home/me/.scripts/mount-common.sh
echo "Mounted H drive"

				#Check for existance of previous backups	
if [ /mnt/h/me-backup.tar.gz.gpg ]
then	
	echo "Existing backup discovered. Moving backup to backup2"
	mv /mnt/h/me-backup.tar.gz.gpg /mnt/h/me-backup2.tar.gz.gpg
	
else 
	echo "No existing backup."
fi

	
				# Copy backup to H drive
$COPY /home/me/me-backup.tar.gz.gpg /mnt/h/
				# Compare copy to original to confirm copy was successful
if cmp /home/me/me-backup.tar.gz.gpg /mnt/h/me-backup.tar.gz.gpg &> /dev/null
				# Added the removal of older backup to conserve space on H.  Wish I didn't have to.
then echo "Move to H drive successful"  && rm -rf /home/me/me-backup.tar.gz.gpg && rm -f /mnt/h/me-backup2.tar.gz.gpg
else echo "Move to H drive unsuccessful!"
fi

/home/me/.scripts/unmount-common.sh
echo "Unmounted H drive"
echo "Backup Complete"

```

---

### Post by Original Brownster on 2005-11-16
[QUOTE=megamania]Well, since I would backup to a removable disk in an Ide rack, it would be great if I could put in a cronjob (is that what it is called?) something like this:

----
if /backup is NOT mounted -> EXIT
backup script follows...
----
[/QUOTE]
Hi,
Well AFAIK you could write a bash script(I just tried it and it worked) that tests for success on running a command like:

#!/bin/bash
if mount /dev/hdb3 /mnt/backups
then
{backup commands}
umount /mnt/backups
else
echo couldnt mount volume, aborting
fi

---
substituting your devices and mount points of course
adding any rsync commands you want as well.
you would then make it executable and save it in your /etc/init.d directory with a name like runbackup.sh
then use the update-rc.d command (man update-rc.d) to add it to runlevel 0 with an appropriate sequence number, this way it would run each and everytime you shut the pc down, cool huh?
check this [link]("http://www.debian.org/doc/FAQ/ch-customizing.en.html") for info about runlevels and stuff - hell I might do it myself now.

---

### Post by Original Brownster on 2005-11-16
[QUOTE=shof2k]No problem....it's good using your own initiative.  You might also want to try DAR.  It's killer feataure is that you can 'slice' up your backups so fit a DVD or CD.[/QUOTE]
dar is brill, I second that for making disk copies.
There is also kdar if you like gui's

---

### Post by docboat on 2005-11-17
I am just trying kdar at the moment ... what I would like to hear is how you are:

1. choosing a good backup application
2. implementing it in daily use

A simpel example of a crontab solution would help me enormously. I am struggling to get my USB drive to be r/w not r/o so I can back up the whole disk (well actually two disks) on to it.

---

### Post by Miguel on 2005-11-17
Just a point:

If you create a tarball of your home or anything else, remember that you can't have files larger than 2Gb (at least for ext3, don't know about reiserfs). A file of 3Gb will still use up 3gigs of hard drive... but will be unreadable (or at least not fully recoverable). I tell you because this is one of the things one does not want to discover by himself... when you need the backup.

---

### Post by nocturn on 2005-11-17
[QUOTE=docboat]I am just trying kdar at the moment ... what I would like to hear is how you are:

1. choosing a good backup application
2. implementing it in daily use
[/QUOTE]

You break it down in to a couple of steps.

1. Define your requirements.
    - How many machines will you back up (more then 1 is more complex).
    - What is the target media, do you want backups to tape, CD, DVD or HD
    - How much data will you back up?  
    - How long to keep backups?  (Do you want to restore a file deleted in march?)
    - What is your skill level (Amanda and Bacula are quite good, but quite complex).
    - Do you require GPL software, or do you want to pay (BRU and Arkeia are pretty good, but not free).

2. Look at your options using freshmeat and google.  Make a list of programs that you can use (and can afford).

3. Match your requirements from step one against the features of the programs and choose the options that fits best.

4. If possible, test-run multiple options.  Or at least the one you chose.  Test making backups, but also restoring them.  Consider what you will do on a full crash (bare-metal-recovery).

I hope this helps

---

### Post by nocturn on 2005-11-17
[QUOTE=Miguel]Just a point:

If you create a tarball of your home or anything else, remember that you can't have files larger than 2Gb (at least for ext3, don't know about reiserfs). A file of 3Gb will still use up 3gigs of hard drive... but will be unreadable (or at least not fully recoverable). I tell you because this is one of the things one does not want to discover by himself... when you need the backup.[/QUOTE]

This limit only applies to ext2, ext3 can have much bigger files (at least 16 GB)
For Reiser, the limit is 8 Tebibyte per file.

For more information, go here:
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

---

### Post by Miguel on 2005-11-17
Really?

I had problems with a tar.bz2 of some 4.2Gb I made with SuSE8.2 before switching to Debian Sarge (work computer). It was irrecoverable. I am pretty sure it was ext3 fs (though I could be wrong). Maybe one also must specify a kernel option?

Of course, something could also have gone wrong. You know, when all possibilities have been discarded by logical arguments, the remaining one must be correct, no matter how unlikely it seems.

PS: Don't worry, I did not delete my /home partition. The tarball was more paranoia that anything else. When all your thesis data is stored there, you start seeing ghosts

PS2: If I didn't delete my home partition... I  can guess which fs it used!!! It is reiserfs (should have known... typical of SuSE). But I moved it to my ubuntu laptop, with is ext3 all the way.

---

### Post by nocturn on 2005-11-17
[QUOTE=Miguel]Really?

I had problems with a tar.bz2 of some 4.2Gb I made with SuSE8.2 before switching to Debian Sarge (work computer). It was irrecoverable. I am pretty sure it was ext3 fs (though I could be wrong). Maybe one also must specify a kernel option?
[/QUOTE]


I guess it must have been an accident or a SuSE specific problem.  I have been using 4GB+ files (mostly ISO) for a long time on both Reiserfs and Ext3 without problems.

---

### Post by Miguel on 2005-11-17
Oh, so it's that. Cheers, nocturn

---

### Post by Original Brownster on 2005-11-17
[QUOTE=docboat]I am just trying kdar at the moment ... what I would like to hear is how you are:

1. choosing a good backup application
2. implementing it in daily use

A simpel example of a crontab solution would help me enormously. I am struggling to get my USB drive to be r/w not r/o so I can back up the whole disk (well actually two disks) on to it.[/QUOTE]

Hi,
cron is fine if your pc / server is up 24/7 otherwise look at anacron, if the pc's not up when the backup is due, it remembers and runs the next time the pc is up. 

My strategy is to use dar to backup the operating system to dvd-r every 3 months and ignore all personal data /home and also my music collection.
then I use anacron and a script and use 'rsync' to copy all my personal stuff to another harddisk which is otherwise unmounted. This I run weekly.
This is just a home pc so this suits my needs.

---

### Post by steve.horsley on 2005-11-17
[QUOTE=Miguel]Just a point:

If you create a tarball of your home or anything else, remember that you can't have files larger than 2Gb (at least for ext3, don't know about reiserfs). A file of 3Gb will still use up 3gigs of hard drive... but will be unreadable (or at least not fully recoverable). I tell you because this is one of the things one does not want to discover by himself... when you need the backup.[/QUOTE]

I have succesfully restored a Windoze partition from a 25 Gig file stored on a Reiser3 drive.

---

### Post by megamania on 2005-11-17
Well, I'd just like to thank you all for the useful infos provided so far, and particularly anthro398 and Original Brownster for their code samples.

I'll try to write a decent script (my first one in linux!) over the weekend, and then I'll scream for help on sunday!  :-)

---

### Post by megamania on 2005-11-25
[QUOTE=Original Brownster]Hi,
Well AFAIK you could write a bash script(I just tried it and it worked) that tests for success on running a command like:
[/QUOTE]

I tried to create a script that checks if a filesystem is mounted as you suggested on your message last week:
```

#!/bin/bash
if mount /dev/hda2 /mnt/backup/
then
echo it is mounted
else
echo could not mount volume
fi

```

I get an error saying that I have to be root to mount the filesystem, even if it is already mounted.

How can I just check if it is mounted, and if it is not then just abort the script?

---

### Post by megamania on 2005-11-25
Well, it took me two hours but I solved it myself, and I'm posting it just in case anybody needs it.

The following code allows you to check whether a filesystem is mounted or not:

```

#! /bin/bash

dev=/mnt/backup
a=`mount | grep $dev | cut -d " " -f 3`

if [ "$a" ]
then 
	echo $dev is mounted
else
	echo $dev is not mounted
fi

```
 :D

---

### Post by megamania on 2005-11-26
[QUOTE=megamania]
The following code allows you to check whether a filesystem is mounted or not:

```


[COLOR="Red"]if [ "$a" ][/COLOR]

```

[/QUOTE]

I realized that the IF statement above is wrong: if you have filesystems with similar names (i.e. mnt/backup and mnt/backup1) it could return a wrong result.

I amended the code as follows:

```

#!/bin/bash
dev=/mnt/backup
a=`mount | grep $dev | cut -d " " -f 3`
if [ "$a" = "$dev" ]
then 
echo $dev is mounted
else
echo $dev is not mounted
fi

```

I think this one is correct... :)

---

### Post by stalefries on 2005-11-26
Try a google search. I think rsync is what you're talking about, but I've never tryed to mess with something like this before.

---

### Post by kosmic on 2005-11-26
Why don't you try 'Parteimage' I use it to backup all my servers, and workstations :)
 
[http://www.partimage.org/]("http://www.partimage.org/")
 
 
and it is just and apt-get far away ;)

---

### Post by megamania on 2005-11-27
[QUOTE=kosmic]Why don't you try 'Parteimage' I use it to backup all my servers, and workstations :)
 
[http://www.partimage.org/]("http://www.partimage.org/")
  
and it is just and apt-get far away ;)[/QUOTE]

Thanks Kosmic.

Stalefries,

yes, we were actually talking about rsync, but I was looking for a way to check if the partition was mounted before starting the backup activity.

Now I have a complete script that checks if the removable (backup) hard disk is mounted and mirrors my home partition to it.

Just thought I'd share the "check if it's mounted" part, since the "rsync" part was previously discussed in this same thread...  :-)

---

### Post by quietglow on 2005-11-27
Here's another vote for rsync:

I have my home directory (which is ~140g) on a separate drive and have another just like it that I rysnc to daily (in the middle of the night). For my non-critical level of work this is just fine!

---

### Post by NZ-Wanderer on 2005-12-04
Ok, I seem to be a little stuck here...
What do I do to apt-get the file?? - I looked in synaptic but it not in there.. 

[QUOTE=kosmic]Why don't you try 'Parteimage' I use it to backup all my servers, and workstations :)
 [http://www.partimage.org/]("http://www.partimage.org/")
 and it is just and apt-get far away ;)[/QUOTE]

---

### Post by sparty2809 on 2005-12-04
I use [Acronis True Image]("http://www.acronis.com/").  It cost money but it does a great job.

---

### Post by thalliwell on 2005-12-04
I use Dive Snapshot 

[http://www.drivesnapshot.de/en/](http://www.drivesnapshot.de/en/)

great little Windows Programme that will back up Your Linux partition.

---

### Post by poptones on 2005-12-04
I have three disks configured with two raid5 areas (one for userland, one big ol' disk for stuff in general). To keep the system maintainable as possible all three disks have identical partition tables, but only hda has the running system image.

dd if=/dev/hda2 of=/dev/hdb2 bs=8192k

Takes about 50 seconds to back up my linux system.

---

### Post by wanger123 on 2005-12-05
Hey all, I have just discovered kdar, and for a single laptop user backing up uni documents and stuff, I think kdar is perfect. 

Another quickie, I too had problems trying to extract a 3.9GB (more than 2GB) .tar.gz file using ARK and ext3. I tried to extract it from a DVD-R and also from a FAT32 partition but no good. 

I wonder if I backup to DVD using the kdar program (4.4GB default size) if I'll also have this problem (an error was encountered trying to open archive.......or whatever ARK says) 

thanks to all

wanger

---

### Post by poptones on 2005-12-05
DVDs do not natively support files larger than 2gb. Neither does fat32.

Reiserfs seems to work fine with larger files, but nautilus acts very flaky when trying to interact with them.

---

### Post by wanger123 on 2005-12-05
Thanks for the reply poptones.

What do you mean by this?

 ```
DVDs do not natively support files larger than 2gb. Neither does fat32.
```

I only ask because I obviously have the 3.9GB .tar.gz on the fat32 partition. So you mean that I can save it to fat32, but I cant open and read on fat32?

If so, I guess I should break it up into 2GB blocks eh?

Many thanks

wanger

---

### Post by poptones on 2005-12-05
You cannot put a file larger than 2gb on a dvd and expect to be able to read it. There is a way to do this but so far as I know it onlky work with linux. Same (sort of) goes for fat32. 

You can make a multipart archive, or just split it after the fact into 1gb pieces,burn it, and pipe it through cat to open it.

---

### Post by wanger123 on 2005-12-05
Thanks a lot poptones, very good advice :KS 

On a slightly different note, would you recommend reiserfs, ext3 or something else for  a file format when I re-partition (I am getting rid of winblows altogether):D 

[EDIT] never mind I found this:

```
ext3 is journaled but if you shutdown improperly you're still likely to end up having to run a ten minute 
fdisk on restart. With reiser it may take a few seconds to replay the last journal and, unless something went 
terribly wrong, you're right back up and running.

I've tried several and I no longer would trust my data to anything but reiserfs. I've accidentally wiped out hundreds 
of megabytes of partition info and, using the reiserfs diagnostic tools, have been able to recover pretty much 
everything that wasn't overwritten. One may have to pour through gigabytes of lost&found directories, but I have 
found it's always been able to recover.
```

thanks
wanger

---

### Post by Original Brownster on 2005-12-07
[QUOTE=megamania]

Now I have a complete script that checks if the removable (backup) hard disk is mounted and mirrors my home partition to it.

Just thought I'd share the "check if it's mounted" part, since the "rsync" part was previously discussed in this same thread...  :-)[/QUOTE]

Glad you sorted it. 
I have just set my backup to run each time I shutdown the pc using a script that mounts the backup partition and then uses rsync to backup my files before unmounting then shutting down.
This will run as root by the way.

If you wanted to do this all you do is move the script to /etc/init.d/
which is where the start up and shutdown scripts live.
Then run 'update-rc.d -n scriptname start 01 0 6 .'
(man update-rc.d before you try this ;-) ) 
the -n does a dummy run and shows you where it will put the script.
01 is the sequence to run the scripts in for that runlevel so I want it to run first.
0 6 is runlevels reboot and halt (I think, I'm at work and doing this from memory)
.  dont forget the period character like I did and wasted a few minutes wondering why it would not work!

That's basically it. If your using rsync with the -v flag you'll see all the files being backed up roll up the screen. I changed this to -q for quiet instead. 

Now I get a backup each time I walk away from my pc! Cool.

Regards

---

### Post by megamania on 2005-12-08
[QUOTE=Original Brownster]Glad you sorted it. 
I have just set my backup to run each time I shutdown the pc using a script 
[...]
If you wanted to do this all you do is move the script to /etc/init.d/
[/QUOTE]

Thank you. I think I need some time to digest it, but I'll put it in practice. At the moment, I start the backup script manually.

[QUOTE=Original Brownster]
That's basically it. If your using rsync with the -v flag you'll see all the files being backed up roll up the screen. I changed this to -q for quiet instead. 

Now I get a backup each time I walk away from my pc! Cool.
[/QUOTE]

In my script, I used the -v flag but redirected the whole output to a file. The output is appended, so that I have a history of my backups.

I was thinking that we could "merge" our scripts (and others), come up with a tiny configurable script and put it in a How-To thread in this forum... but I'm probably still too noob for this. :-)

---

### Post by Original Brownster on 2005-12-10
[QUOTE=megamania]Thank you. I think I need some time to digest it, but I'll put it in practice. At the moment, I start the backup script manually.



In my script, I used the -v flag but redirected the whole output to a file. The output is appended, so that I have a history of my backups.

I was thinking that we could "merge" our scripts (and others), come up with a tiny configurable script and put it in a How-To thread in this forum... but I'm probably still too noob for this. :-)[/QUOTE]

Good idea, I did briefly think about a script / howto, written to make it easy to configure for different users. Best way of learning is to have a go, I'm no script writer but I have a book on the bash shell which I thumb through whenever I need to write anything.  

Regards

---


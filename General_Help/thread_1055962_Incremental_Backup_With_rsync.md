---
title: "Incremental Backup With rsync?"
date: 2009-01-31
forum: General Help
---

### Post by ChildOfMana on 2009-01-31
Okay, I've done a lot of searching (both on the forums and Google) and I know there's _loads_ of threads/info out there regarding this but forgive me for posting this question as I rather need the info distilled down. Some times there's such a thing as too much info, and I can't quite figure out what I need to do! :(

What I want to do is basically have a manual incremental backup system in place. I want to backup (for example) only /home/user/music, /home/user/pictures and /home/user/videos (not the entirety of my /home directory) to a directory on an internal HDD - /media/disk/backup (for example).

Preferably I want to create an initial backup of *everything* in these directories, and then after that I want to run the backup command and have it back up only the files that have changed since.

I'm not too interested in creating regular scheduled backups - just a command I can run on a whim when I want to add changed/new files to the backup folder.

I assume this would be a job for rsync?

---

### Post by ChildOfMana on 2009-01-31
Anyone?

---

### Post by BandD on 2009-01-31
This isn't the most helpful thing, I'm sorry for that.  But I was curious about this.

I use rsync for backing up my home directory and a few other odds and ends and thought it would be useful to know how to achieve this sort of selective directory syncing.  I can't quite firgure it out though.  I know that the command line should look something like this, though it's not working for me:

```
 rsync -avn -f "+ /home/" -f "+ /home/user/" -f "+ /home/user/Pictures/" -f "+ /home/user/Pictures/*" -f "- *" /home/user /media/disk/backup
```

(-a = archive v = verbose n = dry-run  -f = filter  + = include  - = exclude)

From what I gather from the man pages this should work (you'd have to add some more -f "+ ..." for the video and music directories as well).  But it seems that the -f "- *" trumps everything, even though the man pages say that this format should work.  So I'm not sure what the deal is.

Alternatively, you can run three seperate rsync commands to get the job done:

```
rsync -av /home/user/Pictures /media/disk/backup
```
```
rsync -av /home/user/Videos /media/disk/backup
```
```
rsync -av /home/user/Music /media/disk/bakcup
```

---

### Post by ChildOfMana on 2009-01-31
Thanks BandD. I took a slightly different approach in the end though.

I created a script like so;

```
#!/bin/bash
sudo rsync -av --progress --delete /home/user/Video /media/disk/backup && rsync -av --progress --delete /home/user/Pictures /media/disk/backup && rsync -av --progress --delete /home/user/Music /media/disk/backup
```

I named it backup.sh and placed it in my /home directory.

Now I can just run the script;

```
sudo sh backup.sh
```

and it takes care of everything. I could even attach the script to a cron job to automate it if I wanted (which I don't right now - but handy to know).

There's probably an easier way of doing this but at least now I don't have to type a long string of commands every time I want to backup data. :)

---

### Post by p_quarles on 2009-01-31
The script you have works, but it's not actually doing incremental backups, it's just creating mirrors of the Video and Music directories in your /home.

Here's my simple script for creating dated point backups. The --link-dest option uses hard links to create multiple locations for the same file without repeating the data itself. In effect, you get something very much like OS X's Time Machine, in that it creates a space-efficient series of point-in-time backups. This script syncs my entire filesystem, but it's easy to modify to only copy what you want. 
```
#!/bin/sh

date=`date "+%Y-%m-%d-%H:%M:%S"`
rsync -vaP --exclude=sys/** --exclude=proc/** --exclude=media/** --exclude=tmp/** --exclude=var/tmp/** --link-dest=/media/disk/current / /media/disk/backup-$date
rm /media/disk/current
ln -s /media/disk/backup-$date /media/disk/current
```

---

### Post by ChildOfMana on 2009-01-31
Thanks p_quarles.

Actually, I think I asked the wrong question in the first place - it was a mirror of my directories I was after. Sorry about that.

This is only a temporary thing though as I'm planning on adding NAS to my network soon, and I'll be wanting to put a proper backup regime in place then - which will entail incremental backups.

I'll have a look at your script and try to adapt it when the time comes.

Thanks for the help guys.

---

### Post by HermanAB on 2009-01-31
That is a very neat script.  Thanks, I may use it one day.

Cheers,

Herman

---

### Post by unixeducation on 2009-01-31
Give rdiff-backup a shot: [http://arctic.org/~dean/rdiff-backup/unattended.html]("http://arctic.org/~dean/rdiff-backup/unattended.html")

I use it to do nightly incremental server backups via a cron job, pulling from several machines to a central backup host. Hope this helps!

---

### Post by Slim Odds on 2009-01-31
> **ChildOfMana said:**
> I created a script like so;

```
#!/bin/bash
sudo rsync -av --progress --delete /home/user/Video /media/disk/backup && rsync -av --progress --delete /home/user/Pictures /media/disk/backup && rsync -av --progress --delete /home/user/Music /media/disk/backup
```I named it backup.sh and placed it in my /home directory.

Now I can just run the script;

```
sudo sh backup.sh
```and it takes care of everything.

Why the "sudo"? There's no reason to run this as root.

---

### Post by ChildOfMana on 2009-01-31
[quote="Slim Odds"]Why the "sudo"? There's no reason to run this as root.[/quote]

Yeah I know - I read up more on rsync after I made the script. I've since changed it. Still worked with sudo though so no harm done.

Thanks so much for all the answers everyone. I'll have a good play round with rsync when I get time and will hopefully be able to achieve what I want to do.

Edit: Will also check rdiff-backup out. Thanks unixeducation.

---


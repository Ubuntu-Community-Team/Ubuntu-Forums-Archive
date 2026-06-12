---
title: "rsync script will not access home dir!  plz help!"
date: 2009-05-31
forum: General Help
---

### Post by quixote on 2009-05-31
I'm trying to implement an incremental rotating backup system.  This rsync command works fine if I run it in a terminal:```
#!/bin/bash
rsync -avu --exclude ".local/share/Trash/" --exclude ".thumbnails/" --exclude ".VirtualBox/" --exclude='/home/*/.mozilla/firefox/*/Cache' --delete-delay --ignore-errors  /home/quix/ /mnt/bigdrive/quixbackup/home/daily.1  1>log-backup.txt 2>log-backup-errs.txt
```

But if I run it as part of the script that hardlinks "daily.1" to "daily.2" and so on (and ultimately deletes the oldest one) it keeps giving me "permission denied" error on my own home dir!```
$RSYNC					\
	 -avun --delete-delay  --ignore-errors  	\  
        --exclude="/home/*/.gvfs"                 \
	--exclude=".local/share/Trash/"			\
	--exclude=".thumbnails/"		\ 
	--exclude=".VirtualBox/" 	\
	--exclude='/home/*/.mozilla/firefox/*/Cache'	\
	/home/quix/ $SNAPSHOT_RW/home/daily.1 		\
	1>log-backup.txt 2>log-backup-errs.txt ;
```
(The -n switch added so it'll just do dry runs for now)

No matter what I try: running as user, running as sudo, unmounting .gvfs, deleting.gvfs, chmod of .gvfs to 666, I always always always get this error:```
rsync: link_stat "/home/quix/ " failed: No such file or directory (2)
```

At the command line, --ignore-errors seems to deal with that stupid .gvfs stuff.  Why doesn't it work in the script?

Most important: HOW CAN I GET THE RSYNC SCRIPT TO WORK?

Thanks! :D

---

### Post by quixote on 2009-06-02
no rsync experts out there?  Is another part of ubuntuforums maybe a better place to ask this question?

---

### Post by MyR on 2009-06-02
I'm no expert but it appears that
this line: /home/quix/ $SNAPSHOT_RW/home/daily.1
needs to have the space removed

peace

---

### Post by quixote on 2009-06-03
I got on to say you were wrong, that one was source, the other target, but as I look at my own error message more closely ... damned if you're not right!  There does seem to be an extra space.  Be nice if it were that simple (and stupid!).  I'll get back on later with results when I have a minute to go back and try it.

---

### Post by quixote on 2009-06-06
Nope, that wasn't it.  It looks like there's an extra space in the error message, but in reality there isn't.

What I did was try another script where source is specified earlier in the script (SOURCES="/home/quix") and then in the rsync line it say $SOURCES/ 

I have no idea why that would make a difference, but whatever works, I guess.

This is the whole script.  I'm rather pleased with it as a backup solution :) .  The only thing I can't get to work is the exclude statement, hence all the excludes in the rsync line.  (Obviously, to customize, it needs one's own values in for the username, paths, and so on.)

```

#!/bin/sh
# rsync: Brice Burgess - bhb@iceburg.net , rotation: Mike Rubel http://www.mikerubel.org/computers/rsync_snapshots/, mistakes: MMolvray...
# rbackup.sh -- secure backup to a remote machine using rsync.

# Directories to backup. Separate with a space. Exclude trailing slash!
SOURCES="/home/quix"

# IP or FQDN of Remote Machine
RMACHINE=snowy

# Remote username
RUSER=quix

# Directory on (remote) machine where backup(s) will be stored
# Exclude trailing slash!
RTARGET="/mnt/mediavault/quixbackup-jaunty"

#  not working!!!!
EXCLUDE_FILE="/home/quix/exclude-home-file"

# Comment out the following line to disable verbose output
#VERBOSE="-v"

mount /mnt/mediavault/

# step 1: delete the oldest snapshot, if it exists:    # simply delete.  when cron job with week script runs, it will take daily.7
if [ -d $RTARGET/home/daily.7 ] ; then			\
rm -rf $RTARGET/home/daily.7 ;				\
fi ;

# step 2: shift the middle snapshots(s) back by one, if they exist
if [ -d $RTARGET/home/daily.6 ] ; then			\
mv $RTARGET/home/daily.6 $RTARGET/home/daily.7 ;	\
fi;
if [ -d $RTARGET/home/daily.5 ] ; then			\
mv $RTARGET/home/daily.5 $RTARGET/home/daily.6 ;	\
fi;
if [ -d $RTARGET/home/daily.4 ] ; then			\
mv $RTARGET/home/daily.4 $RTARGET/home/daily.5 ;	\
fi;
if [ -d $RTARGET/home/daily.3 ] ; then			\
mv $RTARGET/home/daily.3 $RTARGET/home/daily.4 ;	\
fi;
if [ -d $RTARGET/home/daily.2 ] ; then			\
mv $RTARGET/home/daily.2 $RTARGET/home/daily.3 ;	\
fi;

# step 3: make a hard-link-only (except for dirs) copy of the latest snapshot,
# if that exists
if [ -d $RTARGET/home/daily.1 ] ; then			\
cp -al $RTARGET/home/daily.1 $RTARGET/home/daily.2 ;	\  #this could be --link-dest
fi;



echo "Verifying Sources..."
for source in $SOURCES; do
	echo "Checking $source..."
	if [ ! -x $source ]; then
     echo "Error with $source!"
     echo "Directory either does not exist, or you do not have proper permissions."
     exit 2
   fi
done

if [ -f $EXCLUDE_FILE ]; then
EXCLUDE="--exclude-from=$EXCLUDE_FILE"
fi

echo "Sources verified. Running rsync..."


  rsync $VERBOSE $EXCLUDE -avu --delete --exclude ".gvfs" --exclude ".local/share/Trash/" --exclude ".thumbnails/" --exclude ".VirtualBox/" --exclude ".mozilla/firefox-3.5/*/Cache/"  --exclude ".mozilla/firefox/*/Cache/" $SOURCES/ $RTARGET/home/daily.1  1>loghome.txt 2>loghome-errs.txt

# step 5: update the mtime of daily.1 to reflect the snapshot time
touch $RTARGET/home/daily.1 ;

exit 0

```

---

### Post by lavinog on 2009-06-09
Does it make a difference if you put everything on one line vs breaking it up on multiple?

Also what editor did you use to write the script?
I have had a couple of weird cases where a text editor added unprintable characters to a file. I had to remove them with a hex editor.

---

### Post by quixote on 2009-06-09
Multiple lines versus single didn't seem to make a difference.  I think there must have been something about the way the shell was handling my home directory path in the rsync command in my first version that just wasn't working.  

The second version, where I give it the same information in the script, outside the rsync command, does work.  Go figure.  I don't know enough about rsync or shell idiosyncracies to have a clue why the second works and the first doesn't.

---


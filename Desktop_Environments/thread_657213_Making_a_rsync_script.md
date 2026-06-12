---
title: "Making a rsync script"
date: 2008-01-03
forum: Desktop Environments
---

### Post by frodemt on 2008-01-03
I want to make a rsync script that can be executed from a users desktop.

It will copy only new or changed files to a samba share that I have mounted as "/sikker".

I learned scripting at school in 2001, but have forgotten almost everything.

---

### Post by megamania on 2008-01-03
> **frodemt said:**
> I want to make a rsync script that can be executed from a users desktop.
It will copy only new or changed files to a samba share that I have mounted as "/sikker".


Here's my script. I use it to mirror my home directory to the /archive/ directory of my backup hard disk. In other words, the contents of the destination disk become a copy of the source by just adding / changing / deleting the files as appropriate.

There's a mount check because my hard disk is in a removable tray.

The script is derived from somebody else's script - sorry but I can't give credits. The basic command is the "rsync" in the middle of the script. The rest is just to set it up and create a logfile.

This is intended to get you going - hope it works for you, but it is in no way perfect, and if you don't know what you're doing or what to change _you may end up losing data_. I'm not a script expert at all, but I'll try to help if needed.

```

SOURCE=/home/my_home_dir	# the source for data
DEST1=/media/backup/archive/			# the backup path
dev=/media/backup				# the backup device (file system)-used to mount and check if mounted 
LOGFILE=$0.log					# logfile - takes scriptname + .log

echo logfile created to: $LOGFILE

echo "**************************************************************************" >> "$LOGFILE"
echo "*********************         START OF LOGFILE       *********************" >> "$LOGFILE"
echo "**************************************************************************" >> "$LOGFILE"
echo backup started >> "$LOGFILE"
echo
echo -------------------------------------------------------------------------- >> "$LOGFILE"
echo &date >> "$LOGFILE"
echo -------------------------------------------------------------------------- >> "$LOGFILE"

sudo mount -t ext3 /dev/hda2 $dev

#verifies that $dev is mounted
a=`mount | grep $dev | cut -d " " -f 3`
if [ "$a" = "$dev" ]

then 
	echo $dev is mounted - starting backup >> "$LOGFILE"

	# --delete-excluded       also delete excluded files on receiver

	rsync -av --delete-excluded \
	--exclude='*Cache*' --exclude='*.thumbnails*' --exclude='*.fonts*' \
	--exclude='*.themes*' --exclude='*lost+found*' --exclude='*metafiles*' \
	--exclude='.Trash' \
	$SOURCE $DEST1 >> "$LOGFILE"

else
	echo $dev is not mounted - aborting >> "$LOGFILE"
fi

echo >> "$LOGFILE"
echo -------------------------------------------------------------------------- >> "$LOGFILE"
echo backup finished >> "$LOGFILE"
echo &date >> "$LOGFILE"
echo "$0" finished in "$SECONDS" seconds from opening of shell >> "$LOGFILE"
echo "++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++" >> "$LOGFILE"
echo "++++++++++++++++++++++         END OF LOGFILE       ++++++++++++++++++++++" >> "$LOGFILE"
echo "++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++" >> "$LOGFILE"

echo >> "$LOGFILE"
echo >> "$LOGFILE"

```

---

### Post by frodemt on 2008-01-03
Hi, I will have a look at your script. I think it might be more complex than I have seen my solution.

Thank you!:popcorn:

---


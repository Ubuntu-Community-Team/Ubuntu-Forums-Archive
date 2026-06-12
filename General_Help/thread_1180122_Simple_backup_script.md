---
title: "Simple backup script"
date: 2009-06-06
forum: General Help
---

### Post by rplantz on 2009-06-06
I am providing a script that uses rsync to make rotating snapshot backups of my home directory on an external disk. I adapted a script from [www.mikerubel.org/computers/rsync_snapshots/](www.mikerubel.org/computers/rsync_snapshots/). I recommend reading the material there for a better understanding.

To make a snapshot I simply plug in my external disk. Ubuntu automatically mounts the disk at /media/ and I run the script:
```

./make_snapshot.sh

```
It keeps the latest four snapshots. The --link-dest rsync option hard links unchanged files in the latest snapshot to those in the next-to-latest snapshot. This greatly reduces disk space required and time required for the snapshot. (See the above reference for an explanation of "hard link".)

This type of backup is useful for recovery from two of the most common home user data loss situations:

1. Accidental deletion of a file. This is the well-known user error with ID number 10T (ID10T). To recover the lost file, I plug in the external drive, open the latest snapshot folder, and drag the file back to my main disk.

*Aside:* I actually did a user ID10T operation once where I deleted my *entire home directory*. I wrote a simple rsync script to restore my home from my latest snapshot.


2. Corruption of main disk. To recover from this I would need to fix the disk (perhaps install a new one) and reinstall Ubuntu. I could then plug in my external disk and drag the desired folders and files from my latest snapshot to my main disk. Or I could write a simple rsync script for the recovery.

This backup script does **not** provide for:

1. Long-term archival backup. You need some other means to keep family photos, etc.

2. A mirror backup that can be quickly brought up. You would need this if it's important to stay on line, for example, a server. Recovering from my snapshot backups can take several hours.

3. Backup over a network. This is discussed in the article I reference above.

If you use this script, you will probably want to make some changes:

1. SOURCE -- change "/home/bob/" to your home directory, typically "/home/*usr_name*". This change is *required* (unless your user name is bob).

2. DESTINATION -- double check that this is where your external disk is mounted by Ubuntu. And your disk may have a different name.

3. EXCLUDES -- You can use any name for this file. You will need to decide upon your own exclusions.

4. System commands -- It's probably a good idea to use the "which" command (e.g., which rm) to double check these locations on your system.

5. Make the snapshot -- I named my snapshot folders (on the external disk) snapshot_0, ..., snapshot_3. You can change these to your own names if you wish. Just make sure you are consistent.

As usual, if you see any errors or have suggestions for improvements, please let us know.

```

#!/bin/bash
# ----------------------------------------------------------------------
# Shell script to use rsync for making a snapshot backup to an external
# hard disk.
#
# Adapted from mike's handy rotating-filesystem-snapshot utility
# www.mikerubel.org/computers/rsync_snapshots/
# 
# by: Robert Plantz - 05 June 2009
# ----------------------------------------------------------------------

# -------------- File and directory locations --------------------------
# Assume that the destination volume is mounted. I use an external
# usb disk that mounts automatically when plugged in.
DESTINATION=/media/disk/

# Default is to backup my home directory.
SOURCE=/home/bob/

# Other files and directories excluded or included are listed in the
# following file. See "FILTER RULES" and "INCLUDE/EXCLUDE PATTERN RULES"
# sections in the rsync man page for the format of this file.
# Examples are:
# - .mozilla/firefox/eyo8gt4n.default/Cache
# - .opera/cache4
# - .evolution/cache
EXCLUDES=backup_exclude

# -------------- System commands used here -----------------------------
unset PATH    # to make sure we use the right programs
ECHO=/bin/echo;
RM=/bin/rm;
MV=/bin/mv;
TOUCH=/bin/touch;
RSYNC=/usr/bin/rsync;
MKDIR=/bin/mkdir;

# -------------- Make the snapshot -------------------------------------
# Delete oldest snapshot if it exists.
if [ -d $DESTINATION/snapshot_3 ] ; then
   $RM -rf $DESTINATION/snapshot_3
   $ECHO "Removed old snapshot_3"
fi

# Move existing snapshots back one.
if [ -d $DESTINATION/snapshot_2 ] ; then
   $MV $DESTINATION/snapshot_2 $DESTINATION/snapshot_3
   $ECHO "Created new snapshot_3"
fi

if [ -d $DESTINATION/snapshot_1 ] ; then
   $MV $DESTINATION/snapshot_1 $DESTINATION/snapshot_2
   $ECHO "Created new snapshot_2"
fi

if [ -d $DESTINATION/snapshot_0 ] ; then
   $MV $DESTINATION/snapshot_0 $DESTINATION/snapshot_1
   $ECHO "Created new snapshot_1"
fi

# rsync from SOURCE to DESTINATION.
# rsync behaves like cp --remove-destination by default, so the destination
# is unlinked first.  If it were not so, this would copy over the other
# snapshot(s) too!
# See rsync man page for options. The time saver here is
# --link-dest. If a file has not changed from the copy in
# the specified directory, a hard link is created to the
# already existing copy rather than recopy the entire file.
# This saves both time and disk space.
if [ -d $DESTINATION/snapshot_1 ] ; then
   $ECHO "Creating snapshot_0 based on snapshot_1 on $DESTINATION"
   $RSYNC -a -v --delete    \
        --exclude-from=$EXCLUDES           \
        --link-dest=$DESTINATION/snapshot_1    \
        $SOURCE $DESTINATION/snapshot_0/
else
   $ECHO "Creating a new snapshot_0 on $DESTINATION"
   $MKDIR $DESTINATION/snapshot_0
   $RSYNC -a -v --delete    \
        --exclude-from=$EXCLUDES           \
        $SOURCE $DESTINATION/snapshot_0/
fi
$ECHO "rsync exit code is "$?
# update the mtime of snapshot_0 to reflect the snapshot time
$TOUCH $DESTINATION/snapshot_0

```

Edit: My first snapshot took about 1/2 hour. Subsequent snapshots take only a few minutes because unchanged files are not recopied. There is simply a hard link created in the new snapshot directory to the file that was copied during the very first snapshot.

---

### Post by VMC on 2009-06-06
Thank you. I just last night did little research on rsync. I misunderstood that rsync needed a backup server to function.

---

### Post by rplantz on 2009-06-07
Be careful here. My script doesn't use a server. It uses rsync to create a directory and copy files to the new directory. This new directory could even be on your main hard disk, but that's probably not a good place for it.

I use an external hard disk to provide some added safety. If my main hard disk crashes, the external one (holding my backup) is very likely to be okay.

---


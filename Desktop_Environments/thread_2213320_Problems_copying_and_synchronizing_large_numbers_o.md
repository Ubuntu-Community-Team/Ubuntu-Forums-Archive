---
title: "Problems copying and synchronizing large numbers of files"
date: 2014-03-26
forum: Desktop Environments
---

### Post by crazybear on 2014-03-26
I have very large data disks on my computer. To prevent data loss from crashes or 'hostile action' I keep a backup copy. I prefer to have the back up as a 'mirrored' disk and not as a compressed 'backup'. As I don't like to unplug all of the other disks [I have MANY in my computer] and run clonezilla [running it without removing the other disks is dangerous!], I am left with selecting and copying over to the mirror disk [which is kept OUT of the computer after updating]. However, this is not fast with a 3TB disk and Ubuntu [12.04.4] drives me crazy for having a less user friendly copy function than does Windoze [which I avoid]. There is 'replace all' - which I'm forced to use; there is no 'ignore all' [do not copy if file already exists] and while nearly impossible to stay for hours hitting 'skip' - the Skip button jumps around [and has no key assignment] according to how long the title of the file is. This really needs to be fixed, IMHO. I know of rsync, but find the options confusing and haven't tried that yet. Anyone know of  other programs in Ubuntu that would move only new files and folders to the mirror disk?!....and/or a comprehensible set of instructions for rsync [the standard ones make me almost afraid to try with all the switches and options]? Thanks. To developers, please note that while most things in Ubuntu I find as good or better than Windoze, the copy function really is very poor and I would think easily fixed for large amounts of copying - if only more options were available and the boxes didn't move around.

---

### Post by The Cog on 2014-03-26
rsync is the tool to use.
If you don't like typing commands, there is a wrapper GUI for it called grsync that implements the most important options.

P.S.
This is the script I use for backing up my laptop. It doesn't back up the system, just /home and /opt because I felt that was all I needed to backup. 
Elephant is the backup drive's filesystem label ( because an elephant never forgets).
The compress option is not valid on all filesystem types (my backup drive is btrfs)
```
#!/bin/bash

# Re-run with sudo if we're not already root
if  [ $UID != 0 ]
then
    sudo $0
    exit
fi

# Mount the drive
mkdir -p /mnt/Elephant
mount -o compress -L Elephant /mnt/Elephant

# Check the backup directory is mounted
if [ ! -e /mnt/Elephant/laptop ]
then
    echo Elephant drive is not mounted.
    exit 1
fi


function dobackup {
    echo Backing up to Elephant...
    nice rsync -av --delete --exclude .gvfs /home /opt /mnt/Elephant/laptop
    sync
    umount /mnt/Elephant
}

time dobackup

```

Edit. Gui wrapper name is grsync, not rsynt as I originally typed.

---

### Post by crazybear on 2014-03-26
I haven't found the GUI for rsync - though I  looked - it would be nice and likely helpful. I'm not very experiences with command line scripts - though use them when I feel they are clear enough to not mess up totally.
Normal 'backups' are NOT what I really want, I want a clone, basically, but as only a few files have usually been added or changed, I need some program or script that will only update the reserve copy from the in use primary data disk. [no compression, no special backup file type - but just the normal original file type, etc.] This way, if there is a problem with the original, or I'm travelling and need to bring the copy, I just pop it into a computer and use it. I've had problems in the past from hostile forces and special trojans [hunt and destroy types] because of the nature of work I do. Thanks

---

### Post by crazybear on 2014-03-26
Aha, I found grsync and am running it now...it seems to be doing the job...will know soon enough.....

---

### Post by ajgreeny on 2014-03-26
I've been using grsync for years for the very activity you are wanting and it has never once let me down; it does the job quickly and very effectively.  To avoid possible rogue error messages appearing, make the filesystem of your backup drive partitions ext4 as it will avoid any potential loss of permissions that occurs if you back up to a fat32 drive

Thoroughly recommended!

---

### Post by crazybear on 2014-03-26
> **crazybear said:**
> Aha, I found grsync and am running it now...it seems to be doing the job...will know soon enough.....

No, it didn't work....big problem...I was copying a 75% full disk to a similar sized disk and ***it ran out of room***....so the settings are wrong [and confusing]. I thought it would do just what I wanted, but it didn't...can't figure out yet why. I didn't see extra or double files [but they must be there - there are literally hundreds of thousands or millions, so can't check them all. Hmmmmmm......

Setting was: rsync -r -t -p -g -x -v --progress --delete --ignore-existing -u -c -s [folder 1] [folder 2]

isn't folder one supposed to have a / after it?

---

### Post by ajgreeny on 2014-03-26
You need trailing / for both source and destination in grsync or rsync, otherwise you may get everything in folder1 (source) repeated in the destination within itself, ie folder2 will contain another folder2, thereby doubling the files etc etc sent across.

I seem to remember that grsync does this by default, but my memory may be playing tricks.

---

### Post by crazybear on 2014-03-27
Oh my....the manpages for rsync are about 50 page equivalent long!!!! Its like reading a Russian novel!...I'll try to wade through it.....thanks. I haven't found yet what grsync does by default, but I printed [above] what it 'said' after giving the error report - there were no trailing /'s listed.

---

### Post by crazybear on 2014-03-27
the best I can tell, the trailing '/' need only be on the source - not the destination. If anyone knows otherwise, please advise. grsync refuses to report it is putting a trailing / after the source...and I can't find out if it is or not. Anyone know if it is, but just not showing it.....though I'd doubt that. Could this be a bug?

---

### Post by crazybear on 2014-03-27
I just tried running what I had [plus the trailing /] in terminal...but because my folder has an ! in it, I got an error message.......nothing is working out....I might have to resort to filezilla, but that is NOT how I want to do this - as I must do so regularly.

---

### Post by crazybear on 2014-03-27
removed the ! from the file name, but still getting error messages. I think I'm unable to construct a working model using rsync or grsync...I only get error messages. Even deleting the directory I tried to synchronize yesterday on the target I was told there was no room on the disk....so it is filezilla - UGH!

---

### Post by crazybear on 2014-03-27
> **The Cog said:**
> rsync is the tool to use.
If you don't like typing commands, there is a wrapper GUI for it called rsync that implements the most important options.

P.S.
This is the script I use for backing up my laptop. It doesn't back up the system, just /home and /opt because I felt that was all I needed to backup. 
Elephant is the backup drive's filesystem label ( because an elephant never forgets).
The compress option is not valid on all filesystem types (my backup drive is btrfs)
```
#!/bin/bash

# Re-run with sudo if we're not already root
if  [ $UID != 0 ]
then
    sudo $0
    exit
fi

# Mount the drive
mkdir -p /mnt/Elephant
mount -o compress -L Elephant /mnt/Elephant

# Check the backup directory is mounted
if [ ! -e /mnt/Elephant/laptop ]
then
    echo Elephant drive is not mounted.
    exit 1
fi


function dobackup {
    echo Backing up to Elephant...
    nice rsync -av --delete --exclude .gvfs /home /opt /mnt/Elephant/laptop
    sync
    umount /mnt/Elephant
}

time dobackup

```


thanks, but your model in no way applies to what I have in mind. I'm not [and don't want to] back up, nor compress, I'm all in one computer - one data disk to another - they are to be identical. I keep one in the computer and update and occasionally want to synchonize the other and then keep it OUT of the computer. Sadly, thus far, I only get either an overfull drive or error messages. I don't get it.....

---


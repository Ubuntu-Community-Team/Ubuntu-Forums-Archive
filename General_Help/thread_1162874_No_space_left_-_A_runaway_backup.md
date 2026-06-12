---
title: "No space left - A runaway backup"
date: 2009-05-18
forum: General Help
---

### Post by MimiFromParis on 2009-05-18
Hello all,

Upon starting up my Ubuntu machine this morning, I noticed a general system meltdown. All errors seemed to point to a "no space left on device" situation which was confirmed by the output of the "du" command, namely:

```
/dev/sda1             144G  144G     0 100% /
```

Looking at my backup drive, I notice that the /media/Backup mountpoint contains seemingly infinitely recursive copies of the filesystem:

```
/media/Backup/media/Backup/media/Backup/home/&#8230;
```

Here's the script:

```

/usr/bin/touch /home/user/.institution_backup_log
/bin/echo "Starting backup at `date`." >> /home/user/.institution_backup_log
/bin/mount -t ext2 -o remount,rw /dev/sdc1 /media/Backup/
/usr/bin/rsync -qxa --delete --exclude "- .gvfs/" / /media/Backup
/bin/mount -t ext2 -o remount,ro /dev/sdc1 /media/Backup/
/bin/echo "Ending backup at `date`."  >> /home/user/.institution_backup_log
/bin/echo "---------------------------------------------------------"  >> /home/user/.institution_backup_log

```

Does anyone have any clues as to what happened, and especially why the script filled the root filesystem this way? It was designed to run as a cron job once daily.

Any insights would be much appreciated!

---

### Post by anaconda on 2009-05-18
It sounds like your sdc1 wans't mounted on /media/Backup when the script was run

That is why the data was bacupped to the root filesystems /media/Backup folder...

I haven't user "-o remount" option with mount, but does it mount the filesystem if it isn't already mounted?  That option is meant for remounting an ALREADY MOUNTED filesystem.

My quess is that it wont mount filesystem that wasnt already mounted...

OR the mounting just didn't succeed. Maybe it was an external disk, which wasn't ON??

EDIT: You should modify your script so that it will check that the mounting was successfull. eg. check that a file or folder that exist on the sdc1 actually is under /media/Backup ... or something.

---

### Post by MimiFromParis on 2009-05-18
Thank you, Anaconda, that is good to know. So it is normal behaviour for Ubuntu (or Linux?) to copy files into the root filesystem if the drive that is supposed to be associated into the mountpoint fails to mount?

The drive was most probably mounted and on at the time, as it is a USB drive, powered by the computer’s ports, that was manually mounted with a mount command — which did not, to my knowledge, return any errors. However, it is very possible indeed, that I failed to do something either before or after mounting it or that it was somehow unmounted by the system for some reason I am not aware of.

As a general rule, how would I distinguish between writes on folder of the root filesystem and writes on an exeternal drive? Is there a way to know where, physically, a file lives? (Since the folder/mountpoint is populated by rsync, the drive is identical to the root filesystem, making looking for the presence of a file to distinguish filesystems a moot point.)

Thanks again!

---

### Post by anaconda on 2009-05-18
Yes. Mountpoint is just an ordinary folder, so you can copy files to it just like to any other folder.

And how to distinguish between a folder and a mounted filesystem...
The Backup disk wont have anythin under eg. /media/Backup/home folder. It would have just  /home folder.

The same works the other way round too, Your root filesystem shouldn't have eg. /media/Backup/home  .. I mean there shouldnt be anythng there (when Backup isnt mounted) Unless you have copied it to your /media/Backup folder. (like you accidentally did)

You could eg. unmount your Backup disk, and then copy a file to /media/Backup and then you could check if that file exist in /media/Backup. If it exists then your difsk isnt mounted, and if not then it is....

(there must be better ways to archieve the same, but this is one.)

---

### Post by MimiFromParis on 2009-05-18
Thanks for the details, I really appreciate it!

---


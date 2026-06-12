---
title: "Basic back of folders using rsync?"
date: 2008-12-21
forum: General Help
---

### Post by falconed7 on 2008-12-21
Hi everyone!

I am looking for a guide or some help with how to install and configure rsync to do weekly backups of a directory {/media/share} to an external HDD plugged into the home server (Ubuntu Server 8.04.1).

I would imagine I keep the Seagate FREEAGENT in NTFS, so I can pull it out and access it via Windows?

Any help will be great!

Cheers.

---

### Post by mdurham on 2008-12-21
I could be wrong but if you back-up to NTFS you will loose your file permissions. I always back-up to ext3 and it keeps everything the same.
Here is what I use to back-up my system, if it's any use. I think rsync should already be installed. I put the code below into a file and make it executable. The directory P2jaunty64 must already be on the destination drive.
> #!/bin/bash

sudo rsync -ax --progress --delete-during --exclude=.gvfs --exclude=.Trash --exclude=/tmp/* / /media/EXT_EXT3BKUP/P2jaunty64/
sudo touch /media/EXT_EXT3BKUP/P2jaunty64

read -p "Done. Press 'Enter'"

---

### Post by chrisamiller on 2008-12-21
> if you back-up to NTFS you will loose your file permissions

Yes, this is correct.

The basic usage will be something like "rsync -avn <sourcefolder> <destinationfolder>

If you want a perfect mirror, add the --delete flag.  If you want to exclude certain directories, use the --exclude flag.

A quick search on google or these forums will return a plethora of guides that answer your question more completely.

---

### Post by falconed7 on 2008-12-22
So I lose my file corrections if I place it into Windows? I think that's fine as it's only for my home server

How would I create a executable file?

I would prefer to be able to access the drive in windows also just incase. Would NTFS or even FAT32 be better for this?

---

### Post by jerome1232 on 2008-12-22
> **falconed7 said:**
> I would prefer to be able to access the drive in windows also just incase. Would NTFS or even FAT32 be better for this?

Well you could always install a ext2 driver for Windows, that way it can mount your ext3 disk as ext2 and pull the files off.

I wouldn't recommend ntfs or fat32 for backups just because those file systems don't support Linux style file permissions.

---

### Post by falconed7 on 2008-12-22
Okay I have use the simple line just to check if rsync worked:

```
rsync –av --delete /media/share /media/usbdrive/backup
```

Using [this page]("http://www.marksanborn.net/howto/use-rsync-for-daily-weekly-and-full-monthly-backups/") it says I can automate this proccess using Cron.

So to do weekly backups would I do the following:

```
crontab -e
```

and then add:

```
00 18 * * 5 rsync –av --delete /media/share /media/usbdrive/backup
```

Would this be okay?

---

### Post by chrisamiller on 2008-12-22
Yes, that works fine.  If you find your command getting longer and more complex (due to multiple excludes or whatever else), you can stick the command in a bash script:


```
#!/bin/bash
rsync &#8211;av --delete /media/share /media/usbdrive/backup
```

make it executable:
```
chmod +x bashscript.sh
```

then execute the script from cron
```
00 18 * * 5 bash /path/to/bashscript.sh
```

---

### Post by mdurham on 2008-12-22
rsync has a -n to do a dry-run to see what will happen

---


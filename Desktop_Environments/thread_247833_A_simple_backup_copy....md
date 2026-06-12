---
title: "A simple backup copy..."
date: 2006-08-31
forum: Desktop Environments
---

### Post by mmcmonster on 2006-08-31
Hi.
  I would like to create a simple backup copy of my data to an external hard drive.  I don't want any special formats (tar, etc.), since I will be accessing the backup in multiple different OSs.

So far I am using:
```

cp -r -p -v -u *source destination*

```

Anything better?  Anything I should look into?  I would love to use rsync, but don't know the IP addresses on both ends (and I don't have a static IP address, anyway).

---

### Post by tagra123 on 2006-08-31
rsync is a very good tool for making this kind of backup.

---

### Post by xyz on 2006-08-31
Hi-
That may help: [http://ubuntuforums.org/showthread.php?t=185761](http://ubuntuforums.org/showthread.php?t=185761)
It's the 2nd link of the 1st post.

---

### Post by mmcmonster on 2006-08-31
Will rsync work if I just turn on the external drive periodically?

Can you point me to a rsync tutorial for my situation?  (Sorry, google is giving me a lot of options on this .:-) )

---

### Post by Adler on 2006-08-31
I like this thread. I *want* to clone everything that I now have running and will be buying a new USB external drive e.g. 100Gb just to keep my system **cloned**.

I'm hoping this keeps *everything* going that I now use. Web sites, Servers, Databases, Permissions, cookies and bookmarks. I'm not the casual Desktop Linux user. LOL! Man, did I get burned recently. 

So, what is out there with a good GUI that tells me to sent *everything* to a different drive?

Adler

---

### Post by Lunar_Lamp on 2006-08-31
I use the following little script.  It will require a bit of editing to be of use, but I save it as "/usr/bin/home-backup".  To use it I just plug in my usb hard drive and mount it, then type "home-backup" and wait for it to finish.  It has some errors due to symlinked files, but they don't matter to me.  You will also maybe want to not exclude some of the directories I have excluded, and change what you are backing up (I back up my /home/ed partition onto /media/maxtor...).


```
#!/bin/sh

# rsync.sh
#
# - this script will back up /home/ed using rsync to maxtor hdd
# 
# - can be executed by user (no need for sudo/root access)
# 
# 
#Some explanation of the various rsync flags (info from rsync's man page):

# -v: verbose - this flag makes rsync tell you what files it's moving and gives a summary at the end
# -u: update - this forces rsync to skip any files for which the destination file already exists and has a date later than the source file 
# -r: recursive - rsync will mirror the directories you specified and all the directories inside them.
# -t: times - rsync will copy al the timestamps of the source files, so that the files on the external drive are exact replicas.
# --progress: rsync will tell you how many files need to be copied before it's finished. this is useful if you want to see what's going on.
# --delete: this tells rsync to delete any files on the receiving side that aren't on the sending side.

echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo " Backing up home directory, this may take some time depending on how long it was since you last backed up..."
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"

rsync -vurtpL --progress --delete --exclude=.kde/cache-PMSEH/ --exclude=.wine/ --exclude=.opera/cache* --exclude=.Trash/ --exclude=.icons/ /home/ed /media/maxtor/backups/home-backup

echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo "All done!"

```

---

### Post by Adler on 2006-08-31
> I use the following little script. It will require a bit of editing to be of use

Dah,

I'd like to clone my Box with a GUI, not play with scripts. Then find out later it did not work. Sorry to be so rude. 

Adler

---

### Post by Lunar_Lamp on 2006-08-31
I did find a couple of programs when I was looking around for myself, but I couldn't be bothered to put the effort into getting them to do what I wanted:

HUBackup (home user backup)
SBackup (simple backup)


If you want to clone a system though, I recommend partimage.

---

### Post by Adler on 2006-08-31
Lunar_Lamp,

Isn't this a little strange?

We, as Linux user, can't really keep everything safe? A Back-up Software has to be out there. Complete with GUI and chron job.

I can cut and paste my /Home to a seperate drive, but I loose everything e.g Workstation settings if I go through an update like I did. Mmmm...

Adler

---

### Post by mmcmonster on 2006-08-31
> **Lunar_Lamp said:**
> 
...
#Some explanation of the various rsync flags (info from rsync's man page):

# -v: verbose - this flag makes rsync tell you what files it's moving and gives a summary at the end
# -u: update - this forces rsync to skip any files for which the destination file already exists and has a date later than the source file 
# -r: recursive - rsync will mirror the directories you specified and all the directories inside them.
# -t: times - rsync will copy al the timestamps of the source files, so that the files on the external drive are exact replicas.
# --progress: rsync will tell you how many files need to be copied before it's finished. this is useful if you want to see what's going on.
# --delete: this tells rsync to delete any files on the receiving side that aren't on the sending side.

```

rsync -vurtpL --progress --delete --exclude=.kde/cache-PMSEH/ --exclude=.wine/ --exclude=.opera/cache* --exclude=.Trash/ --exclude=.icons/ /home/ed /media/maxtor/backups/home-backup

```


Thanks.  I'll give this a try.

---

### Post by tagra123 on 2006-09-01
> **mmcmonster said:**
> Thanks.  I'll give this a try.

I wrote this simple How To:

[http://www.ubuntuforums.org/showthread.php?t=240326](http://www.ubuntuforums.org/showthread.php?t=240326)


You can check the backup visually using the filemanager with the rsync options.  Might take a one half hour or so to set up for your machine. 

It's not a GUI but its fairly easy to use. Just follow the directions in the script.

---

### Post by iTrendsNET on 2006-09-15
Check this link for what is in store for Edgy.  Looks pretty good.

[https://wiki.ubuntu.com/HomeUserBackup](https://wiki.ubuntu.com/HomeUserBackup)

---

### Post by Adler on 2006-10-21
iTrendsNET,

Howdy!

I've just ran across hubackup @ Planet UBUNTU, and followed the link to [http://www.whiprush.org/2006/10/ahhh_backups.html](http://www.whiprush.org/2006/10/ahhh_backups.html). It **is** available in the Repos for 6.06, and I've just installed it.

I've not yet tried it out. But, will in the very near future.

Adler

---


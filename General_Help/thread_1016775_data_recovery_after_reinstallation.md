---
title: "data recovery after reinstallation"
date: 2008-12-20
forum: General Help
---

### Post by Ace_NoOne on 2008-12-20
First of all, my apologies for being yet another moron who can't take proper care of his data, thus taking up your time here.

In short (details below), I've lost quite a lot of data by repartitioning and then reinstalling Ubuntu, some of which I now hope to recover.
[Similar threads]("http://ubuntuforums.org/search.php?searchid=53376145") and [this article]("https://help.ubuntu.com/community/DataRecovery") suggest I should try *testdisk* and *gpart* - however, before rushing into this, I wanna make sure not to do more more harm in the process.

So how do I prevent automatically mounting my HDD when booting from the Ubuntu 8.10 live CD - and are there any other precautions I should take?
Should I maybe use something other than the Ubuntu live CD - e.g. [SystemRescueCd]("http://www.sysresccd.org/Main_Page")?

[*details*]
Before reinstalling Ubuntu from scratch* this morning, I ran my simple *rsync* script to back up my home dir to an external HDD - or so I thought.
For reasons I can't fathom, that script didn't actually update the data on the external drive, leaving me with two-month-old backups.
I foolishly didn't check the data integrity before wiping my laptop's HDD, immediately proceeding to make some adjustments with *gparted* (deleting and recreating the *ext3* and swap partitions, and also some resizing on another NTFS partition) and finally installing Ubuntu.
[/*details*]

FWIW, here are the directories I hope to be able to recover:
[LIST]
[*]~/Documents
[*]~/.mozilla-thunderbird
[*]~/.mozilla/firefox
[*]~/Scripts
[*]~/Dev
[/LIST]

Any help would be greatly appreciated!


* I didn't know much about Linux when I started a year ago, so I wanted a fresh start with a clean sytem

---

### Post by cdtech on 2008-12-20
Your drives wont be mounted using the Live CD. You would have to manualy mount the drives.

I'm not sure it's possible once you reinstall the OS. I hope I'm wrong though

Good luck.....

---

### Post by Ace_NoOne on 2008-12-20
Thanks for the quick response.

> I'm not sure it's possible once you reinstall the OS. I hope I'm wrong thoughI hadn't considered that this probably complicates things even more. Not quite sure what to do now...

---

### Post by jerome1232 on 2008-12-20
I don't think testdisk is what you want, but you might be able to file carve some of your data back.

One program that comes with testdisk is photorec, it can scan your hard disk and recover some data (only the stuff that wasn't overwritten with new data by the install though)

Another good program would be foremost, for both of these your going to need another hard drive that is as big as the one your recovering from (maybe a little smaller will work)

This resource should help you a bit with the process.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Ace_NoOne on 2008-12-20
Thanks - I'll give foremost and photorec a try in the morning (UTC).
Will let you know how it went then.

---

### Post by Ace_NoOne on 2008-12-21
After Foremost failed with a segmentation fault early on, I tried PhotoRec - which did indeed recover quite a large number of files.

However, the original filenames and directory structure are gone, so I essentially just have a massive amount of randomly-named files lying around.
I'm not quite sure what to do with those now - e.g. restoring my Thunderbird profile seems pretty much impossible at this point... !?

---

### Post by jerome1232 on 2008-12-21
> **Ace_NoOne said:**
> After Foremost failed with a segmentation fault early on, I tried PhotoRec - which did indeed recover quite a large number of files.

However, the original filenames and directory structure are gone, so I essentially just have a massive amount of randomly-named files lying around.
I'm not quite sure what to do with those now - e.g. restoring my Thunderbird profile seems pretty much impossible at this point... !?

If you look towards the bottom of that link I gave you it gives you some ideas on how to sort through the mess using various meta-data programs and search functions.

I doubt it got your thunderbird profile mostly these programs recover documents and media. (Foremost at least sorts the recovered files by type, photorec just slaps them into numbered folders)

Unfortunately once a file system has been formatted this is the only thing I know of that can recover the old data that was there.

---

### Post by Ace_NoOne on 2008-12-22
I have happy, yet embarrassing news to report:
Turns out my rsync script did not fail after all - it just backed up the data into a sub-directory of the home folder's backup directory (haven't looked into how this happened yet). I noticed this after giving up on the recovery and copying over the old backups (thanks to *cp -v*).
So I have my data back, in its entirety!

While these last two days have been agony, I consider it punishment for my stupidity...
Also, I've learned a lot in the process.

Many thanks for all your assistance!

---

### Post by unutbu on 2008-12-22
Oh, that is really happy news!

Regarding rsync: if you type
```

rsync -a /home/user /backup/user
```

then your data gets copied to /backup/user/home/user

But if you type
```

rsync -a /home/user[COLOR="Red"]/[/COLOR] /backup/user
```

then your data gets copied to /backup/user.

The forward-slash after /home/user makes all the difference.

---

### Post by Ace_NoOne on 2008-12-23
Thanks unutbu.

Turns out I had changed my rsync script, but didn't reorganize the backup drive accordingly...
FWIW, here's my script:
```
# check backup drive
if mount | grep 'on /mnt/backup' >/dev/null; then
	echo "starting backup process"
else
	echo "ERROR: backup drive not mounted"
	exit
fi

# log start time
STARTTIME=$(date +"%Y-%m-%d %H:%M:%S")

cd ~/Scripts/backup/
rsync -a -e -v --progress ~ /mnt/backup/foo/rsync/ --exclude-from="exclude.lst"

# output duration
echo "started: $STARTTIME"
echo "ended  : $(date +'%Y-%m-%d %H:%M:%S')"
```
The accompanying *exclude.lst* contains two entries:
```
.local/share/Trash
Downloads
```

---


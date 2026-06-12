---
title: "is sudo-copy  sufficiant for backing up an ubuntu install?"
date: 2009-06-16
forum: General Help
---

### Post by ouch67 on 2009-06-16
ok, Iafter the last distro update it completely trashed my install so that even the command prompt doesn't work right.

So what I want to do is back up the entire drive into an directory of an another much larger drive. This so I have a referance of what settings I altered, and to back up my crucial data. (I write software in ubuntu, so if I lose that stuff I'm totally screwed)

I know that in windows if you simply issue copy commands on the drive letter it skips tons of files windows hides reguardless of your permission settings. I was wondering if sudo copying the drive would copy ALL the files on the drive or if ubuntu won't copy certain files because they are hidden, need special permission, or have to be referanced directly to find them?

thanks in advance...

---

### Post by kpkeerthi on 2009-06-16
Use rsync. It does differential backup so its faster as it copies only the files modified since last backup.

```

sudo rsync -a /source/folder /target/folder

```

EDIT: It will copy all hidden files & folders unless you explicitly exclude them. See man rsync.

---

### Post by Legace on 2009-06-16
You could use rsync, like this:

```
sudo rsync -av --delete --exclude-from="***PATH***/exclude" / /target/folder
```

Where ***PATH*** is the directory where exclude is saved.

exlude should be like this (you don't need to back those up, you could backup /boot if you want):

```
boot/
proc/
dev/
lost+found/
sys/
media/
tmp/
```

Note that share/backup/ is the folder your system will be backed up to. If you decide to change that location, do so in the exclude file aswell.

To restore the backed up files, you would use:
```
sudo rsync -av --delete --exclude-from="***PATH***/exclude" /share/backup /
```

Note that this will take a while to complete.
Also note that after doing this once, the following times will be much faster (as it will update only changed files)..

---

### Post by eldragon on 2009-06-16
the most important fault in your approach is that sudo cp will destroy file ownership so its not a good idea for a backup

---

### Post by drs305 on 2009-06-16
I agree that rsync is an excellent way to back things up. Another is to take an entire disk image (for restoring when things go really bad). For this you can use partimage (for now not ext4 capable) or a terminal app like fsarchiver.

Note that *copy* does now have a switch which will preserve ownership/timestamps, etc: -p . I use it when making a separate /home partition and it works well. You can read about the -p switch in the man page "man cp".

---

### Post by Cheesemill on 2009-06-16
If I were you I'd take a look at something like [CloneZilla]("http://www.clonezilla.org/") to make a full backup image of your drive.

---

### Post by ouch67 on 2009-06-16
thanks folks, didn't know there was a far better way out there...

---

### Post by VMC on 2009-06-16
> **Cheesemill said:**
> If I were you I'd take a look at something like [CloneZilla]("http://www.clonezilla.org/") to make a full backup image of your drive.

Clonezilla is what I use. And it works with Ext4. Use the experimental version which is jaunty. Reason being it supports Ext4 mbr if you /boot is inside a Ext4 partition.

I tried FSarchiver and kept getting a few errors. Don't know the reason. Couldn't find a way to verify the backup either.

---


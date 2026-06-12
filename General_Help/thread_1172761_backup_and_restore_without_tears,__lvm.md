---
title: "backup and restore without tears,  lvm?"
date: 2009-05-28
forum: General Help
---

### Post by linuxgrrl on 2009-05-28
hello,
Looking for a way to back up my entire system that will be dead-simple to restore.  My pc has a / and /boot taking up half the main disk. The rest of that disk, plus a whole other one are partitioned with LVM to hold photos, videos, etc. Just bought a 1 TB drive in a USB enclosure to put the backups on.  After much research I am TOTALLY confused as to what method will work best for my backups.

Options I've looked at:
OPTION ONE -- using dd and rsync to create a "poor man's raid" as described here [http://users.telenet.be/mydotcom/howto/linux/diskfakeraid.htm](http://users.telenet.be/mydotcom/howto/linux/diskfakeraid.htm)

PROBLEMS with this: creating the initial image is taking 12 hrs plus and eventually the process seems to halt.  I can't figure out how to test the image or see if it is corrupt ... my BIOS does not support booting from USB, so unless I buy a whole 'nother internal hard disk to try it on, and grab a screwdriver, how can I restore my image and test whether it boots?

Also, I can't find any specific info on whether this method is compatible with LVM.  Will LVM choke if I restore the image to a new drive with different UUID?


OPTION TWO-- using "lvm snapshots" to back up the lvm partitions to a normal partition, then use dd plus rsync to back up the normal partitions, plus a separate step to back up the mbr.  DOWNSIDES: this seems too complicated to restore!  Let's say it's 4 years before my disk goes bad, am I even going to remember what the hell I'm supposed to do?  Do I have to then partition the new disk exactly as the old one was, or the whole thing fails? Also the "snapshots" documenation indicates it takes only a "few seconds" to make a snapshot, this seems odd. And same issue with testing as before, how do I safely test this?

OPTION THREE-- use mondo rescue -- this sounds almost too good to be true, claims to be compatible with LVM. In the fine print mentions that things "could" go wrong with LVM depending on your setup and you will need to manually partition the drive in order to restore. Maybe that would't be the end of the world, but can anyone comment on success with mondo and lvm or reliability of mondo in particular?  Or advise how I can test this approach.

Help, I'm so confused here!  There are probably even better methods I haven''t even thought of.
thanks,
Mary

---

### Post by VMC on 2009-05-29
> **linuxgrrl said:**
> hello,
Looking for a way to back up my entire system that will be dead-simple to restore.  My pc has a / and /boot taking up half the main disk. The rest of that disk, plus a whole other one are partitioned with LVM to hold photos, videos, etc. Just bought a 1 TB drive in a USB enclosure to put the backups on.  After much research I am TOTALLY confused as to what method will work best for my backups.

Options I've looked at:
OPTION ONE -- using dd and rsync to create a "poor man's raid" as described here [http://users.telenet.be/mydotcom/howto/linux/diskfakeraid.htm](http://users.telenet.be/mydotcom/howto/linux/diskfakeraid.htm)

PROBLEMS with this: creating the initial image is taking 12 hrs plus and eventually the process seems to halt.  I can't figure out how to test the image or see if it is corrupt ... my BIOS does not support booting from USB, so unless I buy a whole 'nother internal hard disk to try it on, and grab a screwdriver, how can I restore my image and test whether it boots?

Also, I can't find any specific info on whether this method is compatible with LVM.  Will LVM choke if I restore the image to a new drive with different UUID?


OPTION TWO-- using "lvm snapshots" to back up the lvm partitions to a normal partition, then use dd plus rsync to back up the normal partitions, plus a separate step to back up the mbr.  DOWNSIDES: this seems too complicated to restore!  Let's say it's 4 years before my disk goes bad, am I even going to remember what the hell I'm supposed to do?  Do I have to then partition the new disk exactly as the old one was, or the whole thing fails? Also the "snapshots" documenation indicates it takes only a "few seconds" to make a snapshot, this seems odd. And same issue with testing as before, how do I safely test this?

OPTION THREE-- use mondo rescue -- this sounds almost too good to be true, claims to be compatible with LVM. In the fine print mentions that things "could" go wrong with LVM depending on your setup and you will need to manually partition the drive in order to restore. Maybe that would't be the end of the world, but can anyone comment on success with mondo and lvm or reliability of mondo in particular?  Or advise how I can test this approach.

Help, I'm so confused here!  There are probably even better methods I haven''t even thought of.
thanks,
Mary

Have you tried [Clonezilla]("http://www.clonezilla.org/"). I don't know if it supports LVM. It's worth a try.

---

### Post by lindsay7 on 2009-05-29
I have used and really like "Acronis True Image Home 11" which is the newest version. You can install it on a windows drive or just use the cd if you like which is the way to use it if you just have Ubuntu on the system. 

You can back up the drive image of any partitions and it will handle systems with both windows and Ubuntu. I just restored a dual boot system with it and it was very easy.  You can also clone drive with it and do much more.

---

### Post by linuxgrrl on 2009-05-29
> **VMC said:**
> Have you tried [Clonezilla]("http://www.clonezilla.org/"). I don't know if it supports LVM. It's worth a try.

Just checked the website, and it does support LVM2 (which is what I have).  This looks very promising!  

Does anyone know if there is a way to test whether the image will boot, if one's bios does not allow booting from USB device?  Seems stupid to buy a whole bare drive just for testing purposes, but I'll do it if I have to.

---

### Post by unutbu on 2009-05-29
As far as know, the only sure way to test the backup image is
to grab a whole bare drive and put your restore procedure through its paces.

Could I interest you in changing your goal from an entire-system backup to a plain-text data backup? By "plain-text" I simply mean saving individual files as files, rather than as a single binary image. By "data backup" I mean saving only your personal data -- not the entire operating system.

Backing up an entire system as a binary image:
Pros:
[list]
[*] You can restore your system exactly
[/list]

Cons:
[list]
[*] 
[*]It is hard to test if your binary image is good. One error and your backup might be toast. A plain-text backup is more robust -- one error affects only one file
[*]Unlike a binary image, plain-text backup allows you to easily verify the integrity of your files. You can look at them whenever you want.
[*]It takes a lot longer to make a full backup image than it would making plain-text backup of data only. Not only is dd very slow compared to rsync, but also, after the first full plain-text backup, rsync can do very quick incremental backups because it only copies the differences.
[*]Restoring a single file from a plain-text backup is easy -- the task is impractical if all you have is a whole-disk binary image.
[*]Using abhiroopb's method [http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396), you can even reconvert all the packages on your system into debs for easy saving and restoring.
[*]Reinstalling Ubuntu from a LiveCD takes between 1/2 to 1 hours. Coupled with abhiroopb's method and a good data backup, you should be able to restore your system quickly and reliably.
[/list]

---

### Post by linuxgrrl on 2009-05-29
I hear ya, unutbu - that is quite a trade off.  in fact, up until last month i was doing exactly that ...using jungledisk to back up my data and config files.

Then the circuit board of my main drive died w/o warning. That is where the "tears" came in.  I realized that the years (really) I have spent tweaking ubuntu to be my perfect living room media box and server could not be replicated without days of work. Programs compiled from source and subtle hardware tweaks that I would not able to replicate. And my daughter was due to be born in 10 days! 

Thats where the clone urge is coming from. Thank you for pointing out the pitfall -- if one thing is wrong with the clone, I'd be hosed, and I can't test it.

I guess I'll make a clone every month or so but continue to back up all data using jungle disk!

---

### Post by unutbu on 2009-05-29
Hm. I understand better where you are coming from. 

How about this then:

Make a file called /root/exclude.txt with contents

```
/dev/
/proc/
/sys/
/backup/

```
Then mount the backup partition at /backup, and run
```

sudo rsync -av --delete --exclude-from="/root/exclude.txt" / /backup/
```

This will save all your custom compiled software, and still allow you the other benefits listed above.

To restore, boot a LiveCD, mount the backup partition at /backup and the root partition at /mnt and run
```

sudo rsync -av /backup/ /mnt/
```

To save a copy of sda's MBR and partition table, you simply do this:
```

sudo dd if=/dev/sda of=/root/MBR.img bs=512 count=1
```

and to restore, boot a LiveCD, mount the backup partition at /backup, and run
```

sudo dd if=/backup/root/MBR.img of=/dev/sda bs=512 count=1
```

In your first post did you say that rsync conked out on you, or was it dd?

The command "dd if=/dev/sda of=/dev/sdb" would be very slow on any drive of significant size.
```

dd if=/dev/sda of=/dev/sdb bs=10M conv=notrunc
```
would be faster. Still, I would not recommend using dd as your backup method.

---

### Post by bodhi.zazen on 2009-05-29
Have you looked at partimage ? I think it will do what you are wanting.

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

LVM is very nice, until it breaks. If it breaks it can be quite difficult to repair.

---

### Post by drs305 on 2009-05-29
+1 on partimage for ext3 (ext4 not enabled yet). If you want a gui, partimage is a fairly good program.

[http://www.psychocats.net/ubuntu/partimage]("http://www.psychocats.net/ubuntu/partimage")

[http://www.psychocats.net/ubuntu/partimage]("http://www.psychocats.net/ubuntu/partimage")

I run it from a [SystemRescueCD]("http://www.sysresccd.org/Main_Page")

---

### Post by linuxgrrl on 2009-05-29
> **unutbu said:**
> 

To save a copy of sda's MBR and partition table, you simply do this:
```

sudo dd if=/dev/sda of=/root/MBR.img bs=512 count=1
```

and to restore, boot a LiveCD, mount the backup partition at /backup, and run
```

sudo dd if=/backup/root/MBR.img of=/dev/sda bs=512 count=1
```


This is intruiguing. I take it this will replicate the partitions on the new disk in one fell swoop.  Will it work properly with LVM? 

> 
In your first post did you say that rsync conked out on you, or was it dd?
I would ignore the dd command posted at [http://users.telenet.be/mydotcom/howto/linux/diskfakeraid.htm](http://users.telenet.be/mydotcom/howto/linux/diskfakeraid.htm) -- the author must never have tried his own advice. The command "dd if=/dev/sda of=/dev/sdb" would be very slow on any drive of significant size.


dd conked out, but in fairness I forgot to exclude the /mnt for the usb drive, so maybe I got it stuck in some kind of loop?

Anyway, both the rsyn approach and Partimage sound very promising.  

I hope I can be a warning to others, following up the above story: I ended up spending USD 600 to fix the hard drive, because this was preferable to saying goodbye to my beloved mythtv box, and there was no way I would ever have time to rebuild it.  So if you are considering whether it's worth it to buy a $ 200 backup drive -- which I was too cheap to do before -- YES, it is worth it!

---

### Post by bodhi.zazen on 2009-05-29
partimage is run from a live CD and it breaks the image into 2 Gb files which can be put on a DVD. If you zero our your HD first and compress your image you should be able to back up w/o much in the way of additional expense.

Finally, FYI, when restoring from back up you must use the same geometry (partition size) on your back up.

You can also pipe dd through gzip to compress the raw image.

---

### Post by linuxgrrl on 2009-05-29
> **bodhi.zazen said:**
> 

Finally, FYI, when restoring from back up you must use the same geometry (partition size) on your back up.



Not sure I understand. Does this mean I would manually re-create the same partition structure on the new drive? It's several partitions(including swap, /home, etc), some regular, some LVM.  Does partimage restore them all at one go, or do I have to restore each one separately (hence the name "partimage")

I just have this sneaking fear that LVM would choke somehow, and still notice that it's a different disk.  Maybe Im just paranoid.

---

### Post by drs305 on 2009-05-29
You would make an image of each partition with partimage. If you had separate /home or /boot or data partition, you would make an image of each one, [COLOR="DarkRed"]designating each one by the sdXX identifier[/COLOR]. 

One good thing about partimage is that although it "clones" the partition, it doesn't include free space. The image not only is smaller with compression but it also doesn't include free space in the backup although the free space is restored when the image is.

---

### Post by unutbu on 2009-05-29
Edit: Regarding LVM there is too much I don't know, so I am retracting what I wrote earlier.

---


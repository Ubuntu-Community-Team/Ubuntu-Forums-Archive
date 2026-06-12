---
title: "How to clone Dell Vostro A90 / Mini 9?"
date: 2009-05-23
forum: General Help
---

### Post by The Jinx on 2009-05-23
Hi,

I've just recently purchased a Dell Vostro A90 which came shipped with the Dell Version of Ubuntu 8.04. I was wondering how do i go about cloning my SSD to an external flash drive or hdd so I have something to fallback to if the NBR 9.04 install fails on me.


Thanks,
Jinx

---

### Post by The Jinx on 2009-05-24
Bump?

---

### Post by Legace on 2009-05-24
You could use rsync to backup the entire system (excluding /boot, /proc, etc.) and then restore from recovery mode if something goes wrong.

The command to backup would be
```
rsync -av --delete --exclude-from="exclude" / [COLOR="Red"]PATH_OF_YOUR_EXTERNAL_DRIVE[/COLOR]
```

~/exclude would look like:
```
boot/
proc/
dev/
lost+found/
sys/
media/
tmp/
```

The command to restore would be
```
sudo rsync -av --delete [COLOR="Red"]PATH_OF_YOUR_EXTERNAL_DRIVE[/COLOR] /
```

---

### Post by radi0j0hn on 2009-05-24
I don't have a Dell, but on my Asus (and ANY PC I've owned) there is either a CD or software on the drive to create backup disks. Was this purchased new or used?  If new, there should be some option to restore the drive.

Another way would be to DL Clonezilla as an ISO, burn a CD of it and boot from that (assuming you have an external USB drive to use).  Then you can save an exact image to another drive or perhaps a thumb drive.

---

### Post by The Jinx on 2009-05-24
would something like **macrium reflect** fit my needs? or is that only for windows partitions?

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

---

### Post by VMC on 2009-05-24
> **The Jinx said:**
> would something like **macrium reflect** fit my needs? or is that only for windows partitions?

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

First time I've heard of Macrium. It doesn't support Ext4. I don't know what FS your Dell has. 

I would use [Clonzilla]("http://www.clonezilla.org/") or [Parted Magic]("http://partedmagic.com/") myself. There's few backup programs on thoe distros - Partclone, partimage, FSArchiver. partclone, fsarchiver will clone ext4.

The difference between these newer programs and the older Unix dd/tar/rsync is speed, size.

Coming from Windows Acronis True Image and Ghost , I find the ones I mentioned the best - for me.

---


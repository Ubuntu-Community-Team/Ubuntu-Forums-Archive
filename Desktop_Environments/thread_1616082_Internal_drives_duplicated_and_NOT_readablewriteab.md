---
title: "Internal drives duplicated and NOT readable/writeable"
date: 2010-11-07
forum: Desktop Environments
---

### Post by yonkiman on 2010-11-07
I just upgraded from 9.10 to 10.10 and simultaneously added 4 new hard drives.  

However I can not read or write to any of the disks (without sudo).  They are also showing up twice (mounted and removable on top, unmounted underneath) in the "Places" menu.  Of course I want them to be mounted, not removable, R/W'able , and only show up once.

Here'a a screenshot of where I'm at:
[IMG]http://www.yonkitime.com/ubuntu1.png[/IMG]

I believe I set up fstab correctly:
```
# /
UUID=4204d07b-c450-4461-a001-1ef6d4ecb1a3 / ext4 errors=remount-ro 0 1

# swap 
UUID=bd1aaecb-ab8c-4f44-ab22-fe25893f671b none swap sw 0 0

#DVD/CDROM
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

# All the big drives
UUID=e35e96e6-de21-4af2-b8f9-a9a64110df24 /media/disk0 ext4 auto,rw,user,relatime,noatime,nodiratime,async 0 2
UUID=7b6555e4-3e9e-4ce8-a4af-e44a1e6f62d2 /media/disk1 ext4 auto,rw,user,relatime,noatime,nodiratime,async 0 2
UUID=d82087de-c729-4111-b1b2-40759dced35d /media/disk2 ext4 auto,rw,user,relatime,noatime,nodiratime,async 0 2
UUID=bf79b05a-9b9c-4ed0-bf53-a9e85d01a52c /media/backup0 ext4 auto,rw,user,relatime,noatime,nodiratime,async 0 2
```

And I also set up samba:
```
[disk0]
comment = Disk 0
path = /media/disk0
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup
```

Any ideas?

---

### Post by yonkiman on 2010-11-07
Part of it is a permissions issue.  I was able to get R/W access with the combination of:

  sudo chown -R fred:fred /media/disk0
and
  sudo chown -R 666 /media/disk0

on each drive.

I still don't know why the drives are duplicated and considered removable...is it because they are mounted under /media and not /mnt?  I'll try that next...

---

### Post by yonkiman on 2010-11-09
Bump - surely this must be a common problem?

---

### Post by mcduck on 2010-11-09
The drives getting automatically mounted sounds like your fstab configuration is wrong (so it's not actually used) and the drives are automounted instead. The drives show twice because you still have the mountpoints in /media.

Try using simpler options in fstab first. Replace all the options you now have with "defaults" to see how that works out. Also I'm quite sure you can't have both "relatime" and "noatime" at the same time...

---

### Post by yonkiman on 2010-11-09
> **mcduck said:**
> The drives getting automatically mounted sounds like your fstab configuration is wrong (so it's not actually used) and the drives are automounted instead. The drives show twice because you still have the mountpoints in /media.

OK, I sorta get that - but I'm not sure if the "right" thing to do is have them automounted or not.  Are you saying that if fstab is correct, automounting will not occur, and that is the preferred way to mount drives?

> Try using simpler options in fstab first. Replace all the options you now have with "defaults" to see how that works out. Also I'm quite sure you can't have both "relatime" and "noatime" at the same time...

Oops.  Yep, "defaults" seemed to eliminate the duplication.  The "Places" menu now just shows each drive once.  However they still show up as removable (at least "ejectable") in Nautilus.  I can live with that if that's normal, not a big deal.

However Nautilus is also showing (and if I click on it, creating a /media directory for, mounting, and working with normally) an old partition that I don't mention anywhere in fstab or have a /mount directory for.  I assume this is the automounting behavior you mention.

Is there a good resource that talks about fstab and automounting?  All the fstab reading I've done doesn't mention automounting behavior.  I'd like to understand all this better.

Thanks for your help, mcduck!

---

### Post by mcduck on 2010-11-09
Automatic mounting doesn't use fstab (that's why it's "automatic"). And yes, any drives/partitions that are mountable but aren't configured in fstab (or have bad configuration there) will be automounted. And if the drive *is* in fstab, the automatic mounting should leave it alone.

The autmounting is the same that allows you to do stuff like plugging in thumbdrives and accessing them without having to configure them in fstab or run terminal commands to mount them. I believe it's handled by gnome-volume-manager but I must admit I don't know much details about how it works as it seems pretty reliable and all the problems tend to be on the non-automatic side (bad fstab configurations)

I'm not sure about the drives showing as removable, it could be related to them being mounted in /media. I always mount my internal drives in /mnt instead to keep things cleaner (and to avoid them showing on the desktop together with removable drives).

(and no, I wouldn't say either way of mounting drives is preferable. Each have their own benefits and you'd usually use them for different drives. fstab for internal drives that are always mounted rt that you wish to configure in more detail, and automatic mounting for removable drives).

---

### Post by yonkiman on 2010-11-09
> **mcduck said:**
> Automatic mounting doesn't use fstab (that's why it's "automatic"). And yes, any drives/partitions that are mountable but aren't configured in fstab (or have bad configuration there) will be automounted. And if the drive *is* in fstab, the automatic mounting should leave it alone.

OK, that makes senses and is all I need know.

> I'm not sure about the drives showing as removable, it could be related to them being mounted in /media. I always mount my internal drives in /mnt instead to keep things cleaner (and to avoid them showing on the desktop together with removable drives).

I was doing a bit of reading, and it's seems like the origin of the two points is:

/media = removable drives
/mnt   = temporary mounting ([for example]("http://www.linfo.org/mnt.html"))

It seems like there is no standard for non-removable, permanent drives, or perhaps /mnt has evolved into that.

I guess the third option is to mount as /disk5, but then it shows up as a directory, not a disk.

OK, I guess that's all I need to know - thanks again!

---

### Post by mcduck on 2010-11-09
well, there really is no rule apart from /media being for removable drives.

There's nothing saying that /mnt would be for temporary mounting only, on the other hand it's actually common practice to mount your additional drives inside /mnt. Of course you can mount them anywhere you want them.

(when talking about temporary mounting to /mnt, that would usually mean mounting the drive *directly as /mnt*, not mounting drives inside it. And even then the only reason to do that would be that you wouldn't want to create a temporary mount point somewhere else and destroy it afterwards. Might make sense if you mount random drives all the time, but in other cases you can definitely mount anything you want inside /mnt).


edit: the page you linked is pretty old, notice how it actually talks about temporary mounting of USB drives, cd-roms, floppy disks and such into /mnt. Now we have /media for that. So /mnt really is free for you to use as you wish, and as correct place to mount your extra drives as anything can be.

---

### Post by pravinbravi on 2011-12-20
> **mcduck said:**
> Also I'm quite sure you can't have both "relatime" and "noatime" at the same time...

Yes having both "relatime" and "noatime" options set simultaneously is quite ok (applies exclusively only to ext2/3/4 filesystems). Although I do not see the merit in doing so.

Refer:  [http://linux.koolsolutions.com/2009/01/30/installing-linux-on-usb-part-4-noatime-and-relatime-mount-options/](http://linux.koolsolutions.com/2009/01/30/installing-linux-on-usb-part-4-noatime-and-relatime-mount-options/) ([]("http://linux.koolsolutions.com/2009/01/30/installing-linux-on-usb-part-4-noatime-and-relatime-mount-options/")[http://linux.koolsolutions.com/2009/01/30/installing-linux-on-usb-part-4-noatime-and-relatime-mount-options/](http://linux.koolsolutions.com/2009/01/30/installing-linux-on-usb-part-4-noatime-and-relatime-mount-options/))

Option "relatime" is a compromise between"atime" and "noatime". However, if the drives are external like in external USB HDD or something like that and used to store data or backups, I would suggest using "noatime". This would cut down on the R/W operations on the external HDD - which is a cause for failure - typical disk access light flashing/blinking issue. In newer kernels mount defaults to "relatime" anyways. My fstab entry for such a drive would look like this:

```
UUID="yourDriveUUID#"   /mnt/YourExtHD    ext4    defaults,noexec,noatime    0    2
```And as for the drives mounted as removable, instead of mounting from within /media/, try mounting them from within /mnt/ instead - persistent mount. I think so. Hope this helps.

---


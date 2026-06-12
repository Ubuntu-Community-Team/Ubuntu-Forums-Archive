---
title: "help with automounting drives"
date: 2009-05-02
forum: General Help
---

### Post by noremaku on 2009-05-02
I've looked at many other threads regarding this issue and I haven't found a solution yet. Basically I have two other partitions, NTFS and FAT32, that I want automounted for various reasons including to share Firefox profiles with Windows. I tried PYSMD but no matter how I configured it, including setting the owner to my user and to various groups, I couldn't write to it (also not able to use the firefox profile). So I resorted to editing the fstab, but I ended up with the same problem. I verified every time by checking the properties of the drive/folder and sure enough I was the owner with read/write permissions, but it still wouldn't let me write. The only time it lets me is if I delete the fstab entries and mount it myself, manually, like I did before.

---

### Post by Zimmer on 2009-05-03
[http://ubuntuforums.org/showthread.php?t=1142136](http://ubuntuforums.org/showthread.php?t=1142136)
The two responses here might give you some help,
> 
So I resorted to editing the fstab, but I ended up with the same problem. I verified every time by checking the properties of the drive/folder and sure enough I was the owner with read/write permissions, but it still wouldn't let me write.

or, the documentation on fstab...
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

since if you got the syntax/options etc wrong in fstab then the disk may have been mounted with the wrong permissions.

(Personally, I use the DISK MOUNTER gnome-applet and leave my other partitions unmounted most of the time..)

---

### Post by dE_logics on 2009-05-03
You tried chown?

```

sudo chmod <username> <path where you wanna mount the partition>

```

Give this treatment to the 2 folders.

Ok...you tired that...sorry.

---

### Post by noremaku on 2009-05-03
I read the Fstab documentation, fine-tuned my entries, and at this point the ntfs auto-mounts and operates fine (I can write to it) but the fat32 still does not. The ntfs I used the option defaults, for the fat32 I have used (unsuccessfully):
UUID=4E51-8276	/media/Shared	vfat	defaults	0	0

with the following options, again unsuccessfully:
defaults
defaults,user
defaults,rw
defaults,user,rw
defaults,sync
user
user,rw
defaults,user,dmask=027,fmask=137

Yes, I tried chmod,  and yes, I made sure the directory existed before mounting, and yes, the UUID is correct.

---

### Post by kayvortex on 2009-05-03
Post the syslog (Go to System -> Administration -> System Log, and then go to "syslog", type Ctrl-a and then Ctrl-c to copy it). There might be something useful in there.

Also, you could try typing
```
mount
```
into a terminal (no sudo required) and verify how the partitions are being mounted.

---

### Post by noremaku on 2009-05-03
Problem solved!
I manually mounted it (without the fstab entry) like I know works, and used the mount command in terminal to see how it was mounted, then copy and pasted the options into the fstab entry:

rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush

and it now works as intended. Thank you all!

---


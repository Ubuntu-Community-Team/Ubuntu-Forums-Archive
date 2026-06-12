---
title: "gksudo mount (FAIL)"
date: 2011-03-05
forum: Desktop Environments
---

### Post by tetris11 on 2011-03-05
Hi, I looked for previous threads with my problem, but nothing specific for my problem, and my problem's fairly general...

I can't mount my sdb2 partition for some reason. It works fine when I do through the gnome (Places->[my-disk]), but it fails to mount when I try it from a bash script, namely:
```
gksudo mount /dev/sdb2 /media/Hershey
rhythmbox-client

``` where Hershey is my music partition.

I've checked on gparted, and it's definitely the sdb2 partition:
[IMG]http://img843.imageshack.us/img843/2559/screenshotysfc.png[/IMG]

It makes the wierd disk-mounting noises that it normally would, but then just fails....

...any ideas?


Edit: in mtab it lists the partition as:
```
/dev/sdb2 /media/Hershey fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
``` when I mount it normally. So why doesnt it work from bash?

---

### Post by mcduck on 2011-03-05
Is the drive configured in /etc/fstab? It it isn't, you need to specify the file system and mount option in the mount command.


Try this in a terminal:
```
sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sdb2 /media/Hershey
```

---

### Post by ajgreeny on 2011-03-05
It is definitely **sudo** for the mount command, not **gksudo**, so try the suggestion by mcduck.  gksudo is for gui applications only, and sudo is for command line.

---

### Post by tetris11 on 2011-03-05
Hey thanks for the reply guys,

@ajgreeny - I needed to use gksudo so that I can execute the script from a keyboard combo. (Also I dont know how to feed in my password automatically with sudo in the script...:()

@mcduck - yeah it's not in fstab, but when I tried out your command it threw an interesting error "fuse: failed to access mountpoint /media/Hershey: No such file or directory". Which is strange cos /media/Hershey is definitely there...

---

### Post by tetris11 on 2011-03-05
....Nope. No it definitely isn't there - whoops! Sorry about that.

Just created it now and everything seems to be working fine now. Thanks for the correct mount code mcduck!

And ajgreeny, if you know a way for me to feed in my password automatically to sudo - please let me know! Using gksudo just to listen to my music is a hassle....

---

### Post by mcduck on 2011-03-05
> **tetris11 said:**
> ....Nope. No it definitely isn't there - whoops! Sorry about that.

Just created it now and everything seems to be working fine now. Thanks for the correct mount code mcduck!

And ajgreeny, if you know a way for me to feed in my password automatically to sudo - please let me know! Using gksudo just to listen to my music is a hassle....

Gksudo works just fine for command-line apps as well if you need a graphical dialog for entering the password.

(the important thing is that you should always use gksudo for GUI apps, as sudo doesn't handle them correctly. But there is really no reason why the opposite wouldn't work.)

On the other hand you could just configure the drive in fstab to get it to mount automatically on boot, or add "users,noauto" to it's mount options to stop it from mounting at boot but allowing normal users to mount it without requiring a password.

edit: Here's a couple of good guides if you choose to go for the fstab route:
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")
[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by tetris11 on 2011-03-05
> **mcduck said:**
>  or add "users,noauto" to it's mount options to stop it from mounting at boot but allowing normal users to mount it without requiring a password.
Now that Im gonna definitely try! Thanks a bunch man!

---


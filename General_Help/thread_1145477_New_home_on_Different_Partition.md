---
title: "New /home on Different Partition"
date: 2009-05-01
forum: General Help
---

### Post by Drunky on 2009-05-01
I've been reading [this article]("https://help.ubuntu.com/community/Partitioning/Home/Moving") on placing a /home directory on a different partition after having installed Ubuntu.

I don't have any problem with the mechanics of this process.

My questions is how does this *really* affect the user's /home directory?  and how does this affect *other* user's /home directories?

The above mentioned (and really all tutorials I can find) seem to just create a new directory on a different partition and name the directory as "/home".  But if I typed:
```
cd $
```

where would this take me?  Still to my /home on the original partition?

Wouldn't I have to manage the user and moderate the /home directory there ala...

[IMG]http://www.techotopia.com/images/3/38/Ubuntu_linux_user_advanced.jpg[/IMG] ?

---

### Post by Drunky on 2009-05-01
I answered my own question with [this article.]("https://help.ubuntu.com/8.04/installation-guide/hppa/directory-tree.html")

By setting up the /home directory in fstab then *that* is where it looks for that directory...even though there was one before under the root /.

Of course the original /home is now /home-backup or /home-restore or whatever it was copied/moved using the mv command so there is now only one /home directory.

Sorry about that.

---

### Post by ajgreeny on 2009-05-01
I have only done it once and it was no real problem to me except when copying files from another OS's partition (I often run more than one linux distro, together with winXP).  In that case, if I remember correctly the copy command was not as simple as usual, but involved the full pathway with /media/disk/username, or something very similar.  Maybe I just misunderstood how to do the separate home properly, and could have made it easier.

Anyway, I no longer bother with that as it is so simple to backup all my data files and I don't worry about keeping config files when I upgrade the distro, as I have found it to be easier to start again fresh, and it takes about 5 minutes to do now I know my way around the system.

As for other users, they will be on the same partition as you, so if you are on a separate partition, they will be as well, but I don't think you would need to do anything manually when you set them up.

---


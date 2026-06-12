---
title: "Permissions problem with a hard drive"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Jujimufu on 2005-10-17
Upon installation, Breezy automatically mounted one of my sata data drives *(just data, no OS on this drive).*  It's formatted as fat32 so it can recognize it, it can even write to it - but one problem: **It can only write and modify the files as root through terminal** *[color=gray]sudo su - this - that etc[/color]*.

I tried chmod and chown - but it just doesn't work / not even an error message.  It's currently owned by the root user and set to 755 file permission and won't change.  Finally, the etc/fstab file looks like this:

```
/dev/sda1       /media/sda1     vfat    defaults,users,auto        0       0
```

WHY CAN'T THE NORMAL USER ACCOUNT WRITE TO THIS DRIVE?! NEHHH!!... : (

---

### Post by KingBahamut on 2005-10-17
You can try adding a umask=0755 in place of Auto, to give that permissions set. 

Reboot and retry.

---

### Post by Jujimufu on 2005-10-17
Ah thanks, but it actually made it unreadable.  I should have used the search function - sorry.  I found this to be helpful:

[http://ubuntuforums.org/showpost.php?p=355988&postcount=8](http://ubuntuforums.org/showpost.php?p=355988&postcount=8)

A umask=000 worked instead.

---

### Post by tristure on 2005-10-17
Well, you're lucky!

I tried everything I found on the forums and nothing works!!

My fstab line is :

/dev/hdb5       /mnt/tristan    vfat    rw,user,umask=000       0       0

I tried with/without user, with users instead of user, with/without rw, with and without umask!!!!
And still I get those awful r-x permissions whenever I mount the partition!

If I umount it, though, the /mnt/tristan folder appears as a rwx one.

What's strange as well is that when it's mounted, the "last modified" date which appears is 01/01/1970 01:00, instead of the current time, which reappears when the folder is unmounted.

It doesn't happen that way with other mount point?

I'm sorry, but I have to say it to evacuate frustration ;)  :  it sucks.

Wow I feel better. Now I would be grateful if any of you had some advice to solve this...
Thanks a lot.

---


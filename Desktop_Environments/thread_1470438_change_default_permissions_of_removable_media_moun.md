---
title: "change default permissions of removable media mounted via nautilus"
date: 2010-05-02
forum: Desktop Environments
---

### Post by qorron on 2010-05-02
behavior in 9.04:
plugged in a disk, mounted it and it as readable to the world.
this is intended because it is shared via samba.

behavior in 10.04:
the disks have 700, meaning, they are not readable by samba.
this is a problem.

this is the best solution I've found so far:
[http://www.mail-archive.com/ubuntu-uk@lists.ubuntu.com/msg10951.html](http://www.mail-archive.com/ubuntu-uk@lists.ubuntu.com/msg10951.html)
except, that the mentioned means to fix this are gone.
(gconf-editor -> ..., storage  and preferences -> removable media)

after 3 hours of googleing and reading I'm rather upset about this bug.

so please, if you are thinking of suggesting fixed entries in the fstab or anything else that will not work with every media that is plugged into this box, just close this tab.
thank you very much.

---

### Post by qorron on 2010-05-03
If I would just know the name of the mechanism that does the mounting now. It would help a lot. (so I can check the config files or hack something if I have to)

As I have learned already, gnome-volume-manager was responsible for this. But this application has been replaced with something else.
And I have no idea with what.

---

### Post by Morbius1 on 2010-05-03
I do not know the answer to your question but I would like to know as well.

There is a workaround for your samba question until someone answers your specific question.

If , for example, the device mounts with owner = morbius and mode = 0700 then you can add a line to smb.conf:

```
force user = morbius
```Place it in the [global] section if you are using nautilus-share or in the share definition section itself if you are using classic-share. Then restart samba.

The "force user" parameter will act as a mask to convert the remote user ( after whatever authentication scheme you're using allows entry ) to you as far as that share is concerned.

---

### Post by qorron on 2010-05-03
Thank you very much!

This solution works quite as well for me as having 0755 on the mount.

I'm the only user of this box ant the (read only) samba share is for the network based media player (or guests, that want to copy something)

Why dou you need to change the permissions?
maybe I know a work-around for you :)

---


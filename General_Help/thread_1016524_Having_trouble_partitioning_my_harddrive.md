---
title: "Having trouble partitioning my harddrive"
date: 2008-12-20
forum: General Help
---

### Post by ninjaaron on 2008-12-20
Hey, I'm pretty much a linux newb, and I don't know a ton about computers.

Anyway, I'm using Ubuntu exclusively macbook these days, and there is a tweak to get it to load faster at startup. This requires a new hardrive partition. Ok, fine. Installed the Gnome Partition editor. There is the main partition, and then a little one that I don't really understand.

Anyway, I tried to unmount the main partition so I could make a new one. It won't let me unmout.

The error message says:

> Could Not Unmount /dev/sda1

This partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.


So yeah, I don't know what to do. I would post a screenshot, but photobucket is behaving strangely.

---

### Post by adult swim on 2008-12-20
you cant unmount the partition if you are running ubuntu off of you hard drive.  you will need to boot the live cd and then try.

---

### Post by ninjaaron on 2008-12-20
> **adult swim said:**
> you cant unmount the partition if you are running ubuntu off of you hard drive.  you will need to boot the live cd and then try.

Thanks.

Will try.

---

### Post by ninjaaron on 2008-12-20
Ok, I have no idea how to create a new partition with the live CD, short of re-installing ubuntu.

I just want to make a single small partition and install refit on it.

---

### Post by adult swim on 2008-12-20
to do that boot the live cd and choose try ubuntu.  once its up go to a terminal and enter in ```
sudo gparted
```

---

### Post by ninjaaron on 2008-12-20
That seemed to work. However, when I clicked apply they were like 'this could screw up your data, so it should be backed up.'

I got a little squeamish about this, as I have accidentally formated my hard drive before. I will give it another try next week, after I get my external hard drive, and have my stuff backed up.

Thanks for all of your help though.

---


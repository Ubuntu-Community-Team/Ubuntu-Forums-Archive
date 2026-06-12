---
title: "Restore smb.conf from live CD - mount issue..."
date: 2008-12-18
forum: General Help
---

### Post by andonato on 2008-12-18
Hello all, first post from this total n00b. I am having a couple of issues so any help is appreciated. I was attempting to configure Samba and must have made a mistake in editing smb.conf because my system now hangs on boot. It will get to the "Loading Samba Daemons" part and just hang forever. Tried control+c and that didn't work. So I figure I have to restore smb.conf from my live cd. Poking around here on the forum, I learned that I will need to mount the live cd to the partition where my system files reside with something like this: 

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
```

The problem is that /dev/hda1 isn't right. I have tried mounting to other directories and I keep getting the "xxx is not a block device" error. How can I determine where to mount the live cd?

I'm going crazy here, and like I said I'm new to this so I realize that any/all of what I said above could be wrong. Any suggestions are welcome, and thank you.

---

### Post by andonato on 2008-12-19
Please...any ideas?

---

### Post by andonato on 2009-03-02
Just to wrap this thread up, I ended up doing a reinstall, so problem fixed (kind of!).

---


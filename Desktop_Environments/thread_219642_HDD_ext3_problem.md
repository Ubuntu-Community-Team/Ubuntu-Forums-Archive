---
title: "HDD ext3 problem"
date: 2006-07-20
forum: Desktop Environments
---

### Post by Flavian on 2006-07-20
Hi.
I just set up my PC from and formated my 2 HDDs with the ext3 file format.
And guess what, it says that I do not have write permissions!
Why is that? Have I done something wrong, or do I have to enable the write permission first?

Thanks for help!
Flo

---

### Post by halfvolle melk on 2006-07-20
Did you use "sudo mkfs" or something like that? You're probably not the "owner" of the drives. "sudo chown -R username /mountpoint" or "sudo chown -R username /dev/hd?x" should fix this. Adjust "hd?x" to your needs. Do NOT do this to any system partitions!

---

### Post by Flavian on 2006-07-21
I set up the system from scratch. The two HDDs were NTFS before and I formatted them as ext3. Now I wanted to copy the data on them again, but they don't seem to be accessable.
Weird! There is only one folder on each of them, called "lost+found"

Thanks halfvolle but your advice didn't work :(
Do you have other suggestions!

Thanks
Flo

---

### Post by Flavian on 2006-07-24
Can anyone help please :( ?
I simply have NO idea!

---

### Post by halfvolle melk on 2006-07-26
Can you post the output of the following?
```
ls /dev/hd*   # for IDE drives
ls /dev/sd*   # for SATA/USB/? drives
```
and
```
cat /etc/fstab
```

---

### Post by Jivicin on 2006-07-26
> **halfvolle melk said:**
> Did you use "sudo mkfs" or something like that? You're probably not the "owner" of the drives. "sudo chown -R username /mountpoint" or "sudo chown -R username /dev/hd?x" should fix this. Adjust "hd?x" to your needs. Do NOT do this to any system partitions!

Make sure you've made yourself owner of the two HDDs first (see above).  If you still can't write to the disks, try:

```
sudo chmod 755 -R /mountpoint
```

You'll probably need to do that for each disk.  If 755 doesn't work try 777.

---

### Post by Flavian on 2006-08-01
I got it working, thanks friends :)
was chown did work, after several tries.

Flo

---


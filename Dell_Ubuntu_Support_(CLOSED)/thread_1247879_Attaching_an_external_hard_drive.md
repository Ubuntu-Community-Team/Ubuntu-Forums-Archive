---
title: "Attaching an external hard drive"
date: 2009-08-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by daisy91 on 2009-08-23
Hi all ! I have a new Dell Mini 12 with Ubuntu (obviously !) on it. I am trying to attach an external Seagate 250gb portable hard drive with very little success.

I have tried -

sudo mount -t ntfs-3g /dev/sdd1/media/expansion drive -o force

as per the help when  I attached it (which failed)....

Can someone explain the command and why it doesn't seem to attach the drive ?:(

---

### Post by mikewhatever on 2009-08-23
Why not simply go Places and look for new partitions in the left panel? You can also do it from CLI, but why?

---

### Post by daisy91 on 2009-08-24
Mikewhatever, what I am trying to do is move a load of files from the internal drive onto the external, which appears as an external drive in Places, but whenever I try to drag/drop files onto it in Places, I get the mount failure !:confused:

---

### Post by khelben1979 on 2009-08-24
Open up a file manager which have super user priviliges (root) and try the same thing and report back if it works.

---

### Post by doas777 on 2009-08-24
does the directory in your /media/ already exist? also drop the space in your path. thats a big no-no. I've replaced it with an underscore. that is likely your problem. mount thinks that "Drive" is the first parameter not part of the dest path. you could also correct it by quoting the path. also you were missing a space between the device ID and the dest path.

try that
```
sudo mkdir expansion_drive
sudo mount -t ntfs-3g /dev/sdd1 /media/expansion_drive

```

---

### Post by mikewhatever on 2009-08-25
> **daisy91 said:**
> Mikewhatever, what I am trying to do is move a load of files from the internal drive onto the external, which appears as an external drive in Places, but whenever I try to drag/drop files onto it in Places, I get the mount failure !:confused:

I didn't say you could drag and drop files onto anything in Places. By default, the external drives should automount on connection, if yours doesn't the filesystem may need checking.

---

### Post by daisy91 on 2009-08-27
All,
 
Thanks for the suggestions........I sorted it as I guessed that the drive may have been attached at some point to a Windows PC during manufacture and then just unplugged after testing. I reattached it to a PC, Unmounted it 'properly' and then plugged it back into my Dell Mini..........Bingo !

---


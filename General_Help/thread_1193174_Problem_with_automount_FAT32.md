---
title: "Problem with automount FAT32"
date: 2009-06-21
forum: General Help
---

### Post by celticbhoy on 2009-06-21
I have a small problem with a shared partition formated to FAT32. In Windows 7, and Karmic the partition mounts as SHARED, in Jaunty the partition automounts as Shared - note the different capitalisation. I realise this might not seem like a big deal, but I have a small app written in Gambas on this partition, which opens files in its own directory, so this is where the problems start. if the program is set to open a file in /SHARED, it wont open in /Shared etc. I also have a permision problem, I cant create a file in my app under Jaunty, but in Karmic I can. Is there a simple solution to this ?

My fstab line :-

/dev/sda4 /media/SHARED vfat iocharset=utf8,umask=000 0 0

---

### Post by celticbhoy on 2009-06-21
Just to add in my /media folder the partition mounts as SHARED, it just shows in Nautilus and is named on my desktop as Shared. The problem with open files still persists though.

---

### Post by swerdna on 2009-06-21
It's probably owned by root:root. Try this, which should make it root:users and thus more accessible:

/dev/sda4 /media/SHARED vfat [COLOR="Red"]users,gid=users[/COLOR],iocharset=utf8,umask=[COLOR="Red"]0000[/COLOR] 0 0

Note the differences with yours

Reference: [mount FAT32 (VFAT) partitions with read-write access]("http://opensuse.swerdna.org/susefat32.html")

---

### Post by celticbhoy on 2009-06-21
No still the same, but oddly if I comment out the automount line from fstab, and mount from the Places menu, it works fine, appart from the name still being Shared!

---

### Post by drs305 on 2009-06-21
You might be able to fix this by checking the label name or creating a new one. 

The easiest way to label a fat32 partition is via *gparted*. Recent versions can make labels for most filesystems. Check the label and change it to "SHARED" if it isn't already. Highlight the partition, then Partition > Label.

If you happen to be using labels in fstab make sure you make the appropriate change to that file if necessary.

---

### Post by celticbhoy on 2009-06-21
It was GParted I used to set the drive label and in it, it is set to SHARED. That is why I cant understand why Jaunty mounts the drive as Shared, when Karmic, & Win7 read it right.

---

### Post by celticbhoy on 2009-06-22
Bump.

I really need this drive to be mounted read & write, not just read only.

---

### Post by swerdna on 2009-06-22
Try this: unmount the drive. Then chown the folder to your username like this:```
sudo chown yourname:users /media/SHARED
```Then put this line in fstab:
```
/dev/sda4 /media/SHARED   vfat   uid=yourname,gid=users,utf8=true 0 0
```Then remount it with this:```
sudo mount -a
```

---

### Post by celticbhoy on 2009-06-22
Cheers Swerdna - its working great now, well apart from still showing as Shared not SHARED on desktop - but that means nothing.

---

### Post by swerdna on 2009-06-22
That's great news

---

### Post by swerdna on 2009-06-22
This thing about "mount as SHARED" I didn't understand what you mean. Can you desvribe in more words what you mean by "the partition mounts as SHARED"? Does that have something to do with the path or...?

---

### Post by celticbhoy on 2009-06-22
Sorry if I wasn't clear enough, what I mean is that the volume is labeled as 'SHARED' and in Karmic & win7 it shows as 'SHARED' as you would expect. However in Jaunty it shows as 'Shared' - the difference being the capitalisation!

---

### Post by swerdna on 2009-06-22
Thanks. Can't think of anything to help though.

---

### Post by celticbhoy on 2009-06-22
Thats ok you have been helpful enough. It isnt an issue as it doesn't stop anything working, its just weird is all.

---


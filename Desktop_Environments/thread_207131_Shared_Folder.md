---
title: "Shared Folder"
date: 2006-07-01
forum: Desktop Environments
---

### Post by dominicrodger on 2006-07-01
Hi,

I have a shared FAT32 windows partition, which I've mounted in fstab using:

/dev/hda5	/shared		vfat	rw,noatime,uid=500,gid=500,user	0	0

As per various guides.

I can read from it fine, but I can't write to it. I try logging in as root and editing the permissions, but immediately I check the box for write access on group, it gets unchecked.

Is there any way to allow me to write to this drive? I want to use it to share mail files other data between windows and ubuntu.

D

---

### Post by Irony on 2006-07-01
Try;

[php]/dev/hda5 /shared vfat    defaults,umask=000  0       0[/php]

However normally you would put the file in the /mnt folder like this;

[php]/dev/hda5 /mnt/shared vfat    defaults,umask=000  0       0[/php]

or the /media file like this;

[php]/dev/hda5 /media/shared vfat    defaults,umask=000  0       0[/php]

It maybe that by putting the file in /shared you won't have the permissions.

---

### Post by dominicrodger on 2006-07-01
Thanks,

I tried the second approach (using /mnt/shared) and ran mount -a, but I still can't write to it (unless root). How do I change this?

Secondly, I can't deleted the old /shared directory? Any idea why?

Many thanks,

D

---

### Post by coffeecat on 2006-07-01
I've found that vfat lines in fstab are difficult to get right. The uid and gid values are absolutely critical, except that you can often get away without the uid. This is the appropriate line that Ubuntu set up automagically in my multiboot:

```
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
``` 
It works fine, reading and writing from Ubuntu, but you'll have to change the partition and mount point of course. The gid of 46 is for the plugdev group. Check your users and groups in System > Administration - make sure you have a plugdev group with id 46. Also - do you have a group with gid=500? If you don't that's why your first line didn't work.

An alternative that worked for me in SuSE, but I haven't tried in Ubuntu, is to have 'gid=users' instead of a gid number.

If this doesn't work, post back and I'll look at my other two multiboots, and between them we should get a working line for you. :wink:

TTFN

**Edit:** Although this line is working fine, and it was set up by the Ubuntu installer, I think the last value really ought to be zero. I'll check my other multiboots later.

---

### Post by dominicrodger on 2006-07-03
Hi,

I've found the plugdev group (it was hidden). I still can't seem to write to mnt/shared/ Any more ideas?

The line is now:

```
/dev/hda5    /mnt/shared    vfat    defaults,utf8,gid=46  0       0
```

D

---

### Post by coffeecat on 2006-07-07
**dominicrodger**, my apologies. I've been distracted with other things and didn't keep in touch with this thread. Anyway, you've not got a umask=whatever entry. Perhaps this is the problem. Whether it is or not here are a selection of lines from various distros in a couple of my multiboots. They **do** work. (Again adjust partition and mount point accordingly.)

```
/dev/hda5    /windows/D    vfat    rw,users,gid=users,umask=0002,nls=utf8  0 0

/dev/sda2    /mnt/fat32    vfat    auto,users,rw,exec,uid=XXX,gid=YYY,umask=007   0  0

/dev/sda2    /media/sda2    vfat    user,users,gid=users,umask=0002,utf8=true  0  0
``` 
For the second one (for XXX and YYY) substitute the numerical values for your user and group. (Probably 1000,100 or 1000,1000) Note that all three have a umask entry, and are otherwise variations on a theme. The second version is what I usually setup manually if a distro doesn't set up its own. The others are distro automagically set up ones which I may or may not have fiddled with.

I have one other multiboot which I haven't checked out, but which I can if you are still getting problems.

---


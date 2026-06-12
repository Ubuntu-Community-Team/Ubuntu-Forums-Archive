---
title: "Installing on existing disk"
date: 2006-03-26
forum: Desktop Environments
---

### Post by lduperval on 2006-03-26
Hi,

I'm not an absolute beginner, although this feels like an absolute beginner question...

I have Gentoo and Windows XP installed on my machine. My partitions look like this:

```

/dev/hda3              8254272   7511988    322988  96% /
udev                    248888       184    248704   1% /dev
/dev/hda6              4127076   3627504    499572  88% /home
/dev/hda8             18073924  16778656    377156  98% /mnt/share
/dev/hda7              4080524   4054052     26472 100% /mnt/dosshare
/dev/hda1             12281660  10179780   2101880  83% /mnt/windows
/dev/hda2             10317860   9241404    552336  95% /mnt/spare
none                    248888         0    248888   0% /dev/shm

```

I want to install Badger but I want to keep /dev/hda1 and /dev/hda7 intact. I can delete and mix/match the rest. If push comes to shove, I can always delete /dev/hda7 (FAT-32 Read/Write partition) but I really want the Windows XP partition (/dev/hda1) to remain as is.

What can I do?

I remember trying to install Badger on another system where I had a disk with a Windows and some Linux partitions already made, and no matter how hard I tried, I couldn't manage to keep the Win(98) partition intact. In the end, I had to write Badger to the whole disk.

Any suggestions, comments, ideas for me?

Thanks,

L

---

### Post by Sef on 2006-03-27
> I really want the Windows XP partition (/dev/hda1) to remain as is.

Windows has to remain on the first partition.

---

### Post by lduperval on 2006-03-27
Which is what I have, so I should be OK, then.

L

---


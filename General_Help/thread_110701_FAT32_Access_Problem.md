---
title: "FAT32 Access Problem"
date: 2005-12-31
forum: General Help
---

### Post by jacrider on 2005-12-31
I am a relatively new Ubnuntu/linux user.

I have an older machine with 4 scsi hard drives all formatted FAT32.
sda is my linux drive
sdb is my win2k drive
sdc is my data drive (no partitions)
sdd is my win2k applications

I am trying to use sdc as a common data drive for both linux and win2k.

My fstab is set up as follows for mounting sdc:

/dev/sdc1       /media/data     vfat    rw,user,umask=000   0       0

When I boot the machine into ubuntu, I can access most of this drive in rwx access.  However there are a couple of directories that I have read-only access.  As ususal, these are the ones I need most.

Any suggestions on what to do?  I don't think I have any special permissions on these directories set up in win2k.

Thanks.

In the short time I have been using ubuntu (5.1) I have found these forums to be great ... much better than trying to get support for m$ft products!

---

### Post by Norberg on 2005-12-31
Run "sudo nautilus" then you run the filemanager whit root-acess so you will be able to write to all directories.

---

### Post by geolr on 2005-12-31
Hi!

Being no Expert, but having observed strange behaviour on my machine...
I would suggest you leave out the umask=000 option.
But I am not sure if this affects the write access...
Anyway have a backup!

In my fstab there is noted default instead of explicit options, that would be a try also.

Happy new year!
Rudy

---

### Post by jacrider on 2005-12-31
Thanks!  

I found no write access on the directories was trying to access.  Changed them with nautilus access, exited nautilus (nautilus -q) and everything is working perfectly.

---


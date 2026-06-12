---
title: "Considering Dumping Windows (mostly)"
date: 2005-05-25
forum: Desktop Environments
---

### Post by leviathon on 2005-05-25
I've been using ubuntu as my main os for the previous 5 months except for using vmware to run a couple of industry specific apps for work. I think I'm ready to dump my windows partition  \\:D/ My question is, what is the best way to go about it? I would like to split the partition into 2 10gig partitions, one for a testbed and I'd like to move my home to the other. Obviously, I don't want to blow my existing install. Advice?

---

### Post by Masato on 2005-05-25
So..you want to keep your Windows files, right?

Get either a removable drive or something to get the files with. Linux isn't really good with getting files from NTFS, assuming you have Windows 2000 or XP...I've had bad experiences trying to get my .mp3 files from NTFS using Fedora Core 3. I don't know about Ubuntu, but it didn't work at all. It kept giving me errors about the files being corrupted.  ](*,)

---

### Post by sapo on 2005-05-25
Just copy the files to another partion or make a backup on cd or dvd...

Then use cfdisk to delete the partition and create 2 new (dont delete your linux partition.. but the windows (NTFS) one  ](*,) )

Then umount the windows partition and format it as ext3 or reiserfs... i ve dumped my windows partition :D
just use: mkreiserfs /dev/hda3 (or whatever is your windows partition)

Here is my partitions

```

/dev/hda1 on / type reiserfs (rw,notail)
/dev/hda3 on /home type reiserfs (rw)
/dev/hda4 on /mnt/ntfs type reiserfs (rw)

```

hda3 and hd4 were my windows partitions.. i ve split into 2 and just formated as reiserFS  :grin:

---

### Post by leviathon on 2005-05-26
Ok, I backed up to a network share and used gparted to delete my windows partition and split it into two partitions. In gparted they are identified as /dev/hda1 and /dev/hda4 my ubuntu partition is /dev/hda5. /etc/fstab does not reflect this however

--
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro,user_xattr 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    umask=0222      0       0
```
--

How do I mount one of the free partitions as /home ?

---

### Post by leviathon on 2005-05-26
Doh! I thought I had this. I did mkreiserfs /dev/hda1 then sudo mount /hda1 /home and bam! no gnome. Anyway to recover?

---

### Post by logan2004 on 2005-05-26
what happens when you try 

```

sudo umount /home

```

---

### Post by leviathon on 2005-05-26
Ok, I'm back to where I was :) Now, how can I mount and move my home to one of the new partitions?

---

### Post by sapo on 2005-05-26
[QUOTE=leviathon]Ok, I'm back to where I was :) Now, how can I mount and move my home to one of the new partitions?[/QUOTE]


make a temp dir like...
```

/media/temp

```
Then:
```

sudo mount /dev/hda1 /media/temp

```
Then copy the files of the home folder there and move your current home folder:
```

sudo mv -rp /home/* /media/temp
sudo mv -r /home /home_backup

```

Then just mount the partition in yout new home ;)
```

sudo mount /dev/hda1 /home/

```

And edit your fstab like this:

```

/dev/hda1       /home  ext3    defaults      0       0

```

Thats it (i didnt tested it ok.. its just theorically)

But i hope it works  :roll:

---


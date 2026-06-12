---
title: "How to mount --bind at startup?"
date: 2006-01-05
forum: Desktop Environments
---

### Post by nhisyam on 2006-01-05
all i want to do is to have
mount --bind /somedir /tosomedir 
at startup (i guess in fstab)

this is my current fstab content

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 	/media/windows	ntfs	umask=0222	0	0


i tried putting something like this at last line...
/media/windows/Documents\ and\ Settings/   /home/hisyam/Desktop/temp   ext3   default,bind    0     0

it doesn't work..

also tried changing ext3   default,bind    to ntfs   umask=0222,bind

it doesn't work ...

any idea?

thanks in advance

---

### Post by nhisyam on 2006-01-05
hmm i guess i have solved my problem

System ->Preferences -> Sessions ->Startup Programs -> Add
sudo mount --bind /media/windows/Documents\ and\ Settings/hisyam/My\ Documents/tunebite/ /home/hisyam/Desktop/My\ Music/Windows/ 

My problem is solved..:razz:

---

### Post by carlosqueso on 2006-01-05
This won't do exactly what you want, you can do almost the same thing by creating a symbolic link to the directory that you're trying to work with.  All you need to do is type ```
ln -s <directory you're setting up> <new directory>
``` so in your case, it would be ```
ln -s /media/windows/Documents and\ Settings /home/hisyam/Desktop/temp 
``` or wherever you want to put it.

EDIT: oh well, I'm too slow again :-) had to figure it out myself before I did it ;)

---

### Post by Hanneman on 2006-07-17
> **nhisyam said:**
> 

i tried putting something like this at last line...
/media/windows/Documents\ and\ Settings/   /home/hisyam/Desktop/temp   ext3   default,bind    0     0

it doesn't work..



In fstab, you can substitute a space in your directory structure with \040.

In your case the entrance into fstab would be:

```

/media/windows/Documents\040and\040Settings/   /home/hisyam/Desktop/temp   none   bind    0     0
```

When binding directories it is not necessary to specify the filesystem. Took me a while to figure out, but there it is... ;)

---


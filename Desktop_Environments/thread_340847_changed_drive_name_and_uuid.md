---
title: "changed drive name and uuid"
date: 2007-01-17
forum: Desktop Environments
---

### Post by rykel on 2007-01-17
hi there,

i used to have my FAT32 drive automounted as "d" on my desktop (edgy), but a few days ago, i am not sure if i messed up something, but the name of the drive has been changed to "omizing.htm" and CANNOT even be manually changed back to "d". (see the icon in screenshot)

i checked my fstab and it says, "d".

do you know what has happened, and how i can recover the drive name as "d"?

on the other hand, if u look at my fstab, "d" was a manually added line, thus the UUID is missing... do u know how to auto-generate the uuid for any given device again?

---

### Post by mcduck on 2007-01-18
I see you are dual booting? You could have changed the partition's label in windows. Anyway, changing it back to something else would fix the problem.

'ls /dev/disk/by-uuid -alh' will list all your partitions and their UUIDs.

Take a look at this thread for more info&help: [http://www.ubuntuforums.org/showthread.php?t=283131&highlight=removable+ext3+drive+permissions]("http://www.ubuntuforums.org/showthread.php?t=283131&highlight=removable+ext3+drive+permissions")

---

### Post by rykel on 2007-01-19
Hi&#65292;

Thanks for your helpful note... at least now I know the UUID of my drive and have replaced "dev/sda6" with "UUID=xxxx-xxxx"!

But unfortunately, your recommendation did not solve the problem... it still says "omizing.htm" on my desktop, instead of "d"...

btw, I did NOT change any drive letters in Windows; in fact, I hardly use that OS nowadays. (hail Linux!)

---

### Post by mcduck on 2007-01-19
OK. It was just a guess. But anyway you could try changing the partition label, either in windows or with mtools.

---


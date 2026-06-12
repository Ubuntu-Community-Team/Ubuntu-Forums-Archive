---
title: "FAT32, NTFS and such"
date: 2005-12-31
forum: Desktop Environments
---

### Post by npodges on 2005-12-31
my current set up is this: (i know it's weird, but it's that way because of the order i've installed things on my computer)
i have a 120 gb ntfs hdd that i store most of my files on
i have a 30 gb ntfs drive with windows xp installed
and i have a 60 gb drive with ubuntu installed. 
i have a 250 gb unformatted drive sitting on my desk.

I have most of my music/documents on the 120 gb drive, which means i can access them in linux, but i can't write to the drive at all, which is annoying.

well the 120 gb drive broke. or at least windows thinks it did. it's real frustrating, and i've had things likethis happen before. windows sees it as a new, unformatted drive. in linux, after mounting it, all of my files are viewable

what i wanna do is back up everything on that drive, and hopefully keep it on a filesystem that i can use from windows or linux. 

is fat32 my only option, if so how do i go about formatting the drive as fat32 from linux?

or is there a better option here that i'm missing?

---

### Post by cwaldbieser on 2005-12-31
[QUOTE=npodges]my current set up is this: (i know it's weird, but it's that way because of the order i've installed things on my computer)
i have a 120 gb ntfs hdd that i store most of my files on
i have a 30 gb ntfs drive with windows xp installed
and i have a 60 gb drive with ubuntu installed. 
i have a 250 gb unformatted drive sitting on my desk.

I have most of my music/documents on the 120 gb drive, which means i can access them in linux, but i can't write to the drive at all, which is annoying.

well the 120 gb drive broke. or at least windows thinks it did. it's real frustrating, and i've had things likethis happen before. windows sees it as a new, unformatted drive. in linux, after mounting it, all of my files are viewable

what i wanna do is back up everything on that drive, and hopefully keep it on a filesystem that i can use from windows or linux. 

is fat32 my only option, if so how do i go about formatting the drive as fat32 from linux?

or is there a better option here that i'm missing?[/QUOTE]

fat32 is your best option.

---

### Post by pharcyde on 2005-12-31
I think fat32 is the best option.  I know it's possible to mount ext2/3 in windows with some special drivers, though I'm not sure if its writeable.  There may be some alternatives to other file systems such as Reiser but I'm not sure.

---

### Post by npodges on 2005-12-31
alright, thanks. i guess i'll just format it in windows, since i dont know how to do that from linux.

---

### Post by psusi on 2005-12-31
Windows won't let you format a drive that large as fat32, it's Microsoft's way of trying to force people to use NTFS.  Use mkdosfs to format it from linux.  You also might want to run badblocks on it to see if it has any bad sectors.

---


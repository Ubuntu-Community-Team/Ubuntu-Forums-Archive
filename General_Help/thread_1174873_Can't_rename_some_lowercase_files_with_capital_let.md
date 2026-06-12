---
title: "Can't rename some lowercase files with capital letters"
date: 2009-05-31
forum: General Help
---

### Post by blueshiftoverwatch on 2009-05-31
I'm trying to rename some audio files but have run into a problem. For example: if a file is called "01 - Name of **s**ong.mp3" and I attempt to rename it "01 - Name of **S**ong.mp3", changing only the capitalization of the word "song" I'll get an error message telling me that I can't use that file name because it's already in use in that same folder. When it clearly isn't.

Just to make sure that there were no hidden capitalized duplicates messing me up I enabled the showing of hidden files. Which there weren't any.

I think this has something to do with the fact that the files that I'm trying to rename are located on an external hard drive running the FAT32 file system. Because when I copy the same files onto Ubuntu (running ext3) I can rename them with no problems. So it's probably either an inherent problem with the FAT32 filesystem or with Linux's ability to interface with it. If I had to guess I'd say the latter.

Short of copying all of my files onto my desktop, renaming them there, and than having to copy them all back onto the external hard drive what can I do?

---

### Post by Legace on 2009-05-31
I think it's something got do with FAT32.
Why don't you create a NTFS or EXT2 partition?

---

### Post by blueshiftoverwatch on 2009-05-31
> **Legace said:**
> I think it's something got do with FAT32.
Why don't you create a NTFS or EXT2 partition?
I mainly use Linux and Mac OSX during the course of my everyday activities. NTFS is superior to FAT32 but Mac OSX can't natively write to it, only read.

FAT32 is pretty much the universal filesystem for compatibility between operating systems.

---

### Post by pastalavista on 2009-05-31
Try renaming the files without any spaces in the name. Replace the spaces with underscore_or hyphen-... see if that will work. Linux doesn't like spaces in file names.

---

### Post by arubislander on 2009-05-31
> **blueshiftoverwatch said:**
> ... So it's probably either an inherent problem with the FAT32 filesystem or with Linux's ability to interface with it. If I had to guess I'd say the latter.

I'd guess it's a bit of both. The FAT32 filesystem is case insensitive, so Foobar.mp3 is the same as FooBar.mp3 or any other combination of uppercase and lowercase in the word foobar.

So technically the error message is correct. The name you are using to rename the file does exist if it is evaluated without regard to case.

---

### Post by CatKiller on 2009-05-31
> **pastalavista said:**
> Try renaming the files without any spaces in the name. Replace the spaces with underscore_or hyphen-... see if that will work. Linux doesn't like spaces in file names.

Linux has no problems with spaces in names. The only character you can't use in a filename is /. I think you're confusing it with something else.

To the OP: I don't have any FAT partitions to test on at the moment, but does adding 
```
iocharset=utf8
``` to the mount options for that partition in your fstab help? I don't recall if it should or not, but it might be worth a try.

---

### Post by blueshiftoverwatch on 2009-06-03
I think that trying to manually edit my audio files one at a time would be very inefficient. Not only do the song names need edited but the MP3 metadata as well.

A friend was telling me that in WinAmp it'll let him edit the file names and all of the MP3 metadata (band, album, genre, etc) for entire groupings of songs. So if you wanted to change the band name metadata from "AC-DC" to AC/DC" you could do it for all of their songs at one time. Is there a GUI based program that I can do this with in Linux?
> **pastalavista said:**
> Try renaming the files without any spaces in the name. Replace the spaces with underscore_or hyphen-... see if that will work. Linux doesn't like spaces in file names.
I don't like the look of file names with underscores instead of spaces. Putting spaces in file names isn't a problem if you don't mind putting quotation marks around the file you want to select while in the command line. Other wise it might interpret the spaces in the file name as being seperaters for the commands it thinks your trying to enter.
> **CatKiller said:**
> To the OP: I don't have any FAT partitions to test on at the moment, but does adding 
```
iocharset=utf8
``` to the mount options for that partition in your fstab help? I don't recall if it should or not, but it might be worth a try.
I put the that line into the mount options section of the volume tab that is selectable when you right click properties on a mounted device. When I remounted the external hard drive I wasn't allowed to cut, rename, or trash any of the files or folders in the drive. So I removed it, remounted the drive, and now things are back to the way they were before.

---

### Post by CatKiller on 2009-06-03
> **blueshiftoverwatch said:**
> I put the that line into the mount options section of the volume tab that is selectable when you right click properties on a mounted device. When I remounted the external hard drive I wasn't allowed to cut, rename, or trash any of the files or folders in the drive. So I removed it, remounted the drive, and now things are back to the way they were before.

I haven't used removable drives, so I haven't seen the dialogue that you're referring to. But obviously by "adding iocharset=utf8" I meant in addition to the umask=000 or whatever other options you are using.

---

### Post by obiwankamote on 2009-09-17
In my case, I had to modify the fstab (/etc/fstab) and set the shortname to mixed.

See here for more lengthy discussions:

[https://bugs.launchpad.net/ubuntu/+bug/202394](https://bugs.launchpad.net/ubuntu/+bug/202394)
[http://ubuntuforums.org/showthread.php?t=500849](http://ubuntuforums.org/showthread.php?t=500849)

Hope it helps :)

---


---
title: "Sound Juicer files won't Squeezebox"
date: 2006-03-09
forum: Desktop Environments
---

### Post by Mike-97470 on 2006-03-09
The following post didn't get replies, maybe mine will--
[http://www.ubuntuforums.org/showthread.php?t=72785&highlight=slimserver](http://www.ubuntuforums.org/showthread.php?t=72785&highlight=slimserver)

My first problem:  Sound Juicer 2.12.2 generates files that have access mode 640.  My Squeezebox (remote wi-fi audio/text receiver/player when hooked to stereo) and Softsqueeze (PC resident music player) can access the Artist (755) and Album (755) info correctly but can't ("Problem: Can't Open File") play the music unless the file has "Others" Read access permission.  Actually, it must be the Slimserver (the PC resident music server) that needs "Others" Read access.  Note that slimserver is a user in my account's user group.  So what do I do?  Give Slimserver more privileges?  Or get Sound Juicer to generate files with --4? (I've already ripped about 130 CD's so that's not good.)  Or set the "Others" Read bit?  In about 1600 files?  Well, how do I do it with chmod -R o+r music_file.flac    ???
when a typical music file name looks like this--

05 - You are the "Sunshine" of my : eyes (oh, ya, ya).flac

Is there a utility that will do it?

My second problem:  is that I've pushed my flac music over to an external disk.  How do I change it's access mode?  The Properties/Permissions of it's icon on my desktop are 700, they're 444 (grayed out) for it's icon in //computer, and 700 in /media.  When I try to change the 700 to 704, I guess it's the USB PNP monitor that quickly changes it back to 700.  This disk is automounted, at least I didn't do it.  Is there some to mount it and make it permissive?

---

### Post by jpkotta on 2006-03-10
The first problem:
find will do it.  The Swiss Army knife of batch file manipulation.  This will give all of your .flac files in ~/music o=r permissions:
```
find ~/music -name '*.flac' -exec chmod o=r '{}' \;
```
You can put this in a file and execute each time you rip a CD.  Sound Juicer might have a setting for this, but I doubt it.  Try playing with umask, i.e. run Sound Juicer from a wrapper script that sets the umask appropriately.

The second problem:
There is probably a better way, but you could edit /etc/fstab.  I say there is probably a better way because I'm not sure if the automounting that Ubuntu does is controlled by it.  Anyway, the options you're interested in are user, dmask, and fmask.  They're explained in the mount manpage.

---

### Post by Mike-97470 on 2006-03-10
Thanks, the find command-
find ~/music -name '*.flac' -exec chmod o=r '{}' \;
worked great! 

The usb disk mount problem is tricker, and I'm going to defer it.  I'd forgotten that when I tried to put the music files on the usb disk, since it was fat32 and couldn't deal with the weird files names, I decided to clear out an 80g partition on an internal drive and reformat as ext2.  That's where I stuck the music files.

---


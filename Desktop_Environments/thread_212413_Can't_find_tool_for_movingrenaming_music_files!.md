---
title: "Can't find tool for moving/renaming music files!"
date: 2006-07-09
forum: Desktop Environments
---

### Post by cleentrax on 2006-07-09
I am migrating gradually from Windows to Ubuntu, and the next step is my music library. It's about 25,000 files in a mix of mp3, flac and ogg.

I want to rename the files (based on their tags) to Linux- and Network- friendly names, which means removing punctuation, spaces, etc., and I want to change the file structure as well.

In Windows there are several tools that can do this -- from Foobar2000 to iTunes, etc. But I can't find a Linux equivalent. Everything from Cowbell to Amarok will edit tags, but not automatically rename and sort the whole library. 

Know of a tool that does this, or am I doomed to rename and move 25,000 files?

---

### Post by aysiu on 2006-07-09
EasyTag and TagTool are your friends.

I used EasyTag to rename my 8000 MP3s based on their tags.

You may also want to look at KRename.

---

### Post by cleentrax on 2006-07-10
Thanks for the suggestions. Of the three I prefer Easy Tag. But there are a couple of things that it doesn't seem to do:

1. Change the directory structure (i.e. move albums by a particular artist to  the same folder)
2. Change the case (i.e. upper/lower/first-only) of file names
3. Rename multiple directories

---

### Post by aysiu on 2006-07-10
I haven't used these, but you may also want to look into:

*exfalso*
*glurp*
*id3ren*
*mp3info-gtk*

---

### Post by cleentrax on 2006-07-10
Well, I tried EasyTag, and it was a near-disaster. I did one album as a test, which came out OK, so I tried the bulk of the rest of them. It crashed -- corrupting every music folder on the drive!

Luckily, my music was on an external drive, which I unplugged without ejecting, which ignored the changes/corruptions. 

Needless to say, I won't be using EasyTag any more.

I know I should have a backup, and I do have a backup of some of the music. But a lot of the names are non-standard, and backup won't work -- which is why I need to use a program like EasyTag!

---

### Post by aysiu on 2006-07-10
A backup won't work? Have you tried *rsync*?

For example, if your files are in /music and you want to copy them to /media/usbdisk, you would do ```
rsync -av /music /media/usbdisk
``` and it'll create a folder called /media/usbdisk/music that has all your music. *rsync* also does differential backups, so the next time you run that same command, it'll copy only files that have been changed or added since the last time you ran it.

It's a bit different from regular copying, as it tends to be cool with different file names and with symlinks and hard links.

EasyTag worked for me, but I can see how it might be confusing or might overload your system. I had only 8,000 songs. You have 25,000 songs--that's more than three times as many.

TagTool...?

---

### Post by cleentrax on 2006-07-10
I've used rsync with my ubuntu data, but not with this external drive, which is FAT32. Will rsync work ok with non-standard file names on a FAT32 drive? I'm a little nervous to try.

---

### Post by aysiu on 2006-07-10
No. *rsync* will not work with FAT32. Maybe that's the issue--FAT32. Character encoding is a bit weird with FAT32...

---

### Post by cleentrax on 2006-07-10
Yeah, tell me about it! But I use this drive with Linux, Windows and OSX, so FAT32 seemed my best choice at the time. As of tomorrow, I'll have it all on a RAID-5 in my home server (ubuntu, of course...) I just wanted to get the data cleaned up before I tried to transfer it. Thanks for the help, Aysiu.

---

### Post by kditty on 2006-07-18
easytag seems to work well with the %a - %b/%a - title sorting, the only thing you have to be careful of is making sure that all of your music files are properly tagged or it will be a disaster! its also a little slow, any apps out there that do this with a little more speed? i tried audio tag tool but it didnt seem to read id3 v1 tags. 

its taken nearly an hour and a half to rename/move 2000 mp3s with easy tag, and thats with an intel celron 3GHz processor and 750+ mb of ram. im not sure if its taking so long just because of the fact that it has to make the directories or what but this thing is SLOW!

---

### Post by elewton on 2008-07-15
Unfortunately, that changes the file name to the title.  It loses additional information that may be in the filename (original air date, etc.)

You can do it by setting the comment tag to the full file name in the first pass and then using that as the filename in the renaming pass.

Little messy though.  Probably a smarter way to do it.

Since there is a command that returns the ID3 tags, I'm sure you can do a

foreach in *.mp3
mv file PATH/"id3AUTHOR - id3ALBUM/file"

or whatever expression you want.  You'd have to know what you are doing with scripting.  I don't.

Could probably make one that extracts the Author and Album from the folder or filename and tags it appropriately.

On the off-chance that I figure this out, I'll post it.

---


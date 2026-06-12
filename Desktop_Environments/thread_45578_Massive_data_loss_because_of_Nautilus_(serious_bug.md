---
title: "Massive data loss because of Nautilus (serious bug)!"
date: 2005-06-30
forum: Desktop Environments
---

### Post by GameGod on 2005-06-30
Hey everyone,

I just did a seemingly harmless operation on a set of files and lost them all with Nautilus. Big problem.

Here's what happened. I have my MP3s stored in /mnt/music, and I cracked open that folder in Nautlius because I wanted to change the permissions on them. I copied them off a CD about a month ago, and finally wanted to change their permissions from read only to read-write.
So, I highlighted all my MP3s in that directory as well as selected all the sub-folders (I keep whole albums in sub folders within that directory.) I went to properties, and changed the permissions for the group, myself, and others to allow writing.

Bam, Amarok immediately starts saying "local file not found". I look back at that folder, and my music seems fine - but wait, I check the sub directories, and I'm left with all my music in those folders turned into zero byte files.
Here's another interesting thing. My subfolders within subfolders were also turned into zero byte files. My directory "/mnt/music/Bonobo/Dial M for Monkey/ turned into a file with zero size!

What the heck just happened? I'm REALLY fortunate that all I lost was about 30 albums that can be copied back over from my (recent) backup, and the most recent ones re-ripped.

How should I go about reporting this to the Nautilus/GNOME developers? This is pretty big - if I can lose data by changing permissions, I'm not sure I trust Nautilus with my files *at all* any more...

If anyone could help me out here, maybe tell me what happened or offer any advice, it would be greatly appreciated! Thanks guys, Ubuntu's rocked until now (and technically it's not Ubuntu's fault :P)

Albert

---

### Post by lynng on 2005-06-30
Something similar happened to me.  I changed permissions on a bunch of files to read/write recursively and found that all the subdirectories had become 0 bytes, and were now files instead of directories.  Directories need the execute permission to read their contents, and when I took it away they showed up in Nautilus as 0 byte **files** *<edit>They looked like files in Nautilus, but were listed as directories in CLI</edit>*.  I found that Nautilus would not allow me to give back the execute permission to the directories/subdirectories, so I did it by CLI, but as soon as I did I could see all the files within - they had not been deleted as I had first thought.  (A mistake due to both inexperience with the Unix/Linux file system, and just plain not paying attention to what I was doing.)

So, check to see if the subdirectory still has execute.  If it doesn't, add it and you should then be able to see your mp3s inside.

Note: You can recursively add the execute permission to all files/subdirectories in a directory, but then the mp3 files themselves will also have execute, which they don't need.  I preferred to give it only to the directories, which takes a bit longer.

---

### Post by royg1234 on 2005-07-30
I *think* the same thing happened to me, but I don't know.  I don't remember messing around with permissions, but amaroK was involved (with mySQL as an accessory).   My music folder is completely gone, but apparently still taking up space.
  
Here's my thread --> [http://ubuntuforums.org/showthread.php?t=53263&highlight=lost+music](http://ubuntuforums.org/showthread.php?t=53263&highlight=lost+music)

---


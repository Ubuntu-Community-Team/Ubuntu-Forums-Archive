---
title: "filesystem for my media library?"
date: 2006-05-12
forum: Desktop Environments
---

### Post by groggyboy on 2006-05-12
So I was googling around on filesystems, and I was wondering something.

Currently, my linux fs is ext3.  All my mp3/avi files are on a seperate FAT32 partition, so that they can be easily accessed from either windows or ubuntu.  But if the windows-compatibility restriction was removed, what would be the best filesystem for a media library - say, 20+ gigs (and growing) of smallish files?  would reiserfs work for this?  i hear that it's good for situations where there is a high number of small files.  i also gather that xfs is a good filesystem for a high number of large (multimedia) files.  or would ext3 be sufficient (altho that is kinda boring)?  Keep in mind that this is on a personal laptop, not an industrial server!

what are people's opinions on this?

cheers,
groggyboy

p.s.: a couple of websites:
[Wikipedia's Comparison of filesystems]("http://en.wikipedia.org/wiki/Comparison_of_filesystems")
[CoolSolutionWiki's File System Primer]("http://wiki.novell.com/index.php/File_System_Primer")

---

### Post by bpont on 2006-05-12
[QUOTE=groggyboy]So I was googling around on filesystems, and I was wondering something.

Currently, my linux fs is ext3.  All my mp3/avi files are on a seperate FAT32 partition, so that they can be easily accessed from either windows or ubuntu.  But if the windows-compatibility restriction was removed, what would be the best filesystem for a media library - say, 20+ gigs (and growing) of smallish files?  would reiserfs work for this?  i hear that it's good for situations where there is a high number of small files.  i also gather that xfs is a good filesystem for a high number of large (multimedia) files.  or would ext3 be sufficient (altho that is kinda boring)?  Keep in mind that this is on a personal laptop, not an industrial server!

what are people's opinions on this?

cheers,
groggyboy

p.s.: a couple of websites:
[Wikipedia's Comparison of filesystems]("http://en.wikipedia.org/wiki/Comparison_of_filesystems")
[CoolSolutionWiki's File System Primer]("http://wiki.novell.com/index.php/File_System_Primer")[/QUOTE]

"Small" is relative.  My understanding is that Reiserfs is an optimal filesystem for *very* small files, that normally don't fill entire blocks and therefore, create lots of 'tails' (unused, but inaccessible space on your hd).  I think Reiserfs is used often in database environments, though I'm not sure what other environments are best suited for Reiserfs.  The other advantage is of course journaling, which prevents file system and data corruption, but ext3 has that too.  Assuming you have a speedy hard drive, plenty of memory and a decent processor *and* want to keep your stash accessible under linux and windoze, I'd say leave it well enough alone.  However, you seem itchy to experiment, so I'm sure you won't take my advice...so good luck.  ;)

---

### Post by groggyboy on 2006-05-13
word. experiment.  mwa ha ha ha ha ha!

:twisted:

---


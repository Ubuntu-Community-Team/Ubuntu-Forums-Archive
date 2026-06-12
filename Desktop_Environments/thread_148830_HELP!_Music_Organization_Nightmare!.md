---
title: "HELP! Music Organization Nightmare!"
date: 2006-03-22
forum: Desktop Environments
---

### Post by mjwood0 on 2006-03-22
Well, now that I have the new computer up and running, I decided it was time to get organized once and for all!  I had about 50 unlabeled CDs running around my desk area from random backups of music / photos and files.  A real nightmare that's been in the making for close to 5 years since I left college and have been too busy to fix.

So I went through and got all my music off these disks.  Something like 5000 files and I have a whole music collection left to rip.  But before I start, I want to come up with a standard filename structure and naming convention (not to mention Tagging system) for all these files.

What filename structure do you all use and like -- and what's the easiest way to re-name all these files to fit that structure.  I understand this will be a major undertaking, but I might as well get going!

Once the names are correct, how in the world do you use EasyTag?  I opened it last night and all I could do was edit one file at a time and this seemed a little silly.  Also, it highlighted all my filenames in red.  What does this mean?

Thanks for any ideas!

---

### Post by indytim on 2006-03-22
I'll share my experience as a possible approach.  First my music collection is about 400 CDs ripped to high quality mp3.  I set up a dedicated partition for my media files.  The basic organization is a primary folder for the mp3 library.  This is subdivided into genre (ie. Rock-Classic; Soundtrack-Jungle etc).  Within each folder I have a folder for each CD converted to mp3.  In the case of my classic rock entries, I have a master folder by artist then a dedicated folder within that for each CD.  Ie. Pink Floyd -> Meddle ->Dark Side of The Moon.

I keep track of all of this stuffola in a MySQL database with outputs in pdf.  I also cross index the re-mastered CDAs and the DVD I've got specific CDs  burned to.  

I admit it's a bit much, but I've got a lot of time and effort invested in the library and I want to insure that I know what I've got and where it is.

Good luck with whatever approach you use to organizing your music library.

IndyTim

---

### Post by matthew on 2006-03-22
[quote=mjwood0]What filename structure do you all use and like[/quote]I have mine organized in sub-directories like this in my /home directory. The -'s represent sub-levels.

/music
--/group or artist name
----/album one
------/song one
------/song two
----/album two

and so on

---

### Post by rossjman1 on 2006-03-22
Artist - Track.mp3
all in one folder. I only have about 500 songs, so I guess it's a little different.

---

### Post by Shampyon on 2006-03-22
[QUOTE=matthew]I have mine organized in sub-directories like this in my /home directory. The -'s represent sub-levels.

/music
--/group or artist name
----/album one
------/song one
------/song two
----/album two

and so on[/QUOTE]


This was one thing I've always liked about iTunes. It automatically arranges all your music into the same kind of structure, even going so far as to access the gracenote site for extra information (if you let it) to help keep things neat and tidy. I wonder if there's a Linux equivalent... It'd sure make things a heckuvalot easier.

---

### Post by mjwood0 on 2006-03-22
Hmm... so many options, so many songs!

I currently have my music on a seperate drive which houses all my shared data (data my wife and I can both read and write).  It's mounted in /home/data with subdirectories for Music, Photos, etc...

Inside of this, I really would like to seperate things into subdirectories.  Probably, the best approach would be to use matthew's approach above:

/home/data/music
.../artist1
...../album1
......../song1
......../song2
...../album2
.../artist2

Now... how in the world do I get all the music renamed and into those folders!  Time to investigate some program options.

Anyone ever used the following and what did you think:
  tagtool
  renameutils
  mrename
  mp3rename
  id3ren
  krename

Thanks for all the help.  Some of these tasks aren't as straightforward as they would seem.  I guess I could always just do each file one by one, but there must be a easier way (which allows me to learn something at the same time :cool: )

---

### Post by aysiu on 2006-03-22
[QUOTE=mjwood0]
Anyone ever used the following and what did you think:
  tagtool
  renameutils
  mrename
  mp3rename
  id3ren
  krename[/QUOTE] Tagtool has a straightforward and intuitive interface. It's a bit limited in terms of certain tasks, though. For what TagTool can't cover, I recommend EasyTag.

I used EasyTag to rename my 8000+ song music collection, and it was a real timesaver!

---

### Post by goober99 on 2006-03-22
> This was one thing I've always liked about iTunes. It automatically arranges all your music into the same kind of structure, even going so far as to access the gracenote site for extra information (if you let it) to help keep things neat and tidy. I wonder if there's a Linux equivalent... It'd sure make things a heckuvalot easier.

Linux does have an equivalent: Sound Juicer--which I believe comes standard with Ubuntu, but if not, it is only a few clicks away in Synaptic Package Manager--retrieves information about songs and saves them into a directory structure specified by you covering the ripping side of iTunes.

If you want an iTunes look-a-like for playing music, I use Rhythmbox, which also comes with Ubuntu. Rhythmbox is all I use to play music. In my opinion, it is far superior to iTunes. I used iTunes on Windows just so I could sync my iPod. I hated it. It was slow, bulky, and ugly. I never just used it to listen to music.

---

### Post by mjwood0 on 2006-03-22
Thanks!

I just took a look at Tagtool while you must have been writing your post.  Easy to use, but you are right. Somewhat limited.  I'm still trying to understand how to use EasyTag.

---

### Post by celloandy on 2006-03-23
My favorite, I think, for tagging and renaming, is Ex Falso, which gets installed if you install Quod Libet.  It can rename and reorganize huge piles of files based on their tags really easily, and it's pretty easy to customize it.

Andrew

---

### Post by hugmenot on 2006-03-23
I second the suggestion of Quod Libet for tagging and renaming.
Say you have blank files -no tags- but the correct track-number and -order of the original CD. Just select all of them and use CDDB, it will retrieve all tags from FreeDB with high likelihood. If that fails, try the other database plugin for Musicbrainz.
If you have things to clean up afterwards you just group-select all files in question and edit the tags en bloc. QL is really flexible and clean in that regard, it supports free form tagging and renaming, which includes moving files around (example string: /home/mj/music/<artist>/<album> <date>/<tracknumber>. <title>). The batch can get really giant - no problem.
That's it, try it out...
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=7514&d=1143140736[/IMG]

---

### Post by pbaehr on 2006-03-23
I'm currently (literally right now) in the middle of organizing all my music. I'm using easytag. I'm very happy with the way it works, though, I must admit it's the only one I've tried.

It does a nice job of batch renaming files provided you have the correct tags on the files.

---

### Post by Spie on 2006-03-23
Easytag is a very powerful tool. I agree, it is not easy when used for the first time but very useful when tagging lots of files.
Another program worth mentioning is Cowbell. It has a clear interface (HIG) and is very easy.

---

### Post by arctic on 2006-03-23
Programs like Banshee have an inbuilt tageditor that is quite useful and can rename hundreds of files in a hurry.

---

### Post by hugmenot on 2006-03-24
[QUOTE=arctic]Programs like Banshee have an inbuilt tageditor that is quite useful and can rename hundreds of files in a hurry.[/QUOTE]

Huh, how does Banshee rename files? I think B is completely useless for tagging with a minimum of sophistication with its mere four tag fields.

---

### Post by aysiu on 2006-03-24
[QUOTE=hugmenot]Huh, how does Banshee rename files? I think B is completely useless for tagging with a minimum of sophistication with its mere four tag fields.[/QUOTE] Not to mention that, as far as I know, Banshee can't bulk rename files based on their tags.

---


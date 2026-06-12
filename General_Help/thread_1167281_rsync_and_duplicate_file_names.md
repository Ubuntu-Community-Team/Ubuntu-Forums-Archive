---
title: "rsync and duplicate file names"
date: 2009-05-22
forum: General Help
---

### Post by maclenin on 2009-05-22
I have a quick question re: rsync and the way it handles files that share the same name (this doesn't seem to be an issue with regard to directories sharing the same name)....

**Example 1: TEST**

/data contains test_001.txt (an empty text file)

/backup contains test_001.txt (with saved text "abc")

After running...

```
rsync -avr /data /backup
```

/data contains test_001.txt (an empty text file)

/backup contains test_001.txt (an empty text file)

Where did /backup/test_001.txt (with saved text "abc") go? I assume it was over-written?

**Example 2: LIVE**

/images contains file DSC_0001.png (photo taken today)

/backup already contains file DSC_0001.png (photo taken yesterday)

I am concerned that if I run rsync in this LIVE example that /images/DSC_0001.png will overwrite /backup/DSC_0001.png....

Are there any rsync "how to treat dupes" parameters?

Do I need to manage my files differently?

Thanks for any thoughts!

---

### Post by XCan on 2009-05-23
Basically, you want to use rsync to never overwrite files? I would say this is possible with 
rsync -bavr /data /backup /data /backup

The -b (backup) flag should rename the existing files. But try it out first before doing a live run. :)

---

### Post by maclenin on 2009-05-23
**XCan!**

Thanks for the "-b" suggestion!

I gave it a whirl - but the "abc" file still vanishes!

With reference to my example, are you suggesting I try...
```
rsync **-b**avr /data /backup
```
...which should yield...

test_001.txt (empty)

and

test_001.txt_backup ("abc")

...in my /backup directory?

My general concern is that if there are files that already exist in /backup (e.g. files with the same name - as my camera resets to DSC_0001 every time I clean images from the image card) I might "accidentally" cause old images to be removed as I sync /backup with recently-taken photos I have stored in /data (which will also have files named DSC_0001, and so on)....

So, essentially, rsync interprets the "from" file as the latest - and will replace the identically named file it finds in /backup with the "from" version in /data (even though, in my **Example 1** - the "abc" file was created in /backup later than the /data file was created)?

I could NOT get the -b option to work in the way I think you were suggesting it should work!

Thanks, again, for the suggestion!

---

### Post by albinootje on 2009-05-23
> **maclenin said:**
> 
I am concerned that if I run rsync in this LIVE example that /images/DSC_0001.png will overwrite /backup/DSC_0001.png....


Do you want incremental backups ? 
I like using rdiff-backup for that.
There are also scripts for rsync to make incremental backups.

[http://www.gnu.org/savannah-checkouts/non-gnu/rdiff-backup/](http://www.gnu.org/savannah-checkouts/non-gnu/rdiff-backup/)
[http://packages.ubuntu.com/rdiff-backup](http://packages.ubuntu.com/rdiff-backup)

[http://www.sanitarium.net/golug/rsync_backups.html](http://www.sanitarium.net/golug/rsync_backups.html)
[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

---

### Post by maclenin on 2009-05-23
Thanks **albinootje**...I am still trying to figure out just exactly how I'll be using rsync. It seems a very powerful tool, which I want to be certain I don't misuse!

This example describes my current understanding of the way rsync works - at a very fundamental level.

1. If, given a set of files...
```
/data
```
...and an empty folder made to back them up...
```
/backup
``` 
...rsync, at "first use"...
```
rsync -avr /data/ /backup
```
...will create a mirror of /data/ in the empty /backup folder.

2. With each "subsequent use"...
```
rsync -avr /data/ /backup
```
...rsync will compare the contents of /data and /backup and "update" the contents of /backup so it once again "mirrors" /data - both by adding new files (or folders) created in /data and/or by overwriting files already present in /backup but modified in /data since the "first" or "last" use of rsync.

I think my intention, over the long run, is to use rsync in the manner I've described. However, my concern remains re: a possible overwriting of identically-named files which were not modified or updated in /data - but are, actually, completely new files which happen to share the name of files already existing in /backup (e.g. /data/DSC_0001 - created 05.21.2009 and /backup/DSC_0001 - created 05.19.2009).

Essentially, I am starting to consolidate myriad sources of files and data - off cds and usb drives and older hard drives - streamlining collections of photos, music, documents - and as I bring together these disparate collections of older and newer versions of sometimes otherwise identical sets of files and start pooling them - on larger hard drives / backup media - it becomes critical to identify which files will be "source" sets and which will be "destination" sets (with regard to rsync use) - and to make certain that the "source" files represent the most up-to-date versions of files...because if I "source" older files into a collection of newer "destination" files - the newer files will be overwritten by their older counterparts (as Example 1 in my OP seems to demonstrate). This issue affects not only DSC_0001 type files (i.e. digital photos that are renamed every time the memory card is cleared) but other "regular" files as well.... For example, a document - essay_001.txt - is edited on 03.12.2009 and then again on 04.12.2009 and the two versions are saved on different usb sticks. I want to preserve the "04" version, however, I'll need to make certain the "04" is part of a "source" group - or it will be overwritten by the "03" version.

Of course, I could examine every file - manually - to compare dates - however, this seems a bit archaic.... Does rsync not have an option - as "simple" copy and paste does - to warn you that you're attempting to overwrite a file that already exists - showing you the age of the two files in question - and giving you the option to overwrite the "destination" with the "source" or to cancel the operation? 

Thanks, again, for any thoughts or clarification!

---

### Post by albinootje on 2009-05-23
> **maclenin said:**
>  Does rsync not have an option - as "simple" copy and paste does - to warn you that you're attempting to overwrite a file that already exists -


Maybe you're asking to much from rsync. 
Read the rsync documentation whether such an option exists, I think there isn't.

Also Grsync might be interesting to try as a GUI for rsync.

And please test the suggestion by XCan.

---

### Post by maclenin on 2009-05-24
Thanks, again, **albinootje**....

As for my archiving goals it seems I might need to do some "manual" sorting at some point in the process....

It is, essentially, true that when using rsync, "source" files will overwrite "destination" files, should a difference be detected between two files.... However, it's the "source" file that will always win the battle - even if the "destination" file was modified LATER than the "source".... It's about a change found via checksum - IF a change is found the "source" will overwrite the "destination" - rsync presumes the "source" contains the latest version of the two files? Am I understanding this correctly?

I went back and tried XCan's original suggestion (using the test_001 file setup from my Example 1)...
```
rsync -bavr /data /backup /data /backup
```
...and received the following...

...in /data
test_001 (empty file)

...in /backup
test_001 (empty file)
/backup/test_001 ("abc")
/backup/backup

XCan's suggestion does, indeed, preserve/backup the "duplicate" test_001 ("abc") file - though I need to figure out how "-b" works, exactly (thanks, **XCan**)....

Perhaps I can use this method to sort out duplicate files - purge the old and then generate a clean set that I can then use to properly "rsync" for backup purposes....

Thanks, again, for your continued guidance!

---

### Post by XCan on 2009-05-24
> **maclenin said:**
> Thanks, again, **albinootje**....

As for my archiving goals it seems I might need to do some "manual" sorting at some point in the process....

It is, essentially, true that when using rsync, "source" files will overwrite "destination" files?

I went back and tried XCan's original suggestion (using the test_001 file setup from my Example 1)...
```
rsync -bavr /data /backup /data /backup
```
...and received the following...

...in /data
test_001 (empty file)

...in /backup
test_001 (empty file)
/backup/test_001 ("abc")
/backup/backup

XCan's suggestion does, indeed, preserve/backup the "duplicate" test_001 ("abc") file - though I need to figure out how "-b" works, exactly (thanks, **XCan**)....

Perhaps I can use this method to sort out duplicate files - purge the old and then generate a clean set that I can then use to properly "rsync" for backup purposes....

Thanks, again, for your continued guidance!

I believe that by default rsync will append ~ to preexisting files. I just tested it out locally using
```
rsync -bavr ~/Desktop/temp/ ~/Desktop/test
```
a couple of times. First run gave the file test.txt in ./test. Second time, the backed up file got renamed to test.txt~. Third time, I got a new file called test.txt~~ and so it went on, adding a tilde for every time I ran the command. 

Are you showing hidden files in your window manager? Also, it's possible to specify what you want to append at the end of existing files, as well as if you want a specific backup dir. The following is cut straight from rsync's man page:
> -b, --backup
    With this option, preexisting destination files are renamed as each file is transferred or deleted. You can control where the backup file goes and what (if any) suffix gets appended using the --backup-dir and --suffix options.

    Note that if you don't specify --backup-dir, (1) the --omit-dir-times option will be implied, and (2) if --delete is also in effect (without --delete-excluded), rsync will add a "protect" filter-rule for the backup suffix to the end of all your existing excludes (e.g. -f "P *~"). This will prevent previously backed-up files from being deleted. Note that if you are supplying your own filter rules, you may need to manually insert your own exclude/protect rule somewhere higher up in the list so that it has a high enough priority to be effective (e.g., if your rules specify a trailing inclusion/exclusion of '*', the auto-added rule would never be reached).

--backup-dir=DIR
    In combination with the --backup option, this tells rsync to store all backups in the specified directory on the receiving side. This can be used for incremental backups. You can additionally specify a backup suffix using the --suffix option (otherwise the files backed up in the specified directory will keep their original filenames). 

Hope it cleared some stuff up. :)

---

### Post by maclenin on 2009-05-24
Indeed, **XCan** - thanks a bunch!

Hidden files was the ticket, with regard to finding "~"!

However, I was not able to reproduce the "~~" or "~~~" behavior you describe...can you be a little more specific about your testing conditions?

As for the rest of it, I am still learning and tweaking to align the best rsync "options" with my situation....

Thanks for checking back - you've been enormously helpful!

---

### Post by XCan on 2009-05-24
Sure, this is what I did. On my desktop I created two folders ./temp and ./test. Inside ./temp I created a text file 'test.txt'. I then proceeded and ran
```
rsync -bavr ~/Desktop/temp/ ~/Desktop/test
```
once, which gave me test.txt inside ~/Desktop/test. Following that, I opened ~/Desktop/temp/test.txt and modified the file (just added a few blank spaces), and ran 
```
rsync -bavr ~/Desktop/temp/ ~/Desktop/test
```
again. This gave me the modified test.txt in ~/Desktop/test and the old test.txt got renamed to test.txt~. If I modified the source test.txt again, and ran rsync, I would get an additional file called test.txt~~. When you performed the test, did you modify the file at the source location between each rsync run?

I was looking again at your previous post, which I couldn't fully understand your output from running rsync -bavr /data /backup. But I suspect it may have something to do with trailing slashes. If I recall correctly, "rsync -bavr /data /backup" would put the dir itself /data into /backup/data/<rest_of_file_here>. But perhaps what you are looking for is more "rsync -bavr /data/ /backup/" which will put only the contents inside /data/ into /backup/ and not the /data/ dir itself. (This is getting very jumbled even for me, but I hope you can make some sense of it) :p 

Don't give up on rsync yet, it's an excellent tool. I use it to backup my workstation at work through SSH to my home computer as well as my personal files to a encrypted USB thumbdrive all the time. :)

---

### Post by maclenin on 2009-05-24
**XCan** - thanks for the detail - still **NO GO** with my "tilde test"....

I **CAN** get ~ ... **HOWEVER** ~~ and ~~~ are just **NOT** happening (in the same way) for me.

There is a little "twist" in the results I get....

I'll try to be as concise as possible re: the way I am running my test - which seems to be exactly the way you are....

My directories are:
```
/data (source)
/backup (destination)
```
My files are:
```
/data/test_001 (*containing the text:* source_000)
/backup/test_001 (*containing the text:* destination_000)
```
After the **1st run** of rsync -bavr /data /backup, the yield is:
```
/data/test_001 (source_000)
/backup/test_001 (source_000)
/backup/test_001~ (destination_000)
```
Then I modify the /data/test_001 (source) file only - changing "source_000" to "source_001", leaving me with:
```
/data/test_001 (source_001)
/backup/test_001 (source_000)
/backup/test_001~ (destination_000)
```
Then, after the **2nd run** of rsync -bavr /data /backup, **MY** yield is...
```
/data/test_001 (source_001)
/backup/test_001 (source_001)
/backup/test_001~ (source_000)
```
...where test_001~ (source_000) replaces test_001~ (destination_000)...

...instead of yielding what I think you're yielding, which is:
```
/data/test_001 (source_001)
/backup/test_001 (source_001)
/backup/test_001~ (source_000)
/backup/test_001~~ (destination_000)
```

**NB:** After the 2nd run, if I rename /backup/test_001 (source_001) to /backup/test_001 (source_002), and run rsync a 3rd time, the yield of the run will REPLACE /backup/test_001~ (source_000) with /backup/test_001~ (source_002)...as is consistent with my 2nd run result - the previous backup is replaced by the subsequent backup! Never do I yield multiple tildae! 

Any (additional) thoughts?

---

### Post by XCan on 2009-05-25
Hey maclenin, after some better controlled testing, it appears like I made an embarassing mistake. The behaviour of rsync is indeed as you reported where files only gets renamed once, and every subsequent run would overwrite the old ~file. 

Being no linux guru I can see two ways to remedy this. Either use the --backup-dir or --suffix switch. Perhaps someone could easily whip up a script that would generate a --suffix based on the current date/time whenever it's run?

---

### Post by maclenin on 2009-05-25
No, no! It's the thought that counts! You led me down the right path **XCan**! I would never have tried my (your) little experiment had you not led me to "-b"!

I think (hope) I am starting to put it all together (re: -b options and others) - thanks to your assists - and will certainly use rsync in one of it's many manifestations....

Thanks, again **XCan** - and, hopefully, as (if) my skills improve I'll be able to return the favor in kind!

---

### Post by PGScooter on 2009-05-27
> **XCan said:**
> Hey maclenin, after some better controlled testing, it appears like I made an embarassing mistake. The behaviour of rsync is indeed as you reported where files only gets renamed once, and every subsequent run would overwrite the old ~file. 

Being no linux guru I can see two ways to remedy this. Either use the --backup-dir or --suffix switch. Perhaps someone could easily whip up a script that would generate a --suffix based on the current date/time whenever it's run?

I don't know about nifty, but I think a simple ```
--suffix=`date +%y.%m.%d.%H.%M`
``` should work.

---


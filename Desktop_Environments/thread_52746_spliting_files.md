---
title: "spliting files"
date: 2005-07-28
forum: Desktop Environments
---

### Post by pabc on 2005-07-28
one of the last things I need to get sorted before I get rid of my XP is uploading files to usenet.

I upload a 110MB file each day which on XP I split into 5MB chunks with winrar, add 10% parity with quickpar and upload with powerpost.

the parity (par2 create) and upload (newspost) I have sorted but I dont want to upload the avi in one chunk. I cant find a suitable compressor/archiver which will give me 5mb files which windows uses can easily access.

My best attempt so far is to split the avi with split -d -a 3 -b 5m file.avi file. and then have a script creates a dos bat file which contains 'copy /b file.002 + file.001 [etc....] final_file.avi' but thats hardly elegant.

Is there a simple free way to archive my .avi into chucks that windows winrar will handle?

hopefully;

Phil

---

### Post by cwaldbieser on 2005-07-29
The zipsplit program should do the trick.

---

### Post by pabc on 2005-07-29
[QUOTE=cwaldbieser]The zipsplit program should do the trick.[/QUOTE]

zipsplit only acts on a precreated zip file so I've tried zipping with -0 to store but when I attempt a zipsplit on it I get a strange error;
"entry too big to split (filename.zip)

so I'm guessing zipsplit will only split the zip file where the files inside can be grouped and when you just have one big file it cant do it.

looks like I may end up paying! for winrar on linux which is a tad annoying.

P

---

### Post by strikeforce on 2005-07-29
You can try rar-nonfree which you can grab from the backports which is the the same as rar. It can also be split from the command line.  You need the non-free version btw.

---

### Post by BoyOfDestiny on 2005-10-05
[QUOTE=strikeforce]You can try rar-nonfree which you can grab from the backports which is the the same as rar. It can also be split from the command line.  You need the non-free version btw.[/QUOTE]

I just googled for a front end to 7zip (since there is p7zip for linux)
and found this:
[http://xarchive.sourceforge.net/](http://xarchive.sourceforge.net/)

Looks great! Going to test it myself.

---


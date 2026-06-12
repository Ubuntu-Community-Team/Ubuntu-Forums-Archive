---
title: "[SOLVED] No gui after reiserfsck (rebuild tree)"
date: 2008-12-04
forum: General Help
---

### Post by gully on 2008-12-04
A while ago I used gparted to clone my IDE hard drive to a larger SATA drive.
I noticed that reiserfs doesn't display the right amount of free space after it is cloned to a partition of a different size: [http://ubuntuforums.org/showthread.php?p=6294810](http://ubuntuforums.org/showthread.php?p=6294810) .

I tried the rebuild tree option in reiserfsck to fix this: [http://www.cyberciti.biz/tips/repairing-reiserfs-file-system-with-reiserfsck.html](http://www.cyberciti.biz/tips/repairing-reiserfs-file-system-with-reiserfsck.html) , but when I booted back into hardy there was no gui, I can log in and some commands do work, but there's no gui and important commands like apt-get give "server errors."

This shouldn't be happening and it's things like this that are starting to turn me away from ubuntu (compared to hardy, win xp is an oasis of stability), so please help me get my gui back and I will give linux another chance.

---

### Post by glotz on 2008-12-04
We don't negotiate with terrorists. I just called your blackmail attempt.

---

### Post by gully on 2008-12-04
Alright, but seriously, I want my gui back, I'm not gonna step of ubuntu completely, because it is a nice backup media (survives mobo upgrades and is immune to viruses.)

---

### Post by Herman on 2008-12-07
Here's what the manual page for [reiserfsck]("http://web.archive.org/web/20061113154617/http://www.namesys.com/reiserfsck.html")  has to say about the --scan whole partition option,
> EXPERT OPTIONS
       DO NOT USE THESE OPTIONS UNLESS YOU KNOW WHAT YOU ARE DOING.  WE ARE NOT RESPONSIBLE IF YOU LOSE DATA AS A RESULT OF THESE OPTIONS.

       --no-journal-available
              This  option  allows reiserfsck to proceed when the journal device is not available. This option has no effect when the journal is located on the main data device. NOTE: after this opera&#8208;
              tion you must use reiserfstune to specify a new journal device.

       --scan-whole-partition, -S
              This option causes --rebuild-tree to scan the whole partition but not only the used space on the partition.
GParted has a feature for checking all file systems and resizing them to fill the partition.
No commands necessary, you just need to do this, [Running a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_").
For a reiserfs partition, that will run '*reiserfsck --yes --fix-fixable --quiet /dev/sdxy*' for you, and after that it will run *[resize_reiserfs]("http://web.archive.org/web/20061113154617/http://www.namesys.com/resize_reiserfs.html")[]("http://www.namesys.com/resize_reiserfs.html")*.

It that doesn't work, try reiserfsck again with the --rebuild-tree option and leave out the --scan-whole-partition part this time.

[resize_reiserfs]("http://web.archive.org/web/20061113154617/http://www.namesys.com/resize_reiserfs.html")  is probably all you really needed in the first place. It always happens that cloning or dd-ing a file system to another partition results in a file system that doesn't fill the partition and we always need to run resize reiserfs or resize2fs or whatever afterwards, it doesn't matter what file system we use.

Goodluck with it, I hope that helps,
Regards, Herman :)

---

### Post by gully on 2008-12-07
Thanks, I'll try that, the funny thing is that I just found about resize_reiserfs half an hour ago while googling, it seems to be precisely what I was looking for.

---

### Post by gully on 2008-12-07
It worked!

Thank you! I finally got this thing solved.

Btw, I installed intrepid (no bugs so far, a definite improvement over hardy) on another partition.

---

### Post by Herman on 2008-12-08
:p Cool! ...can you please mark this thread as 'solved'?  -the might help someone else with a similar problem find their answer quicker, thanks. 

ReiserFS is actually a very easy file system to deal with. 

Just for the future, here's what I do with mine.

(But first, I have to remind everyone to never runa file system check in a mounted file system, use a LiveCD if possible.)

The reiserfs --check command is the one to run first, it just runs a quick check (takes a look around), and tells you if anything is wrong. 
This is a safe command for anyone to run at any time you like. 
It doesn't fix anything, but you can use this whenever you want to perform a routine disk check just to make sure everything's okay.
The feedback from this quick check will tell you if any more work is needed.
```
sudo reiserfsck --check --logfile check.log /dev/sda2
```Where: /dev/sda2 is the partition with the reiser file system in it, use a different number to suit your system if yours is different.
**[B]NOTE:** [/B]After you press 'enter', you will see a message to let you know what reiserfsck will do for you and asking you to confirm.
Make sure you type 'Yes', (with a capital 'Y') after the prompt, or nothing will happen.

The feedback from this quick check will tell you if any more work is needed.
It will tell you if you need to run reiseerfsck again with the --fix-fixable option or with the --rebuild-tree option, (or something else, but usually one of those two).

The you jsut run whichever command you need,
```
sudo reiserfsck --fix-fixable --logfile fixable.log /dev/sda2
```[FONT=Bitstream Vera Sans Mono]
or
[/FONT]```
sudo reiserfsck --rebuild-tree --logfile rebuild.log /dev/sda2
```Mostly, those two commands will almost always fix whatever's wrong.

And of course now you know about resize_reiserfs too.

There are a few more tricks and tweaks you can learn about ReiserFS, but now you already know the main things, and probably you won't even need to know that again anytime soon. 

Sometimes I just use GParted too, even though I know the command line method. Gnome Partition Editor is great, I always install it in my operating systems.

I'm glad that worked for you.


Happy Ubuntiung
Regards, Herman :)

---


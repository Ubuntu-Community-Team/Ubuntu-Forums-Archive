---
title: "fragmentation / non-contiguous / 18% (high?)"
date: 2005-12-23
forum: Desktop Environments
---

### Post by towsonu2003 on 2005-12-23
[edit]poll above to see what others are seein in their systems[/edit]

the situation: 
fsck just checked my etx3 filesystem and reported that there was 18% contiguous something (sorry, don't remember exact term, possibly 'blocks') in my /home partition. here the usage stats of my home partition: ```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6              19G  715M   18G   4% /home
```
so its very empty... 

I did some research on this, and responses were a little diverse, but all said there is no defrag utility. Below are what I found about this. My question is: isn't 18% too much anyway? and why did that happen? this is no more than a 2-months old installation. too much reboot maybe (this is laptop)?

So people say:
> I think we're going to see more and more need for defrag utilities. I think, just based on usage, that desktops create more fragmentation than servers. [http://www.linuxquestions.org/questions/showthread.php?t=354960](http://www.linuxquestions.org/questions/showthread.php?t=354960)

> I wouldn't worry about that I've never seen ext3 filesystem go above 10 percent fragmentation.[http://www.linuxquestions.org/questions/showthread.php?t=349041](http://www.linuxquestions.org/questions/showthread.php?t=349041)

> Note that non-contiguous does not necessarily mean fragmented.  Files
that are larger than a block group will be non-contiguous by
definition.  On the other hand if you have more than one file
simultaneously being written to in a directory, then yes the files
will certainly get fragmented.[https://www.redhat.com/archives/ext3-users/2004-March/msg00005.html](https://www.redhat.com/archives/ext3-users/2004-March/msg00005.html)
could not understand what it is saying above...

> Defragmenting does not help at all since, after the fragmentation, the file system will quickly reach again the fragmentation level suitable for the utilization of the file system and will remain there. (...) Defragmentation is a waste of time[http://portal.suse.com/sdb/en/2002/06/ext2frag.html](http://portal.suse.com/sdb/en/2002/06/ext2frag.html) 
above is talking about ext2 filesystems.

thanks

---

### Post by fordfan753 on 2005-12-23
This is why I like reiserfs, it seems to be almost immune to fragmentation and it's really good with many small files

---

### Post by cwaldbieser on 2005-12-23
[QUOTE=towsonu2003]the situation: 
fsck just checked my etx3 filesystem and reported that there was 18% contiguous something (sorry, don't remember exact term, possibly 'blocks') in my /home partition. here the usage stats of my home partition: ```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6              19G  715M   18G   4% /home
```
so its very empty... 

I did some research on this, and responses were a little diverse, but all said there is no defrag utility. Below are what I found about this. My question is: isn't 18% too much anyway? and why did that happen? this is no more than a 2-months old installation. too much reboot maybe (this is laptop)?

So people say:
 [http://www.linuxquestions.org/questions/showthread.php?t=354960](http://www.linuxquestions.org/questions/showthread.php?t=354960)

[http://www.linuxquestions.org/questions/showthread.php?t=349041](http://www.linuxquestions.org/questions/showthread.php?t=349041)

[https://www.redhat.com/archives/ext3-users/2004-March/msg00005.html](https://www.redhat.com/archives/ext3-users/2004-March/msg00005.html)
could not understand what it is saying above...

[http://portal.suse.com/sdb/en/2002/06/ext2frag.html](http://portal.suse.com/sdb/en/2002/06/ext2frag.html) 
above is talking about ext2 filesystems.

thanks[/QUOTE]

Have you noticed some sort of performance degredation with regards to your drive?

---

### Post by towsonu2003 on 2005-12-23
[QUOTE=cwaldbieser]Have you noticed some sort of performance degredation with regards to your drive?[/QUOTE]

My brief response is no:
I am having performance issues but I believe these are related to ATI video card (using ati) and firefox bugs... Best examples would be 1-high CPU usage for stuff that's not supposed to use that much CPU (firefox browsing web and coming accross a flash object; or mplayer playing a video) and 2-firefox sucking up my RAM. I wouldn't associates these to fragmentation if this was Windows, but rules are different here?

---

### Post by bernardfrancois on 2005-12-23
Can someone tell me how I get the percentage of uncontiguous blocks? I'm curious about the situation on my 366mhz laptop. I install/uninstall a lot of software, and the 6gb hard disk has been almost full all the time.

About the browser... I'm using Opera, and everything runs smooth (only the starting of opera takes a lot of time, but once started it browses very fast).

Maybe another reason why linux doesn't get fragmented as much is because there is a separate partition for swapping. In an operating system where the virtual memory data is put together with regular files, there must be more fragmentation. I don't know much (yet) about file systems and the way data is organised on a hard disc; this is nothing more than a guess.

---

### Post by towsonu2003 on 2005-12-23
[QUOTE=bernardfrancois]Can someone tell me how I get the percentage of uncontiguous blocks? [/quote] ```
sudo shutdown -Fr
``` F for forcing fsck (the utility that checks filesystem **integrity**) ; r for rebooting. (So it will restart your machine and force check --> once you press enter, you'll loose unsaved data).

I would just wait for the 30th mount or so (when it automatically forces fsck on / ) - Not worth the reboot :)

---

### Post by cwaldbieser on 2005-12-23
[QUOTE=towsonu2003]My brief response is no:
I am having performance issues but I believe these are related to ATI video card (using ati) and firefox bugs... Best examples would be 1-high CPU usage for stuff that's not supposed to use that much CPU (firefox browsing web and coming accross a flash object; or mplayer playing a video) and 2-firefox sucking up my RAM. I wouldn't associates these to fragmentation if this was Windows, but rules are different here?[/QUOTE]
If you ever do run into a problem, this article suggests how you might go about defragmenting the hard way:
[http://www.itworld.com/Comp/3380/nls_unixfrag040929/]("http://www.itworld.com/Comp/3380/nls_unixfrag040929/")
The article suggests you shouldn't really run into this problem unless you have files you keep appending information to, though.

---

### Post by towsonu2003 on 2005-12-24
> While you're unlikely to see many Unix systems with fragmentation reaching higher than 5%, it's good to know what you can do to defragment a file system if and when you run into this situation. The classical method is to back up the file system with a program such as dump or ufsdump, rebuild the file system with a command such as newfs or mkfs, and then reload the file system from the backup. On a large file system, this operation can take several hours to run.

what do you mean by "files you keep appending information to"? an example would be soooo good? (native language is not english, so sometimes it's hard to grasp the things around :) )

Also, is s/he basically telling in the article to 'format the thing and that's it'?

---

### Post by cwaldbieser on 2005-12-24
[QUOTE=towsonu2003]what do you mean by "files you keep appending information to"? an example would be soooo good? (native language is not english, so sometimes it's hard to grasp the things around :) )

Also, is s/he basically telling in the article to 'format the thing and that's it'?[/QUOTE]
It means you start with a file of a certain size, but then you make it bigger, then you make it bigger again, then you make it bigger again, etc...

The author says that in ext3, extra space is pre-allocated for files, so they don't get fragmented, be if you keep adding to the file, eventually the pre-allocated space gets used up.

The author's defragmentation process is more or less like this:

1) Copy the data elsewhere.
2) Destroy the partition.
3) Recreate the partition.
4) Copy the data back.

It is somewhat drastic.  In a lot of normal cases, the expectation is that you are probably going to buy a new hard disk before you ever get to the point where you would need to do that.

---

### Post by towsonu2003 on 2006-01-20
just an update: fragmentation is now down to 15% after 35 mounts, without me taking any action against it (waiting for dapper and graduation to get rid of spss and most of my ntfs)

also added a poll to see what others are seeing.

---

### Post by bernardfrancois on 2006-01-20
[QUOTE=towsonu2003]```
sudo shutdown -Fr
``` F for forcing fsck (the utility that checks filesystem **integrity**) ; r for rebooting. (So it will restart your machine and force check --> once you press enter, you'll loose unsaved data).
[/QUOTE]

Where do I check the percentage of non-contiguous blocks after I did this? Maybe you can put the answer in the first post, since you added a poll to this topic...

Or is there any log file where I can find this information, stored from last time when my root partition got checked?
I tried a **sudo rgrep 'blocks\|contiguous' $(find /var/log) 2> /dev/null**, but I didn't find any useful information...

---

### Post by bernardfrancois on 2006-01-24
When I booted my computer today, it was accidently the 30th mount time for my root partiton, and the percentage of uncontiguous blocks appeared on my screen.
It was 3.7%

Not too bad I guess? I expected worse, because my hard disk has been almost full all the time, and I installed/uninstalled a lot of software.

I don't know the exact definition of an uncontiguous block, so in fact I have no clue what that value of 3.7 pct means. I guess that if the blocks of one file are located in whole different areas of the hard disk, that it won't change the number of uncontiguous blocks, while this is - in my eyes - a form of fragmentation (and it will take longer to read a file like that because the hard disk's read/write heads will have to move more).

Maybe after my exams I'll write a script to measure fragmentation like that... (or is it already included in the percentage of uncontiguous blocks? In any case I will first check it out before I start writing a useless script :) )
Then I'll be able to use the knowledge I accumulated at school during statistics and unix classes...

---

### Post by towsonu2003 on 2006-01-24
[QUOTE=bernardfrancois]Where do I check the percentage of non-contiguous blocks after I did this? [/QUOTE] I don't exactly know where (as in "file") to check it, that's the reason I did not put any information on how to check this in my first post. In my computer, fsck runs every 35 mounts and the non-contigious thingy is displyed during boot, right after the check is over. you can also fsck the drive using a live cd (bc it has to be not mounted at the time of check) but I didn't do research on fsck, so I don't know the exact commands. man fsck should help wityh that. be careful as I remember fsck being a little dangerous.

---

### Post by christhemonkey on 2006-03-27
just to say,
```
sudo fsck -n
```
will do a fsck without actually doing anything at all.
Just my $0.02

---

### Post by dasunst3r on 2006-03-27
I use xfs on my laptop.  That's also not as prone to fragmentation.

---

### Post by Scunizi on 2006-03-28
I just had to reinstall Dapper again 'cause I hosed it.  After doing all the updates  from Flight 5 to current it asked for a reboot.  On rebooting it checked the root and immediatly went into diskcheck.  That runs FOREVER and have never seen the end of it yet.  Anyone have any idea what's going on?  ](*,)

---

### Post by Drakkor on 2006-11-14
Hmmmmmm..... trying to also figure this out... on boot it said my Media/Data
(hdb3)ext3 partition was 17.7% non-contiguous. I unmounted it and ran fsck,but it basically told me nothing e.g.
drakkor@Ubuntu-Edgy:~$ sudo fsck /dev/hdb3
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
Media Data: clean, 3610/4538368 files, 6135733/9054635 blocks 
:confused:

---

### Post by ShadowVlican on 2006-11-14
i thought linux doesn't get fragmented, well that was due to a comment of a linux user laughing at window's many defragmenting programs

now i know....

---

### Post by towsonu2003 on 2006-11-15
> **ShadowVlican said:**
> i thought linux doesn't get fragmented, well that was due to a comment of a linux user laughing at window's many defragmenting programs

it fragments alright, but it is supposed to take care of the issue itself unless the disk is 90%+ full. that's why there is no usable / stable defragmentation tool for linux. 

the problem is, 
[LIST=1]
[*]Is non-contiguous in Linux = fragmented in Windows?
[*]Is 18% a lot in Linux?
[*]Do we need to worry?
[*]If 1 and 2 are positive, why is this happening? It clearly isn't supposed to... 
[/LIST]

PS. As far as I understand, the only perfect way to defragment a filesystem in Linux is to reformat it, which clearly tells us that fragmentation isnt a problem in Linux.

---

### Post by ericesque on 2006-11-15
@towsonu 
" 1. Is non-contagious in Linux = fragmented in Windows?"

Nope.  Non-contagious in Linux = VERY contagious in Windows.


I have 2 partitions which are ext3-- both are media partitions which are accessed from both windows (using some driver I found) and from linux.  whenever fsck runs, both of these drives wind up with well over 50% non-contiguous.  Though there is no apparent loss of performance.

I don't care where my files are as long as the performance is right.  Although, when I see those numbers, it always makes me feel like my install is dirty.

---

### Post by FyreBrand on 2006-11-15
ext2/3 file systems don't handle storage the same way fat32 or NTFS does.  Files stored on a hard drive using ext3 don't need to be stored in a linear or contiguous fashion.

ext2/3 uses pointers to the data on a disk.  These pointers are called [**inodes**]("http://en.wikipedia.org/wiki/Inodes").  

I found an excellent article and description of what's going on in the ext2/3 file system.  It's very detailed with reference links for more reading.  Good stuff!! Here is a link to the Google-Answers article: [**file system limitations RedHat 7.3, ext3**]("http://answers.google.com/answers/threadview?id=122241") There is some really good stuff in there.

The [**OCLUG**]("http://www.oclug.on.ca/") site was another good reference.  Here is one article: [**OCLUG - Defrag Windows**]("http://www.oclug.on.ca/archives/oclug/2003-December/036290.html").

The short answer I got from these articles is that fragmentation is basically irrelevant to the performance of this type of file system.  It is the inodes and more specifically the number of inodes pointing to one location and the depth (indirect, double indirect, and triple indirect) that affect the performance of a drive.

I like how the OCLUG guy in that message discussed good disk hygiene.  It made me laugh, but it's true.


I hope that information is helpful.

---


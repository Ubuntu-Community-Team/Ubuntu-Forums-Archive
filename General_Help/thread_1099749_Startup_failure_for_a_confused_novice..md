---
title: "Startup failure for a confused novice."
date: 2009-03-18
forum: General Help
---

### Post by Anne Sejer on 2009-03-18
For three months I have enjoyed getting to know Ubuntu better. I am no computer nerd, but I am greatly impressed by any community of people who can put together such a wonderful achievment with nothing to gain but the pleasure of having fun with their work, and hopefully each other - thanks to all. Now however I am standing with my hat in my hand.... 

The past few days my computer has been acting funny, programs won't start or won't shut down.... All things which made me doubt if I was really getting a handle on learning to find my way around in this new medium, or if there was something wrong. Now upon starting up today, I am confronted with a black screen with a bunch of text


Checking drive /dev/sda1: 19% (stage 1/5, 59/214)
/dev/sda1: Inode 485422 has illegal block(s)

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
         (i.e., without -a or-p options)
fsck died with exit status 4
                                                      (fail)
* An automatic file system check (fsck) of the root filesystem failed. A manual fsck should be preformed in maintenance mode with the root filesystem mounted in read-only mode.
* The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system. 
bash: no job control in this shell
root@anne-laptop~#




I have NO idea of what this means or how to proceed. Would some one be so kind as to guide me to a higher level of understanding?

---

### Post by mpeltz on 2009-03-18
I wish I was as far as you were.  I am getting a similar text and I have been unable to even get started with ubuntu.  Everytime I try to load it....I can't seem to get very far. Very frustrating. I have posted a question on how to get started installing this program.  Good luck.  Sorry I can't help, but I do feel your pain. Perhaps, reinstalling the program might work?

---

### Post by Anne Sejer on 2009-03-18
Hi! I am the one who was asking for help and now I too am the one wishing I could give it..... I was really impressed by how quickly (and more or less easily) the OS guided me through installation and found itself at home in my old DELL Inspiron 8600. I can only advise that you perservere - it is a fun OS, and a wonderfull alternativ to what is commercially available from the evil empire ;)

I hope it all works out for you!

AS

---

### Post by fieroboom on 2009-03-18
> **Anne Sejer said:**
> 
Checking drive /dev/sda1: 19% (stage 1/5, 59/214)
/dev/sda1: Inode 485422 has illegal block(s)

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
         (i.e., without -a or-p options)
fsck died with exit status 4
                                                      (fail)
* An automatic file system check (fsck) of the root filesystem failed. A manual fsck should be preformed in maintenance mode with the root filesystem mounted in read-only mode.
* The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system. 
bash: no job control in this shell
root@anne-laptop~#




I have NO idea of what this means or how to proceed. Would some one be so kind as to guide me to a higher level of understanding?

This is telling you something is wrong with your hard drive, like a corrupted or unusable block.
See [this thread](http://ubuntuforums.org/showthread.php?t=256949).
Also, in the future, a [quick google search of the error](http://www.google.com/search?hl=en&safe=off&newwindow=1&q=UNEXPECTED+INCONSISTENCY%3B+RUN+fsck+MANUALLY.&btnG=Search) before starting a new thread will usually give you much more information, and a much quicker answer.
:D
-Paul

EDIT:
Now that I re-read my post, it kinda sounds mean, but that's not my intent. We all started as a novice, and we all had to learn from somewhere. My remark for searching google isn't meant to shy you away, but to give you another avenue to solve your issue. If you just get told what to do, you'll probably forget, but if you have to search for it, I guarantee you'll remember, and then you can help the next guy! :D

---

### Post by Anne Sejer on 2009-03-18
Hi Super thanks! I didn't take it mean. The funny thing is while I was waiting for someone to answer I sort of got the idea myself, and searched in this forum under fsck that already helped a bit but your reference gave me a bit more patience. I have learned a bit. Thanks!
AS

---

### Post by ajgreeny on 2009-03-18
As ypu may already have done, boot to your live CD, open a terminal and run ```
sudo fsck /dev/sda1
```  Hopefully it will find and repair any problems you have on your disk.

Good luck!

---

### Post by freeediver on 2009-05-25
OK dumb me, I have the same problem.
What do you refer to as Live CD ?
I restated with my CD and I get this screen
try ubuntu without change...
install ubuntu...
check cd for defects
test memory
boot from first hard disk.

A couple lines below I get a line that says press f4 to sel. alt start-up and install modes.
Below that the normal f1 help f2 language, f3 keymap etc etc.
f6 is other options

OK now what and how do I do it?

How do I proceed to follow your previous inst.?

Thanks, I'm lost

My comp just heaved and looks like it is doing a complete re-install
anything that I can do now to save my files?

---

### Post by merlinus on 2009-05-25
try ubuntu without change...

When it is up-and-running, open a terminal (Applications/Accessories/Terminal) and type in the command that ajgreeny wrote.

---

### Post by halcyonhell on 2009-05-26
Hi. I'm running 7.04 and i get almost the exact same error with fsck except, the /dev/shm/root is scanning. It gets to 70 something % and fails. What should i do? Boot from disk and run sudo fsck /dev/shm/root maybe?

---

### Post by freeediver on 2009-05-26
Ok I did that and this is what pops up on my screen:
fsck 1.40.8 (13-march-2008)
e2fsck 1.40.8 ( 13-march-2008)
fsck.ext2: No such file or directory while trying to open /dev/sdal

The superblock could not be read oe does not discribe a correct ext2 filesystem. If the device is valid and it really contains a ext2 filesystem ( and not swap or ufs oe something else ), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
 e2fsck -b 8193 <device>

ubuntu@ubuntu:-$
OK I'm really lost now.
All I have (had) on my laptop is ubuntu with no partitions
Any ideas would be welcome.

On a side note when I am reading and trying to follow instructions like those above to open a term. and write sudo etc. etc. is can be tough to know where spaces actually belong, it took me 3 trys
to get the command to be accepted, all because of spaces.

**Salvation It Works and I don't know why. I'm hoping the sudo command that was suggested did the trick... Thanks Much**

---

### Post by halcyonhell on 2009-05-26
After doing the fsck /dev/shm/root, a million yeses later, maintenance shell failed to open, then rebooted, logged in and I lost 2 years worth of files. Rebooted and now its auto scanning /dev/sda1 again. should I be worried about more data loss? Hopefully this one wont fail and it will return to normal.

System: Intel S5000VSAS Board
        2x 320GB in a RAID 1 array       
        Ubuntu 7.04

Ive had the problem before with rebooting and the fsck, but then no problems. Had data loss but restarted and everything was back again. I never shut it down because it is a file server. Is a fresh installation and backups my final solution after 2 days of downtime?

---

### Post by kiridude on 2009-05-26
> **freeediver said:**
> Ok I did that and this is what pops up on my screen:
fsck 1.40.8 (13-march-2008)
e2fsck 1.40.8 ( 13-march-2008)
fsck.ext2: No such file or directory while trying to open /dev/sdal

The superblock could not be read oe does not discribe a correct ext2 filesystem. If the device is valid and it really contains a ext2 filesystem ( and not swap or ufs oe something else ), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
 e2fsck -b 8193 <device>

ubuntu@ubuntu:-$
OK I'm really lost now.
All I have (had) on my laptop is ubuntu with no partitions
Any ideas would be welcome.

On a side note when I am reading and trying to follow instructions like those above to open a term. and write sudo etc. etc. is can be tough to know where spaces actually belong, it took me 3 trys
to get the command to be accepted, all because of spaces.

**Salvation It Works and I don't know why. I'm hoping the sudo command that was suggested did the trick... Thanks Much**

Freediver, you're superblock is corrupted and that's kind of a bad situation. check out a thread I was helping someone with yesterday and at the end you'll find a post by "unutbu" detailing a procedure to use an alternate superblock.

As far as the spaces go, click in the code and use your cursor to see if there is a space or not.

---

### Post by kiridude on 2009-05-26
> **halcyonhell said:**
> After doing the fsck /dev/shm/root, a million yeses later, maintenance shell failed to open, then rebooted, logged in and I lost 2 years worth of files. Rebooted and now its auto scanning /dev/sda1 again. should I be worried about more data loss? Hopefully this one wont fail and it will return to normal.

System: Intel S5000VSAS Board
        2x 320GB in a RAID 1 array       
        Ubuntu 7.04

Ive had the problem before with rebooting and the fsck, but then no problems. Had data loss but restarted and everything was back again. I never shut it down because it is a file server. Is a fresh installation and backups my final solution after 2 days of downtime?

Go [here]("https://help.ubuntu.com/community/DataRecovery") for info on data recovery. Also I would suggest you update to the newest version of Ubuntu. I don't see any reason for using such an outdated version.

---

### Post by halcyonhell on 2009-05-26
finished the scan. all files from the day after the 18 Sep 2007 up until yesterday are gone. the remaining files are dated the same day i copied everything to the server. Why would it revert back to then? why cant i access the lost+found folder through the admin account? why would ubuntu fail so dramatically?

---

### Post by lan3y on 2009-05-26
well you are using an outdated version of ubuntu, you should take what files you have and upgrade ubuntu,

you can either do this through the update manager or download a cd image from ubuntu.com , the latest version is now jaunty jackalope (ubuntu 9.04).

lan3y

---

### Post by freeediver on 2009-05-26
I spoke to soon the error is back.
I can bypass the check disk ( esc during the startup) but I would rather it work properly.
What now, I will try to locate the Ubuntu thread, do you have a link?
When I bypass the check disk during startup everything seems to work properly, i'm using my "broke" comp to
write this now.

I found the thread and it seems more than a bit confusing, no way do I have 270gig to play with.
Is there any other way to repair my system or should I just reinstall from the get go or is it time for a new comp?
I did save/backup all my files.

---

### Post by kiridude on 2009-05-26
> **halcyonhell said:**
> finished the scan. all files from the day after the 18 Sep 2007 up until yesterday are gone. the remaining files are dated the same day i copied everything to the server. Why would it revert back to then? why cant i access the lost+found folder through the admin account? why would ubuntu fail so dramatically?

Halcyonhell, check out the link I suggested in my last response to you. There are ways to recover your data.

---

### Post by kiridude on 2009-05-26
> **freeediver said:**
> I spoke to soon the error is back.
I can bypass the check disk ( esc during the startup) but I would rather it work properly.
What now, I will try to locate the Ubuntu thread, do you have a link?
When I bypass the check disk during startup everything seems to work properly, i'm using my "broke" comp to
write this now.

I found the thread and it seems more than a bit confusing, no way do I have 270gig to play with.
Is there any other way to repair my system or should I just reinstall from the get go or is it time for a new comp?
I did save/backup all my files.

Freediver, let the computer do the check disk, it may clear up your problem. If not, since you're backed up, I would suggest a re-install - its definely less confusing than using alternate superblocks. And sorry I forgot to include the link in my response :)

---

### Post by freeediver on 2009-05-27
using h.h. so please excuse the x2 post.
Silly question but if I upgrade my system  from 8.04 to 8.10 could that resolve my issues? is there any easy way to repair my installation?
Well thats the problem, when the disk check runs it hangs and gives me the error message, when I bypass the check disk everything runs fine. Is there any way to repair my installation or like I asked above will an major update cure the issue ? I'm stumped, if I have a bad HD why would everything work if I bypass the check feature? 
I have copied everything to a backup drive but what about the corrupt file?
Thanks

---

### Post by kiridude on 2009-05-27
> **freeediver said:**
> using h.h. so please excuse the x2 post.
Silly question but if I upgrade my system  from 8.04 to 8.10 could that resolve my issues? is there any easy way to repair my installation?
Well thats the problem, when the disk check runs it hangs and gives me the error message, when I bypass the check disk everything runs fine. Is there any way to repair my installation or like I asked above will an major update cure the issue ? I'm stumped, if I have a bad HD why would everything work if I bypass the check feature? 
I have copied everything to a backup drive but what about the corrupt file?
Thanks

Freediver, do a fresh install with 9.04, many issues have been fixed. Don't waste time with outdated versions.

---

### Post by freeediver on 2009-05-27
OK
Just so I don't screw it up what is the process for a complete fresh install vs. upgrade from 8.04 to 9.04.
I still have my original Ubuntu install disk.
I have a Toshiba  laptop Satellite a105 S2031.
Plenty of memory all else is as delivered.
It might be time for a new H.D. as well, who knows???
I might be reading this with my H.H. as I do the install.

Thanks

---

### Post by kiridude on 2009-05-27
download the image of 9.04 and burn to cd. Insert the cd and restart your machine. Follow directions for installation and you're done!

At the partition phase, simply choose the partition where you had you're previous linux os and it will overwrite it. No point in doing upgrades with corrupt superblock.

---

### Post by freeediver on 2009-05-27
Thanks
Will I be informed when in the partition phase where my previous
version is located?
I have been reading that an upgrade to 8.10 might be necessary
before installing 9.04 or is that only referring to the upgrade process from 8.04 to 8.10 to 9.04?
Any advice on the best U.S site to download from? I had issue's in the past that why I bought the CD.
Any 9.04 cd's out there?

---

### Post by kiridude on 2009-05-28
Yes, you will be informed, it's very user friendly and hard to go wrong. You will look for the partition labeled Linux. If you do not want a dual boot with windows, simply choose the "whole disk" option and you don't have to worry about partitions.

I am not suggesting an upgrade, but a new installation, so going to 8.10 does not come into play. 

Best place to download: Ubuntu.com

---

### Post by freeediver on 2009-05-28
Thanks
I've done that and just made a new post concerning the MD5SUM check procedure, I'm stuck. Terminal says no directory exists yet the DL file is sitting in my DL box 699Mb.
Title
Install 9.04
[http://ubuntuforums.org/showthread.php?t=1172582](http://ubuntuforums.org/showthread.php?t=1172582)

---


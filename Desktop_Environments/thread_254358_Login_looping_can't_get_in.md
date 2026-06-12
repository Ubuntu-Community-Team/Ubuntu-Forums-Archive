---
title: "Login looping can't get in"
date: 2006-09-09
forum: Desktop Environments
---

### Post by johnbl on 2006-09-09
Using Dapper, updated to last advice on automatic - it says new available I let it instal!

Has been running without a problem then this am started as normal, username accepted, password accepted - in that there was no message screen blinks - as normal and for all intents is loading then, Username / password sequence restarts.

Tried using a dummy name password and did get a case message, other than that muti attemptsd and zip!

Tried adminisitrator session and message came back about possible disk full prventing a write operation.......

Is there any way of gaining some form of access to verify disk condition and removing some data?

Booting from a dist disk in demo wont allow any hard disk access as I understand so that's out...

Stumped here.

It was all working just so well. <sigh>

Any help most appreciated, I don't want to wipe everything with a new install, some I can't replace! Dummy me.

John

---

### Post by mssever on 2006-09-10
I'm not sure if I quite understand your problem, so please forgive me if I tell you to do something you can't do. I don't know what you mean by an administrator session.

First, try booting into recovery mode (do this from the Grub menu. If there's no grub menu at boot, hit escape and it'll appear). Look for errors in the files ~youruser/.xsession-errors and the logs in /var/log. Type startx if you want a graphical environment.

To see if your disk is full, type df -h

To check your disk, run ```
fsck -A
``` Use sudo if you're not running in recovery mode.

Also, it is perfectly possible to mount hard disk partitions from the live CD. Simply type ```
sudo mount -t ext3 /dev/hda1 /mnt
``` making changes as appropriate. See "man mount" for help.

---

### Post by johnbl on 2006-09-10
Sorry for the lack of clarity.
Had used the old sessions to try and gain access. Looped back to login every time.
Tried your suggestion as to Esc and recovery. Appeared to work. Many lines flashed by. Ultimately asked for login as root, used my own, rejected that. Used Crtl D, normal login screen and looping again. Then message came up;

GDM Could not write to your authorisation file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case it is not possible to log in. Please contact your system administrator.

Had a word with myself as Amin and decided I didn't know what the question was....<g>


So there must be a way of getting in as  ' system admin ' it's the how? Some form of system recovery for system recovery maybe <g>....

---

### Post by mssever on 2006-09-11
> **johnbl said:**
> Sorry for the lack of clarity.
Had used the old sessions to try and gain access. Looped back to login every time.
Tried your suggestion as to Esc and recovery. Appeared to work. Many lines flashed by. Ultimately asked for login as root, used my own, rejected that. Used Crtl D, normal login screen and looping again. Then message came up;

GDM Could not write to your authorisation file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case it is not possible to log in. Please contact your system administrator.

Had a word with myself as Amin and decided I didn't know what the question was....<g>


So there must be a way of getting in as  ' system admin ' it's the how? Some form of system recovery for system recovery maybe <g>....
The system admin recovery thingie is recovery mode. It never asks me for a password. Did you enable the root password? If so, use that.

Alternately, you can try to log in from the console (when running in normal mode): Press Ctrl+Alt+F1 to access the console. (There are actually 6 consoles; substitute F2..F6 for F1 above. To get to the graphical version, it's Ctrl+Alt+F7.) Try logging in then. If there are errors, please post them. Otherwise, type ```
df -h
``` to check your disk space. Type ```
sudo /etc/init.d/gdm stop
``` to kill GDM, then type ```
startx
``` and see if things work that way. Post any errors that show up on the console.

Here's a tip for asking questions so that you get better, faster help: Be specific. Describe the symtoms and what you've tried *thouroughly* and completely. Don't assume that someone can figure out your problem by seeing only a handful of scattered facts. Also, write complete, grammatical sentences. It makes your question much easier to understand. Pretend you were being graded by an English teacher.

---

### Post by casperlingus on 2006-09-12
This is identical to my problem.  Twice now my Dell Precision M90 laptop has crashed like this.  I try to log in and I get looped.  I can't even switch to  any of the other terminals with Alt-Ctrl-F1,F2, etc.  Just blank screens.   When I boot into recovery mode and do df -h, it tells me my HDD is 100% full, 16GB/16GB.

When I boot a live CD and mount the hard drive, a df -h tells me the same thing.  But when I query the root directory (using properties, from Nautilus) it tells me there's only 7GB of files. 

I removed a ton of stuff, and df -h still tells me 100% full.  I don't still have my system like that, as this is my work machine and I didn't have time to mess around, I just reformatted/reinstalled.

This happened a second time and I decided to use SuSE to reinstall.  Unfortunately, SUSE is not pleasing and I want to go back to Ubuntu, but I can't keep reformatting my OS like this.  At least I keep all my stuff on a separate HDD so recovery after reinstalling the OS isn't too bad.

Ideas?  I might just reinstall Ubuntu *again* and hopefully have a DB of ideas here waiting for me the next time it happens (seems to be about every 1.5 months).

Casper...

---

### Post by mssever on 2006-09-12
It could be core dumps, although I haven't seen any core dumps in Ubuntu. A core dump is basically a memory dump made when a program crashes under certain situations. If you have any core files lying around, they can be eating your disk space. Do
```
sudo updatedb && locate core | less
``` to check for coredumps. If you find any, delete them. They're only useful for debugging.

Another thing to try to pin down the offending file(s) is to run du -h. Start with du -h /bin, du -h /home, etc. Then look in further subdirectories. What you're looking for is someting that seems unusually large. When you find that, investigate (ls -lA). This will probably take some time, but you'll probably only need to do it once, as you'll find out where the problem is. Then, you can fix that problem/ask for help.

---

### Post by johnbl on 2006-09-12
> **casperlingus said:**
> This is identical to my problem.  Twice now my Dell Precision M90 laptop has crashed like this.  I try to log in and I get looped.  I can't even switch to  any of the other terminals with Alt-Ctrl-F1,F2, etc.  Just blank screens.   When I boot into recovery mode and do df -h, it tells me my HDD is 100% full, 16GB/16GB.

When I boot a live CD and mount the hard drive, a df -h tells me the same thing.  But when I query the root directory (using properties, from Nautilus) it tells me there's only 7GB of files. 

I removed a ton of stuff, and df -h still tells me 100% full.  I don't still have my system like that, as this is my work machine and I didn't have time to mess around, I just reformatted/reinstalled.

This happened a second time and I decided to use SuSE to reinstall.  Unfortunately, SUSE is not pleasing and I want to go back to Ubuntu, but I can't keep reformatting my OS like this.  At least I keep all my stuff on a separate HDD so recovery after reinstalling the OS isn't too bad.

Ideas?  I might just reinstall Ubuntu *again* and hopefully have a DB of ideas here waiting for me the next time it happens (seems to be about every 1.5 months).

Casper...
I'm lucky in that my system is non production - or rather it's my road machine and I have a couple of weeks before I have to rely on it again. Your positions must be horrific.
Am a tad flumoxed that this problem is appearing for many users - or so a troll through the forms would suggest - yet no in depth anaysis by those with the real skill have posted a definative answer as to cause or resolve. As a tyre kicking newbie who just LOVES Ubuntus saving graces that's not me unfortunately. But is this was a MS problem, how many computers would be selling one can only wonder at!
As for me, I'm still grateful for and trying all the suggestions with fingers crossed. <VBG>
John

---

### Post by mssever on 2006-09-13
I just remembered something else. If you've enabled disk quotas, you could be running up against that.

I haven't seen any other threads about 100% disk full errors--although I haven't looked for them, either. But I'm positive that this isn't a common problem. "Those with real skill" don't have enough information at this point to be able to solve it, IMO. Given that this is an uncommon problem, merely stating that the disk is 100% full doesn't give any clues as to what the problem is. Either something is messed up regarding quotas, or something is writing a huge amount of data to disk--that much is plain. But without knowing where the bottleneck is, it's impossible to give more details. That's why I asked the troubleshooting questions above.

And, by the way, if this were a Microsoft problem, they'd still sell as many copies of Windows as before, because they have a near monopoly. Also, remember that this is a tech support forum, which means that people post when they run into problems. This forum is a poor measurement of those who have a trouble-free experience with Ubuntu.

---

### Post by johnbl on 2006-09-13
COREDUMPS?
core returns a long list of every thing with core in the name.
What extension would a coredump be identified by?

On what does something mean.
Still attempting to get the a notebook to accept username / password. But hd is showing a 100% full, and I have NO idea how that could be so. In perusing via recovery and root found 100M in a Directory '.user\.Trash ' 

Assuming Trash means just that is there any way to remove the directory or it's contents - which includes sub directories. rm -d {directory} doesn't seem to work. man rm kind of indicates that is the case however not my experience in attempting it.

John

---

### Post by johnbl on 2006-09-13
> **mssever said:**
> I just remembered something else. If you've enabled disk quotas, you could be running up against that.

I haven't seen any other threads about 100% disk full errors--although I haven't looked for them, either. But I'm positive that this isn't a common problem. "Those with real skill" don't have enough information at this point to be able to solve it, IMO. Given that this is an uncommon problem, merely stating that the disk is 100% full doesn't give any clues as to what the problem is. Either something is messed up regarding quotas, or something is writing a huge amount of data to disk--that much is plain. But without knowing where the bottleneck is, it's impossible to give more details. That's why I asked the troubleshooting questions above.

And, by the way, if this were a Microsoft problem, they'd still sell as many copies of Windows as before, because they have a near monopoly. Also, remember that this is a tech support forum, which means that people post when they run into problems. This forum is a poor measurement of those who have a trouble-free experience with Ubuntu.
ON the 100% full.. I as maybe others who have a problem and there are others, did zip as to setting up anything other than as it came. AS others have commented, disk filled without, apparently anything being done on the part of the user to the point where ' normal ' log on simply isn't possible.

Once found the recovery boot works fine, login as root ditto.
But following the assits on line doesn't seem to make any difference to the ' normal 'GUI log on loop condition.
I might be learning some about Linux but not in a time frame of my choosing and if push comes to shove, Linux will have to go and that I do not want at all. Ubuntu is simply too good! But, I can't go to the wall for an OS and starve for my beliefs, that's for painters in Garrets, so proprietory!<VBG>

As to only the screwed show up asking for assistance, your right but only in part. In my case this is my third attempt to get into a production environment with Ubuntu and about the fifth with Linux in general. In all other cases I simply pulled the pin on it,time being valuable & always assuming it was me anyway reloaded Windows to the subject system. But I ' count ' once!

There is a problem. No OS should simply fill a hard disk to an apparently non usable situation by sacrificing the critical login area to whatever! However, if that is the case a tool set capable of being run from say recovery as root that can reset to some default position possible conflics, delete the apparently many possible causes in coredumps,tmp files, iso images et al either directly or following a prompt. This might be a worthwhile tool to be available! 

John

---

### Post by mssever on 2006-09-16
Sorry for the delay in answering. I've been really busy lately and haven't had much time for the forums.
> **johnbl said:**
> COREDUMPS?
core returns a long list of every thing with core in the name.
What extension would a coredump be identified by?
Possibly core. I don't remember, though, as it's been quite a while since I've seen a core dump. I've never seen one in Ubuntu. ```
locate core | less
``` will find any core file, but as far a I know, you'll have to look through the list manually.
> In perusing via recovery and root found 100M in a Directory '.user\.Trash ' 

Assuming Trash means just that is there any way to remove the directory or it's contents - which includes sub directories. rm -d {directory} doesn't seem to work. man rm kind of indicates that is the case however not my experience in attempting it. I assume you mean **~**user**/**.Trash instead of .user\.Trash?

Note that man rm says that the -d option only works if your system supports it. I've never seen a Linux system that does. What you want is the recorsive option: ```
rm -r directory
``` Or, you might prefer to not delete the trash folder itself; only its contents: ```
rm -r ~/.Trash/*
``` 
I don't know much disk space that you've allotted to Linux (if everything were working right, that is), but is that 100M trash folder enough to account for our disk full errors? Certainly deleting its contents ought to enable you to log in, but unless you're trying to cram Ubuntu onto a really small partition, there has to be something else eating disk space. Keep hunting...
> **johnbl said:**
> There is a problem. No OS should simply fill a hard disk to an apparently non usable situation by sacrificing the critical login area to whatever!
True. However, there really isn't a "critical login area." GDM just needs some available disk space. So the real problem is disk space being eaten. No OS should eat disk space without good reason. And I suspect that there *is* some good explanation for what's going on. I just don't know what that explanation is.
> However, if that is the case a tool set capable of being run from say recovery as root that can reset to some default position possible conflics, delete the apparently many possible causes in coredumps,tmp files, iso images et al either directly or following a prompt. This might be a worthwhile tool to be available!  Yes, that has been discussed before. Now, we need someone to write it...

---

### Post by johnbl on 2006-09-18
Starting to get the picture on command line and thanks.
Managed to solve the problem and it was being eaten, and how!
Backups were the source of the problem and the default settings therein I think.
I posted my final resolve here in step by step format;

[http://ubuntuforums.org/showthread.php?t=257597](http://ubuntuforums.org/showthread.php?t=257597)

Basically starting in recovery, running as root, starting the GUI and then deleting oldest full backs and clearing out the trash.

System has 70G HD wholly given up to Ubuntu on install - the dual boot thing was SUCH a pain it was ' choose one 'situation! 

WINE, when kind of mastered takes care of the majority of my legacy windows must haves on the road. Not sure if I'm game to switch the main production platform yet but tempted to get a new box to sit in as a front end whilst being able to switch back wholly if any gotchas come out of the wood work as happened with this logon loop.
 
Will keep at it, might even get to a point where I can constructively contribute! <g>

Thanks again

John

---


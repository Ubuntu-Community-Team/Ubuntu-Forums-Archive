---
title: "Wallpaper changer"
date: 2017-01-31
forum: Desktop Environments
---

### Post by heatopher2 on 2017-01-31
Hi Everyone. I'm still fairly new to all this. Help me out please. Sorry, not sure which board to put this on, so just dropping it here.

To cut a long story short, I've been trying two different wallpaper changers, "wallch" and "variety" on my desktop and netbook, both of which I've recently migrated over to Ubuntu. I really want them to work, as both have some nice features, but they also both seem to have problems. Neither is working at all at the moment, which is making me a bit sad :sad: I know it's not the end of the world, but I really do appreciate a bit of desktop art.

Is it a problem that I've had both of them installed at the same time? I don't have them both starting at boot, by the way. The weird thing is that wallch was working more or less fine on the desktop until I thought to try variety on there. Now they both seem to have been knocked out! Slightly strange. Neither of them has been working very reliably on the netbook. Variety was OK for a bit, but seems to have given up the last two days.

Or is it  irrelevant that they're installed side by side, and is it just that they're both not being properly maintained any more?

If so, any alternatives? Thanks very much!

---

### Post by wildmanne39 on 2017-01-31
*Thread moved to **Desktop Environments for better support**.*

---

### Post by TheFu on 2017-01-31
I use **feh**. No GUI. Probably not what you want.  
Saw a LAS episode where they recommended something - sorry, don't remember which episode or which tool. OMGUbuntu covered it, I think.

Anyway, here's the script I have in my crontab. Runs every 30 min:
```
#!/usr/bin/env perl

my @files=`ls -1 ~/Pictures/Best/*g`;

# pick a random file
my $bg = $files[rand @files];

`env DISPLAY=:0 /usr/bin/feh  --bg-scale $bg` ;
```

---

### Post by heatopher2 on 2017-01-31
Well, if all else fails I can certainly use that! It's good for learning a bit of code anyway, eh. And I've also learned about a podcast to watch. So thanks all in all :~}

I just remembered after I posted this that I actually backed up my desktop this morning, so I've gone back to that, and won't be fiddling around with the wallpapers on here for a while!

By the way, it wasn't just that neither of those two programs were working. I also couldn't change to one of the wallpapers already supplied in Ubuntu. So I suppose it's in the system somewhere!

---

### Post by TheFu on 2017-02-01
Backups rock. Automatic, versioned, backups rock the hardest (best).  Plus if you do them daily, they are usually just 1-4 minutes from start to finish. For example, backups from last night for a few systems here:
```
=== Time for Backups to spam2 === 
StartTime 1485933064.00 (Wed Feb  1 02:11:04 2017)
EndTime 1485933072.58 (Wed Feb  1 02:11:12 2017)
ElapsedTime 8.58 (8.58 seconds)
TotalDestinationSizeChange 360 (360 bytes)


=== Time for Backups to lubuntu === 
StartTime 1485929708.00 (Wed Feb  1 01:15:08 2017)
EndTime 1485930008.40 (Wed Feb  1 01:20:08 2017)
ElapsedTime 300.40 (5 minutes)
TotalDestinationSizeChange 10448678 (9.96 MB)


=== Time for Backups to hadar === 
StartTime 1485930914.00 (Wed Feb  1 01:35:14 2017)
EndTime 1485930921.70 (Wed Feb  1 01:35:21 2017)
ElapsedTime 7.70 (7.70 seconds)
TotalDestinationSizeChange -4369 (-4.27 KB)

```

On X/Windows, the wallpaper is set using **xsetroot** - check out the manpage. The desktop "background" is known as the "root window." X/Windows only works with pixmaps (a type of bitmap graphics file), so any tool will convert to that on the fly.

Glad you like my perl.  I wanted to use bash, but my knowledge of how to get a random filename from a list wasn't sufficient. I knew exactly how to do it in perl, which is why perl is used here.  Because this is run from a crontab, which is a terrible idea for any GUI tool, I can't say how bad this is (plus it generally doesn't work at all), I had to set the DISPLAY value to work with the correct X-display. IT won't work over remote X-sessions.

BTW, the use of `ls` to fill the file array is bad form.  File globbing is an issue - it is a hassle to do it the correct way that actually works.  In theory, using something like @array = < "~/path/to/files/*g">; should work. In theory.  In practice, using the File::KGob module is necessary.  That's a bunch of extra code to pull in for something so small.

---

### Post by heatopher2 on 2017-02-01
Ah, OK, it's Perl. I was wondering, but now I see it at the top, ha ha ha!

Does this only pick up the files in that particular directory, or also files in sub-directories? Just because I've got different folders for different types of art (fine art, nerd/fractal art, caveman art, historical art, bla bla bla), but all under one directory.

Yes, I've set my backups up now, all automated. That was the last thing that I wanted to get sorted out before I could confirm my graduation from beginner to apprentice :) I've got a monthly tar file, plus a daily rsync of important folders, and then a weekly rsync of the latest daily one. I think that's enough, eh! (although I'm still not sure, despite reading quite a lot, about which directories I should be backing up - home? etc? usr? var? - it's all still Greek to me really!). Also using Clonezilla for occasional snapshots, and that was in fact what I used to restore just now.

---

### Post by TheFu on 2017-02-01
I only use rdiff-backup. No need to clone (wasteful), rsync is great for a mirror, but not much more. Definitely not sufficient for versioned backups.

What needs to be backed up depends on the system and what it is running.  All my systems have slightly different backups, but the general steps are:
[LIST=1]
[*]Setup paths to the correct programs
[*]Set the directories to be backed up into an array
[*]Run daily data cleanup tasks - cache files, flash objects, etc.
[*]Run data capture tasks - lshw, parted, lsblk, lvs, vgs, blkid, any RAID configs, ruby gems, perl cpan modules, crontabs, 
[*]Ensure all target locations for storage exist and are mounted
[*]Create a list of file patterns to be excluded (videos, audio, HUGE files, , browser caches, etc)
[*]Make a list of all the currently installed packages on the system.
[*]Stop any running daemons like blogs, DBMS, tv-recordings, etc. to ensure a clean backup. (this may not be desirable on certain systems)
[*]Run the backups
[*]Restart any daemons that were stopped, startup order should reverse the shutdown order
[*]Run the old-backup removal task(s), if any.  I keep 60, 90, 120 days of backups, depending on the attack vector risks.
[*]Create a report of the backup (size, clock time, change data) and email it.
[/LIST]

Having all that system data, captured daily really is helpful.  If an external disk disappears, but nobody has looked for it in awhile, it would be good to know when that happened so that correct log files can be reviewed, for example.  When trying to rebuild a system from backups after a HDD fails, it is handy to KNOW the storage layout. Non-disk failures usually aren't that hard - just reconnect the old disks to the new system.

If you can't have downtime, then you'll need to use LVM and lvm snapshots before the backup is taken, mount that snapshot, and backup off it, not the normal storage areas. No need to stop any running processes doing it that way. When done, umount the snapshot area(s) and remove the snapshot. A snapshot for an hour shouldn't be much storage - usually less than 1%. 

Anyway - hope this helps.

tar is fine for 50MB of data, but not much more. There are just more efficient solutions.  Remember that tar was created when we did tape backups (sequential).

---

### Post by heatopher2 on 2017-02-01
Oh, wow, that's a ve-e-e-ery detailed list! Thanks again :~)

I'm  *afraid* that some (approximately half!) of that is beyond me yet -  remember I'm still very much an apprentice - but I shall definitely  refer back to this list whenever I'm coming back to this stuff. For the  time being I'm just quite proud of myself that I've finally got round to  running Linux, and have some kind of backup going on (nothing like as  clever as what you wrote), after several failed attempts in the past.  And now I need a couple of days away from all this. I'm getting square  eyes! All the best just now :~)

---

### Post by TheFu on 2017-02-02
I didn't come up with that when I was new.  Took about 10 yrs to get there after trying to reduce the total time and size of backups to a level that made sense to me. Failures is what got me there. Lots of failures. ;)

---

### Post by heatopher2 on 2017-02-02
OK, there's no point resting on the laurels for too long (I don't feel  like I've got ten years to learn all this stuff!), and I'm more awake  than I was when I read that last night. Let's get on with this.....

Looking at your list, one at a time:

#1 Do you mean the path to the backup script in crontab? I don't really understand other than that.

#2 Yes, I've done this (I think). This is what it looks like in my  script (are these directories the right ones - honestly, I've read a  bit, but I really don't know yet what I need to be doing):

```
declare -a directories=("bin"
            "etc"
            "home"
            "lib"
            "lib32"
            "lib64"
            "opt"
            "sbin"
            "usr"
                       )
```

#3 Are these instructions useful? [http://www.ubuntugeek.com/cleaning-up-a-ubuntu-gnulinux-system-updated-with-ubuntu-14-10-and-more-tools-added.html](http://www.ubuntugeek.com/cleaning-up-a-ubuntu-gnulinux-system-updated-with-ubuntu-14-10-and-more-tools-added.html)

#4 Well, there are only two and a half things there that are familiar!  Crontabs, OK. blkid - yes, I've done that. I think I know what RAID is -  that's when you have two hard drives mirroring each other, isn't it? I  don't have that. Everything else in #4 is NEW !!!!

#5 Check. I've made sure that all the drives are mounted at startup.

#6 Yes, I've got the exclude thing clear. Anyway, I've never kept large  video or audio files on the system partition in Windows, so doing the  same thing here of course.

#7 OK, this is important. Do I use "apt list --installed" ?

#8,9,10 What daemons would a new boy like me have running? I don't  *think* I have anything like that set up yet. I suppose I might try to  set up mysql at some point, as I have used that in the past, but I'm not  using it right now.

#11 Yes, delete old backups, no problem. I know how to do that. Not sure  that there are any high vector risks (ooof, more new vocabulary for  me!)

#12 Yes, no worries, I can do that.

---

### Post by TheFu on 2017-02-02
Scripting best practices: [http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting) - applies to sh/ksh/bash and all the other languages commonly used. Here's a bash script following those best practices: [http://blog.jdpfu.com/files/kernel-cleanup.sh](http://blog.jdpfu.com/files/kernel-cleanup.sh)  That specific script isn't needed anymore - Ubuntu finally decided to manage the number of kernels left behind for us.

There are usually 50 ways to solve any problem. Perl is my tool of choice whenever a script gets over 1 pg in length, so my backup scripting is all perl. We are off the wallpaper topic. Best to open a new thread about backups, if you care, so other people will chime in.

---

### Post by heatopher2 on 2017-02-02
Oh, and by the way, back to the original wallpaper problem, it looks like I've hopefully fixed it :D

Towards the bottom of this thread:

[http://askubuntu.com/questions/527366/wallpaper-is-not-changing-and-right-click-does-not-work-on-desktop-in-ubuntu-14](http://askubuntu.com/questions/527366/wallpaper-is-not-changing-and-right-click-does-not-work-on-desktop-in-ubuntu-14)

This line seems to have sorted it:

```
gsettings set org.gnome.settings-daemon.plugins.background active true
```

Command line or dconf editor, seems OK. Well, the evidence is that I've got the variety app working (touch wood) on both desktop and netbook, so it looks alright :~}

---


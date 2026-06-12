---
title: "Help - computer appears to be bricked!"
date: 2009-02-01
forum: General Help
---

### Post by kiwi8mail on 2009-02-01
Regrettably, I think I've bricked my computer!

I followed the instructions in the following webpage (after first creating a new partition using the live CD) in order to move my home directory to a separate partition:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

I got as far as the command "$sudo mount /dev/hda5 /home"

As suggested by the text at that point, I then did a check that things were okay.   They didn't seem to be - nothing could be viewed or accessed.   

What went wrong, I don't know...

Restarting the computer, and trying to log in results in a message: "Your home directory is listed as: '/home/andrew' but it does not appear to exist.   Do you want to log in with with the /(root) as your home directory?   It is unlikley anything will work unless you use a failsafe session."

I tried logging in both using an ordinary session, and a Failsafe Gnome session, but in both cases, after a few error messages, I get just the blank standard Ibex wallpaper and nothing else.

If necessary, I will work out how to use the recovery partition (its a new Dell pre-installed Ubuntu laptop), but I would prefer something less drastic - as I had spent an evening upgrading to 8.10.   Are there a few magic commands I can type in after logging in as a Failsafe Terminal session?

Thanks for any assistance!

Andrew

---

### Post by The Cog on 2009-02-01
I wonder where your home folders are. Can you boot into recovery mode and have a look round, try to find them? Try to answer these questions:

Does /home exist? If so, does it contain any subdirectories?

Does /mnt/old_home exist? If so, does it contain your files?

If old_home still contains your files, then this should recover them:
delete /home if it exists: **rmdir /home**
move old_home back: mv /old_home /home

I wonder if the layout of that article mislead you. This part:
> $cd /home/
$find . -depth -print0 | cpio –null –sparse -pvd
/mnt/newhome/
should be just two commands, not three. Their layout has broken it into three lines (at least, it has on my PC). Kind of irresponsible if them. I feel.

If you need a GUI in recovery mode, the command startx might get one for you. I haven't tried it myself, but it might work.

---

### Post by argedion on 2009-02-01
i would try the live cd and see if i could find my home folder once located i would then burn everything to cd for safe keeping and try out cogs suggestion.

---

### Post by kiwi8mail on 2009-02-01
Thanks for that Cog - worked like a charm!   All fixed now.   Think I will stick to a single partition!

---

### Post by KeyserSoze93 on 2009-02-01
It may well be that the process went fine.

You know "mount X Y" only lasts till you reboot, so while it may show up fine, if you want to make that persistent, you'll have to add a line to /etc/fstab (as it says in that guide).

Could you post the contents of /etc/fstab? So we can be clear if the right lines went it.

When you say it went find till you mounted it, and then you rebooted after checking everything was there, does that mean you didn't go to the next step which involves adding the line to fstab?

---

### Post by The Cog on 2009-02-02
Im glad you got your data back. But a separate /home is a good idea. Bear it in mond when you next upgrade - maybe take the opportunity to do a good backup of all your data and do a complete install with separate home before restoring your data.

Actually, I have two / partitions, one for my real OS and one for testing the next release. Whichever one is my favoured / gets the provoledge of using my large /home partition. The testing one has to keep /home on its / partition.

---


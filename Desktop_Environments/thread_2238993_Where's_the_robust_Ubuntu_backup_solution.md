---
title: "Where's the robust Ubuntu backup solution?"
date: 2014-08-11
forum: Desktop Environments
---

### Post by jimerman on 2014-08-11
Dear Ubuntu community, admittedly my favorite OS is OS X, and I am really loathing Windows after working on it for 25 years.  I really like Ubuntu distro, but I am struggling with what I consider to be one of the most important aspects of an OS - the built-in backup solution.  With Windows, good luck if you want a single, integrated solution for various types of backups.

Let me explain what I mean for that.  There are 2 main reasons you would back up: 1) to save yourself from yourself (I botched this file, I need it back to the way it was on X), and 2) to save yourself from the computer (hard drive dumped, the cat burgler got it, etc.).  Therefore, a robust strategy should take into account how do you restore a single file or set of files, to how do you restore the entire OS.

In Windows case, there is no real anser to the first.  The second, truly the only way to accomplish is a system image - expensive because you back up the OS (unnecessary) and all the apps and their settings.  What happens if you restore to different hardware?  Plug and pray, baby, plug and pray.

With OS X, it's a well-orchestrated symphony.  Time Machine is a single click setup - and it backs up all changed files every hour for 24 hours, then every day for a week, then every week.  All your personal (/home) settings are backed up, as well as applications and system settings.  Thus, a total restore scenario looks like this:  Format hard drive, install the OS, and pick "Restore from backup."  Wait as long as it takes to restore the files and settings and apps you put on the computer.  Voila.  Complete, robust.  If you want single file or folder restore, you slide back in time to the point you want and click Restore.

So, in looking at Ubuntu, I see Deja Dup, and this gives me weekly backups?  Really, I can make it daily, but say I pooch a file at 3PM, so I lose the entire day's work?  Also, what does it back up exactly, so what does the full restoration scenario look like?  Does it back up the system (user accounts, apps installed, etc.)?  Does it back up system files I may have changed (crontab, /etc/hosts, etc.)?  It looks like it *only* backs up the /home folder, and nothing else unless I specify.  So no one-click get everything, make sure my system is protected like Apple? 

Or, is there some other utility that provides a complete approach?

Thanks for replying, I truly appreciate Ubuntu as the best Linux distro.

---

### Post by grahammechanical on 2014-08-11
Some people install a Linux distribution and it seems as if they were expecting an exceedingly cheap Windows clone. What are you expecting? An exceedingly cheap OS X clone?

Perhaps you should stick to OS X. That seems to meet your needs. With Linux we get what someone else has spent a lot of time and effort on. It was their choice on how to spend their time, skills and energy. Many do it unpaid. If we see in Linux a need for a certain kind of software then we have 2 options. Personally invite developers to write that software and give them whatever support we can give. Or, write the code ourselves. We have this freedom.

There is a third option; accept the realities of life and make the best of it we can.

The complete approach?

[https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs)

It is aimed at servers more than the desktop. It lacks a GUI management snapshot utility . It all has to be done through the command line. If we install Ubuntu using btrfs as the file system instead of ex4 then install apt-btrfs-snapshot then every time we update the system a snapshot will be created. We can use the command line to revert to an earlier snapshot and the recovery mode menu will give us an apt-snapshots option which will allow us to revert to an earlier snapshot from there. I know of at least one forum user who has be able to revert a distribution upgrade back to the previous version using the btrfs snapshot feature.

It is possible to modify the recovery menu apt-snapshot script to be a bit more useful and to run it from a terminal. I have done this.

Regards.

---

### Post by amanchesterman on 2014-08-11
There are several backup apps in the Software Center: have you tried them all?

Personally I use ukopp, which I find simple and effective: I can choose exactly what to back up and when, and if I want to access or restore a single file from the backup copy I can. Sure I have to remember to click a button on screen to start the backup, but personally I don't find that a great hardship; it's just part of my work routine. I've set it to backup only the files that have changed, so it's very fast.

I agree with grahammechanical, though: if the functionality you need/want only exists on OS X, then use that.

---

### Post by ian-weisser on 2014-08-11
> **jimerman said:**
>  Time Machine is a single click setup - and it backs up all changed files every hour for 24 hours, then every day for a week, then every week.  All your personal (/home) settings are backed up, as well as applications and system settings.

I use OSX a lot also, and it's not special - just different, pretty, and expensive.

You will discover that most Ubuntu backup solutions, though they lack the pretty graphics and require a few more clicks, are even more customizable and flexible...once you know where to look.

Ubuntu has *many* robust backup applications. But, like Legos, you must assemble the pieces yourself.
The best backup solution will depend on you and your needs. A myriad are available.
For  example, I use rdiff-backup, a simple, scriptable, cron-able, ssh-able  command line application. When it runs in the background, I don't even  notice it. I love it. You may hate it.

---

### Post by philhughes on 2014-08-12
Unfortunately this kind of very easy to use, graphical, single backup solution is one area in which Ubuntu falls behind the competition, and particularly Time Machine. I have never used it, but it seems to be pretty well acknowledged as the leader. The Windows 8 built-in backup tool, is also poor, but at least it now has a built-in "restore to new" tool.

As others have said, Linux has many powerful tools available, but they will generally require a lot more work to understand and configure. There are some graphical tools which generally are interfaces to the command line tools, but I don't think there is any one solution as powerful as Time Machine (though there have been some attempts to replicate this).

Deja Dup is one of these tools, but I found it lacking in configurability, and more important not reliable - it would not find backups it had done, which I could see were there.

You might like to look at Back In Time ([http://backintime.le-web.org](http://backintime.le-web.org)) which was inspired by Time Machine and uses rsync under the hood. It does file versioning. It is in the Software Centre - if you are using stock Ubuntu, install the Gnome version (backintime-gnome). In my testing, I found it reliable.

---


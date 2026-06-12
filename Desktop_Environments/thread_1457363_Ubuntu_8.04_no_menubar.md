---
title: "Ubuntu 8.04 no menubar"
date: 2010-04-18
forum: Desktop Environments
---

### Post by henryf61 on 2010-04-18
Actually I have many errors. They started when Thunderbird said I had 1 email but there was no space to write it to disk. I checked and my disk had zero free space. I deleted 30 MB of old messages and many nautilus daily backup files from last year and early this year. Still no free space!!!

Then I rebooted and got this error message:

The application "gnome-panel" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you may have selected may not take effect or may not be restored next time you use the application.

This is my personal laptop and no one else is my sysadmin. I tried rebooting several times and with a previous kernel but this error persists.

There is an option to see details. The drop-down window is only 4 lines high and two inches wide. It begins thus:

No database is available to save your configuration. Unable to store a value at key '/apps/panel/toplevels/toplevel_screen0/diable_movement/' as the configuration sever has no writable databases. 

The details continue on at great length and are even more incomprehensible to me.

Sorry for the length of this message but I don't see how to make it much shorter. Right now without a menubar, my system is pretty useless.

TIA for any help.

Henry

---

### Post by quixote on 2010-04-19
When you deleted the messages etc., did you just hit "Delete" or did you bypass Trash?  If not, and they're in the Trash, you haven't actually gained any space.

The problem is that without a lot of space, the graphical user interface doesn't run right, or at all.  It's recommended (but not clearly enough!) not to let your disks (ie partitions) get fuller than about 95%.

The way to deal with this is from the recovery console because that avoids loading the GUI.  Boot your system, but choose "recovery mode" instead of the usual one.  If you have an ethernet cable, plug that in, and when it gives the six or so booting options, choose "root console with network access".  (If no ethernet, don't worry about it.  It'll just give you an error message but boot normally.)

The prompt will look like this: #
You will be in **root's** home, not your own.  To delete your own Trash from the command line type ```
rm -rf /home/your-login-name/.local/share/Trash
```
DO NOT MAKE ANY TYPOS. Especially do not put any spaces in the path.  For instance, "rm -rf /home /your-login-name/etc would delete all the home directories on your machine.  The "rm -rf" command, running as root, will allow you to delete your entire hard disk, or any part of it, without a single "are you sure?" question.

Another huge space hog is nautilus' thumbnails.  They can safely be deleted too, and will be rebuilt as you need them. ```
rm -rf /home/your-login-name/.thumbnails/
```

When you're done deleting things, type```
reboot
```to restart the boot process.

If a full Trash was the problem, this should at least give you enough space to boot normally again and to go on with the deleting process in an easier environment.

---

### Post by henryf61 on 2010-04-19
To quixote,

Thanks for your detailed instructions which I followed carefully but no success.:(

You are correct about my Linux partition being full. In my previous effort I had deleted a few hundred bytes but that was not enough for gnome to work. I ran gparted from a CD and discovered (to my surprise) thet my linux partition is only 4 GiB. THere is over 30 GIb of unallocated disk space below it (and a Windows partition at the very beginning.) When get up enough nerve, I will try expanding my linux partition and hopefully that will cure the problem.

Meanwhile, I have a few other options which I will explore.

Thanks very much for taking the trouble to reply and to give such well-written instructions.

Regards,
henry

---

### Post by quixote on 2010-04-19
It's bit odd that deleting those files didn't help at all, unless they weren't part of the problem to begin with.  Still, if you have 30GB, don't worry about it.  That's actually your best option I would think.  Tinkering with the system is a much more fraught process than enlarging a partition.

One thing: is the free space before your linux partition?  I.e. to the left of it in gparted's diagram?  If so, I know that gparted used to have trouble dealing with that.  I don't know if it still does.

If it does still have trouble, you need to 1)make a new partition as far to the left as it goes in the free space, and make it least as big as your current one.  2)Copy your linux partition to the new one. 3) Delete the old linux partition. 4)add the freed space to your new linux partition.  It's best to apply each change as you do it instead of stacking them up and then applying all at once.  Gparted seems happier that way.

You may find you need to rebuild the bootloader (ie grub) after the process since the names of the partitions will have changed.  That sounds intimidating, but it's really quite easy.  We'll deal with that if it turns out to be a problem.

---

### Post by henryf61 on 2010-04-20
I am extremely nervous about moving/copying my Linux partition in case the whole partition gets wiped out. All the files are still readable; I just can't run any programs.So I want to try every other alternative before gparted.

1st try. Delete more files about 90 MB. Then repeat your instructions to reboot in recovery mode and delete Trash. Free space is still zero!! I suspect that the error message on my first email indicated damage to some system database that somehow needs to be re-created and that lack of space is not the only problem. 

2nd try. Setup Ubuntu on an old desktop and restore thunderbird profile from as external backup which I made just before the crash. This worked! :) I downloaded 33 messages that were waiting while Linux was down. All my message folders seem to be restored. 

Thunderbird email was the most important thing I had on Linux. I use Xmarks to synchronize my Firefox bookmarks across machines. I still have a lot of important files on Linux but they too were all backed up externally and it will take a little while to restore them to my desktop. When that system is back up to the same level as my damaged Linux, then I will try your strategy of moving or copying Linux to a new partition. By then I will have a complete working copy.

Thanks again for the detailed instructions. I will let you know how moving Linux to a new location goes.

Regards,
Henry

---

### Post by quixote on 2010-04-21
My first point was going to be "back up your important files", but you beat me to it :D.

There's something strange going on that you delete and don't get free space. There's a possibility that somehow root's Trash is what may be plugging up the system.  To delete that at the recovery console use: "rm -rf /root/.local/share/Trash".  Also, make sure that's where your Trash really is on Hardy: ```
#ls -al /root/.local/share
ls -al /home/your-login-name/.local/share/
```and see if there's "Trash" there.  It used to be somewhere else entirely, but I think by the time Hardy came around, that was the location  (same as it is now on Karmic).

You're going to need to find about 200MB worth of files to delete, would be my guess.  That gets you to about 95% full on a 4GB system.  

Another thing I remember is having Big Issues with the gnome virtual file system on Hardy filling up my system.  If this problem happened suddenly, after a backup, maybe that bug has bit you too.  There's a fix for that too, but it's a bit different.

You don't need to boot into recovery console.  You could also boot from a LiveCD, find the full 4GB partition in /media, and then work with it from there in nautilus or the command line.  The path would /media/disk-designation/home/your-login-etc or /media/disk-designation/root/etc.  If the disk designation is an interminable string of numbers, just type the first couple and hit Tab to auto-complete.

---


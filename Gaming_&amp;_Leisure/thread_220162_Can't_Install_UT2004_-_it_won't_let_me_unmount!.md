---
title: "Can't Install UT2004 - it won't let me unmount!"
date: 2006-07-21
forum: Gaming &amp; Leisure
---

### Post by Brighid on 2006-07-21
Hi everyone,

I'm sorry to bring this up .. because I know it's a common topic, but I can't install Unreal Tournament 2004!

I copied linux-installer.sh from the first CD to my home folder, as I found was recommended.  I even tried "export SETUP_CDROM=/media/cdrom0" as I saw suggested somewhere, but that didn't seem to help (to be honest, I don't even know what it did, if anything).  I started the installer with sudo, and it went fine, until I had to unmount the CD to insert the second disc.

In a second terminal window, again as told, I entered "umount /media/cdrom0", and I was told that the device was busy.

I tried using "fuser" to determine what processes were using it (I entered "fuser /media/cdrom0").  I noted the process ID's and sent "SIGKILL" to them with KDE System Guard - and to my surprise, the terminal with the installer closed!

I don't know what I'm doing wrong.  I had read somewhere that disabling supermount could help, but typing "supermount -i disable" just tells me it's an unknown command.  Maybe I don't even have supermount, though I wouldn't know.

So .. what am I doing wrong?  I really can't understand why it won't unmount the CD .. does anyone have any ideas?

Thanks in advance ..

**Edit**: Well, after searching some more (I'm too persistent sometimes!), I seem to have found the solution.  I had thought I was logged in as root (had typed "sudo su") when I entered the umount commands, but I may have been mistaken.  After a simple "sudo umount /media/cdrom0", I was able to eject the disc, insert the next one, and mount it.

I'd delete this thread, but I know how helpful I've sometimes found obsolete thread to be, so I'll just leave it, in case it ends up helping someone else.

---


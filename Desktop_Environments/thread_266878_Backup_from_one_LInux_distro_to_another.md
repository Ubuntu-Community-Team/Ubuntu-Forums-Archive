---
title: "Backup from one LInux distro to another"
date: 2006-09-27
forum: Desktop Environments
---

### Post by sandpvrr on 2006-09-27
Hello All,
      I'm a very very green ubuntu user, but I've been using SimplyMEPIS for two or three years now. What I'm trying to do is backup my digital photos from my Mepis machine to another machine which I have running ubuntu. I have the simple backup configured, but this won't do files, or I can't figure out how to make it do files.
      First the basics:
      Both machines have SAMBA running, and running successfully - I can mount shares from both directions - Mepis to ubuntu, and ubuntu to Mepis. I have keep installed on the Mepis box (it runs the KDE desktop) but when I try to have it backup to the prescribed directory, it gives me an error. Something about that directory not being an rdiff folder and that I should try the backup with a -force option. Tried to run rdiff in a command shell, not found. What is rdiff anyway? 
      I have changed the chmod permissions on the samba config (smb.conf) file to be 777 so as to be read and write and execute for all users, which should allow me to save files across the network, but the backup program does not seem to allow this.
      I am looking for a solution - either to push the backup from my Mepis box to the ubuntu or for the ubunto to pull the backup from my Mepis box. Suggestions for either one would be welcomed!
       Thanks!
       cya, Joey

---

### Post by kidders on 2006-09-27
Hi there,

If it were me, I'd keep things simple and just use cron. You could have something like **export TMPNAME="/tmp/`date +%F`.tar.gz"; tar -czf $TMPNAME /home/photos && scp $TMPNAME server:/home/username/backups && rm -f $TMPNAME**. I'd set myself up with a public/private keypair and set the cron job to run as me every evening, say.

That way, you wouldn't have to bother with samba or any annoying backup apps.

---

### Post by sandpvrr on 2006-09-28
Hello Again,
      Well - I must admit that would work - but what I'm really looking for is a no compression file copy or synchronization that I can schedule, not necessarily a command line solution, as I'm sort of a graphical person :-)
      Any other suggestions?
      Thanks!
      cya, Joey

---

### Post by lamego on 2006-09-28
Once you have the samba mounts done you could use fullsync:
[http://fullsync.sourceforge.net/index.php](http://fullsync.sourceforge.net/index.php)

---

### Post by kidders on 2006-09-28
Did you *really* mean to use the word "sync"? ... that makes things much more complicated. Some kind of filesync app is your best bet, I'd say, like lamego suggested.

I can't help wondering why you're using a Microsoft filesharing protocol to share files between two Linuxes though ... don't all the silly file naming and permissions management restrictions irritate you? (That was the motivation for the SCP part of my suggestion.)

---

### Post by sandpvrr on 2006-09-28
Hello All,
      I'll try the fullsync when I get home. Yes I do mean 'sync' the issue would be that occasionally I do delete or move a photo, and I want that to be reflected on the backup.
      Although using the Windows shares to do this is a bit complicated, I like the power since I do have a pair of Windows XP machines as well (gasp!) and backup to those as well. In case you're wondering - my Laptop is used primarily for two things, gaming and wireless web surfing. Neither of which is done particularly well in ubuntu, the Wlan card (interal) will simply not function.
      Thanks - and I'll let you know what happens!
      cya, Joey

---

### Post by sandpvrr on 2006-09-29
Hello All,
      Well, I tried to get Fullsync, but I must be missing smoething since it doesn't seem to want to run on mysystem, and I'm alsmost certain I've got Java installed. No matter.
      It wasn't the solution I'd figured on, but it works:
      2 Bright Sparks makes a software package called SyncBack - its free - and for Windows. I've used it for years. I soft of assumed that one or the other of the Linux distros would have a built in backup utility that would work as well or better - but it would seem not. 
      I hadn't tried it until tonight, but it runs fine under Wine and has already synced my pictures. Looks like that is my solution!
       Thanks for all the help...
       Great distro BTW - works great - no issues with hardware detection at all!
       cya, Joey

---


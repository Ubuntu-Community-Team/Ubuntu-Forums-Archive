---
title: "backup"
date: 2005-12-09
forum: Desktop Environments
---

### Post by davebradford on 2005-12-09
does anybody know of a linux application that will backup files/folder to another location on say a weekly bases? that runs without a GUI? any ideas on this and i shall be very chuffed!!

Dave

---

### Post by frodon on 2005-12-09
A bash script run with crontab should do what you want if you just wish to copy some file in another folder in a automatic way.

---

### Post by nocturn on 2005-12-09
[QUOTE=davebradford]does anybody know of a linux application that will backup files/folder to another location on say a weekly bases? that runs without a GUI? any ideas on this and i shall be very chuffed!!

Dave[/QUOTE]


Bacula will do this, but it is a complex (but powerfull) backup system.

---

### Post by davebradford on 2005-12-09
how do u use crontabs?

---

### Post by frodon on 2005-12-09
Here is a good article about what is crontab and how to use it : [http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)

Don't hesitate to ask for help for writing your script and setting your crontab job.

---

### Post by rudiz on 2005-12-09
try "simple backup" :sbackup.


[http://packages.debian.org/unstable/admin/sbackup](http://packages.debian.org/unstable/admin/sbackup)

---

### Post by luxir on 2005-12-19
[QUOTE=davebradford]does anybody know of a linux application that will backup files/folder to another location on say a weekly bases? that runs without a GUI? any ideas on this and i shall be very chuffed!!

Dave[/QUOTE]
 
I found <dar> to be a good choice for regular backups. It can save over the network, compress, encrypt and split the backup file so it fits on CD's. It comes with a very good HOWTO, so even a noob like me can make it run ;) 

Luc

---

### Post by kosmic on 2005-12-19
You also have Partimage :)

---

### Post by maglis on 2005-12-19
I was impressed by ***backuppc ***:

> high-performance, enterprise-grade system for backing up PCs
BackupPC is disk based and not tape based. This particularity allows
features not found in any other backup solution:
 * Clever pooling scheme minimizes disk storage and disk I/O.
   Identical files across multiple backups of the same or different PC are
   stored only once (using hard links), resulting in substantial savings
   in disk storage and disk writes.
 * Optional compression provides additional reductions in storage.
   CPU impact of compression is low since only new files (those not already
   in the pool) need to be compressed.
 * A powerful http/cgi user interface allows administrators to view log files,
   configuration, current status and allows users to initiate and cancel
   backups and browse and restore files from backups very quickly.
 * No client-side software is needed. On WinXX the smb protocol is used.
   On linux or unix clients, rsync or tar (over ssh/rsh/nfs) can be used
 * Flexible restore options. Single files can be downloaded from any backup
   directly from the CGI interface. Zip or Tar archives for selected files
   or directories can also be downloaded from the CGI interface.
 * BackupPC supports mobile environments where laptops are only intermittently
   connected to the network and have dynamic IP addresses (DHCP).
 * Flexible configuration parameters allow multiple backups to be performed
   in parallel.
 * and more to discover in the manual...

---

### Post by skeezer65134 on 2005-12-20
I am also looking for a backup solution, although not for a system backup. I am planning to build a machine (well, I have the machine, I just need the drives) to act as my backup datacenter of sorts. I want to pack it full of 160gb drives (likely 4 or 5), make a RAID5 setup with them (likely software RAID, with 1 drive running as a hot backup). 

The computer will run debian, ubuntu, or gentoo (most likely something debian based though). I don't care at all about burning DVDs or CDs of the data as the RAID setup should be enough backup for what I need. Currently, I use a large drive on an external USB enclosure and do a backup whenever I think about it and have time. Needless to say, I want something more stable.

Some notes:

- The machine will have no X installed, servers don't need GUIs (otherwise I'd just run Windows :P)
- It will run an FTP server, SSH server, Samba server, possibly a webserver (for whatever intranet reason, nothing on the internet) for accessing files and controlling the machine
- Running a journalling file system to prevent failed writes (likely ReiserFS since it seems to be pretty solid on my machines)

This is all easy to do, I simply need to put the drives in the computer and install the software. No biggie.

My problem at the moment is I am planning to backup from various other computers in my house. Here's the breakdown in short.

My desktop running Linux currently houses:
- MP3s
- personal pictures and documents
- my software

My media pc running Windows currently houses:
- emulation (roms, emulators, etc)
- digital movies
- tv show recordings (since it's a DVR)

My laptop running Linux and Windows currently houses:
- additional personal info

It's also very possible (and likely) that more machines will be added to this mix with time.

What I want to do is synchronize, not simply backup, all of this information with the server. I'd also like to do this on a schedule, be it daily, weekly, or monthly (and this may be different for all the different types of data although that isn't a manditory requirement). This way, I have a redundant and fault tolerant center for all of media and it's accessible from all of my machines (via samba, ssh, ftp, etc).

My problem is, how can I achieve this? I can set up an rsync server on the datacenter and use it with the desktop and laptop, but what about the windows machine? I could do it over samba I guess and handle it all from the server end, but I just wanted to ask here if there is a better way to achieve what I need before I spend time learning and setting up rsync.

I need something that will sync mostly because of the MP3 collection. It is always growing and I regularly replace files that I find to be too low bitrate and blippy. This would also apply to the movie and TV show collection as well as my personal data like papers and such which will be constantly changing.

One advantage I see with rsync is that the less I change, the less it has to do. This means that even running daily or hourly backups would be relatively quick or the local intranet. It's likely the route I will go, but like I said, I thought I'd ask around. 

I hope this isn't too much of a repost, but I didn't really see anything posted that handled what I was looking for. Thanks for any and all advice.

---

### Post by maglis on 2005-12-20
[quote=skeezer65134]What I want to do is synchronize, not simply backup, all of this information with the server. I'd also like to do this on a schedule, be it daily, weekly, or monthly (and this may be different for all the different types of data although that isn't a manditory requirement). This way, I have a redundant and fault tolerant center for all of media and it's accessible from all of my machines (via samba, ssh, ftp, etc).
[/quote] 
If you want backup files that you can use to extract information from, in a 'catastrophic' event, then use ***backuppc***.

If you want a synchronization tool that you will use to keep two synchronized replicas of the same thing at two different computers, then use ***unison***.

---

### Post by linkunderscore on 2005-12-20
I am running a bash script with crontab and have been doing so for quite some time. This script backs up my .fvwm folder and its contents. 

However, the script that is running tars the .fvwm folder in such a way that it also includes /home/link/.fvwm/ 

For example:
When I go to untar the back up I have to navigate through /home/ then link/ then I get to .fvwm/. I just want the tar ball to inlude .fvwm/  The home/ folder only includes the link/ directory and the link/ directory only includes the .fvwm/ directory. The home/ and link/ dirs don't contain anything and are not needed. I hope i explained that well enough. 

Unfortunately I do not have my laptop with me atm to post the exact command I am using.

What can I do so that the backup tar ball doesn't include anything but the .fvwm/ directory.

---

### Post by skeezer65134 on 2005-12-27
As for that bash script linkunderscore, I usually just make the script cd into the dorectory it's coming from. I know there's a way to make tar do it, but I never bothered to learn how. An example might be:
```
#!/bin/sh

cd /home/link

tar -jcvf /location/of/backup/fvwm_`date '+%m.%d.%Y'`.tar.bz2 .fvwm
```

This will create a bzipped tar of the .fvwm directory and create a backup file with the current date. It might be bad prectice for your scripts to jump around to directories, but this'll work for what you want.



Maglis, thanks for the Unison suggestion, I'll have to look into it. I still have some wuestions about it, which I could probably Google up, but I'll most likely just install it and play with it.

Anyone else have any other suggestions besides just running rsync? I plan to build the machine this week since I finally have a handful of 160gb hard drives.

---

### Post by rasmusbp on 2006-01-02
i'm trying to synchronize the stuff on my shared partition (i'm running a xp dual boot system). I'm synchronizing to a password protected (remote) ftp-directory. I've been struggling to get FullSync to work, but gave up. Then following this thread, I tried Unison (using the gtk app). But I get this error when trying to set it up: 

> Uncaught exception Prefs.illegalValue("rsh://sv_bildepetersendk@/dokumenter/passwd/Rasmus//ftp.bildepetersen.dk missing host)

Can't unison use ftp to sync directories? The URL looks completely screwed...

I'll appreciate any help! 

Cheers,
Rasmus

---

### Post by ubuntumaneh on 2006-01-02
I use a the very old simple bash script for making bzip2ed tar of my home (or anything if you wish), and then I use rsync between different machines. Cron does the work.
I have a file of something around 500Mb that I need to backup once a week. So I have a script that splits the bak.tar.bz2 file into lots of 8Mb, then send them all to a gmail account. It takes too long, but while I don't have a pen drive it is a satisfactory solution, for I have to use this file in different machines, some of them I cannot use rsync.

---

### Post by maglis on 2006-01-02
[quote=rasmusbp]Can't unison use ftp to sync directories? The URL looks completely screwed...
[/quote] From the [unison manual]("http://www.cis.upenn.edu/%7Ebcpierce/unison/download/releases/stable/unison-manual.html#basics"):

>  The syntax for roots is based on that of URIs (described in RFC 2396). The full grammar is:    *replica* ::= [*protocol*:]//[*user*@][*host*][:*port*][/*path*]
           |  *path*

  *protocol* ::= file
            |  socket
            |  ssh
            |  rsh

  *user* ::= [-_a-zA-Z0-9]+

  *host* ::= [-_a-zA-Z0-9.]+

  *port* ::= [0-9]+
 which I thinks says no to your question.

If you have to use ftp, the best solution to suggest for simple file and directory synchronisation is use the gFTP client. You can use it to compare the local with the remote trees and transport any different files or folders either way.

---

### Post by rasmusbp on 2006-01-05
Thanks Maglis. 

However, I don't have the patience to synchronize each and every directory etc. So, since there does not seem to be any suitable linux-apps for FTP synchs, I'm now running SyncBack (XP) in Wine, which is working fine, except for the automatic scheduling. Just have to remember to run it every now and then....

Cheers,
Rasmus

---

### Post by linkunderscore on 2006-01-10
[QUOTE=skeezer65134]As for that bash script linkunderscore, I usually just make the script cd into the dorectory it's coming from. I know there's a way to make tar do it, but I never bothered to learn how. An example might be:
```
#!/bin/sh

cd /home/link

tar -jcvf /location/of/backup/fvwm_`date '+%m.%d.%Y'`.tar.bz2 .fvwm
```

This will create a bzipped tar of the .fvwm directory and create a backup file with the current date. It might be bad prectice for your scripts to jump around to directories, but this'll work for what you want.



Maglis, thanks for the Unison suggestion, I'll have to look into it. I still have some wuestions about it, which I could probably Google up, but I'll most likely just install it and play with it.

Anyone else have any other suggestions besides just running rsync? I plan to build the machine this week since I finally have a handful of 160gb hard drives.[/QUOTE]

I swear I tried to cd /home/link/ before in the script...but it works now so whatever. :) Thank you very much :)

---

### Post by Haegin on 2006-01-29
How could you set the script to run when you remove a usb device but before it unmounts the drive? Im hoping to set it up so whenever I unplug my usb disk it backs up the contents to /home/harry/usbBackup/<date of backup> and then I can use another script that runs on a crontab to remove backups older than a week or something.

Any ideas?

---

### Post by ritger on 2006-01-29
I've always liked rsnapshot. Simple to configure, creates incremental backups using rsync and works over ssh should you need that. It also comes with a handy little switch that detects whether the backup root exists.

---

### Post by skeezer65134 on 2006-04-20
It's been a while since I posted in here...

I have been using Unison over SSH with shared keys for a while now and it's working out awesome. It runs every night and syncs what I want from my desktop to my Raid server. I really like the configuration files that Unison uses, and I also like how it's cross-platform (as much as I don't need that). The best part is that it only takes a couple minutes to parse through ~80GB+ of data and sync all the data (unless, of course, I change all 80GB or it...).

Anyway, if anyone has a scenario like me (see my previous post on the bottome of page 1), I would highly recommend Unison. You need to learn how to do shared keys with SSH as well as figure out the ssh-agent stuff and get keychain working to automate it all, but it's not too hard.

---

### Post by unclben on 2006-08-13
> **skeezer65134 said:**
> Anyway, if anyone has a scenario like me (see my previous post on the bottome of page 1), I would highly recommend Unison. You need to learn how to do shared keys with SSH as well as figure out the ssh-agent stuff and get keychain working to automate it all, but it's not too hard.I'm in a situation very similar to the one you described in your big post earlier in this thread (with the exception that I'm all Linux and *BSD). Through some searching, I came to the same conclusion that you have; Unison is the perfect choice for me.

Unfortunately, it appears that Unison is no longer under active development! Still, it appears to be the best tool out there. I'm gonna give it a try, knowing that it might not be long before there are unacceptable security issues or it stops being packaged in Universe.

---


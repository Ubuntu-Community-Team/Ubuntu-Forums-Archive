---
title: "Network Backup - Need a Solution - rsync? Bacula?"
date: 2005-12-21
forum: General Help
---

### Post by ksudbury on 2005-12-21
Right basically, I have  bunch of machines offsite I need to bacup once a day. 

I have thought about using ssh and rsync. 

However some of the data is on a Windows 2003 server, I thought I could then mount the windows share with samba and rsync that back my main server. 

However will this keep the permissions ?? when I have to restore the data ? 

Rsync will work great for backup as it seems to only backup whats actually changed in the file (this is exactly what i want to save bandwidth & backup time). For example if I have a 4gig file and a user changes some thing minor with the file rsync only transfers what has changed with the file it does not resend the whole file agin just because it has changed (think outlook .pst's or exchange server db). 

Now iv heard great things about bacula but does it work in the same way that rsync does? i.e only transfers what has changed not the whole file? 

Does anyone else use any thing different for backing up? (id like to keep it OS & Free if at all possible)

Also is there a way to backup exchange db in 2000 and 2003 sbs server 

Thanks in advance.

---

### Post by maglis on 2005-12-21
I recommend [I][B]backuppc

[/B][/I]> high-performance, enterprise-grade system for backing up PCs
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

### Post by Koybe on 2005-12-21
[QUOTE=maglis]I recommend ***backuppc***[/QUOTE]

Backup PC is nice if you plan to backup to disk. If you want to backup to an external drive it doesn't fit very well. The biggest advantage is that's easy to use.

You can also have a look to "amanda".

---

### Post by ksudbury on 2005-12-21
Thanks, 

Looking at those two now. Backuppc looks nice would be a good ideal then i could just backup the PC that its running on here to tape ?

---

### Post by Koybe on 2005-12-21
[QUOTE=K31TH]Thanks, 

Looking at those two now. Backuppc looks nice would be a good ideal then i could just backup the PC that its running on here to tape ?[/QUOTE]

Of course you can, it's just a question of automation (sorry for my english, i'm not sure about that word ;) )

---

### Post by ksudbury on 2005-12-21
Yeah need to find some thing that will backup microsoft exchange really. I read on backuppc website that it cannot bkup locked files. 

Anyone used bacula to backup exchange ??


Thanks

---

### Post by John Jason Jordan on 2005-12-21
[QUOTE=Koybe]Of course you can, it's just a question of automation (sorry for my english, i'm not sure about that word ;) )[/QUOTE]
I opened Synaptic intending to install backuppc, only to discover that I must have already installed it.

Unfortunately, it did not install a menu item to launch it from Applications in the panel. I tried "backuppc" from a command line (and "sudo backuppc"), but got an error message that there was no such program.

Where is it and how do I launch it?

---

### Post by ksudbury on 2005-12-21
it runs a web server. when u installed it with apt-get it would of told you this.  point web browser at [http://server-ip/backuppc](http://server-ip/backuppc)

---

### Post by John Jason Jordan on 2005-12-21
[QUOTE=K31TH]it runs a web server. when u installed it with apt-get it would of told you this.  point web browser at [http://server-ip/backuppc](http://server-ip/backuppc)[/QUOTE]
I see. I did not realize it was for backing up Windows computers on a network.

All I am looking for is a simple way to back up my laptop to an external USB pocket drive. I tried Simple Backup but it has too many bugs and doesn't work. Right now the only thing I have found that works is Dump, and that only after a local guru taught me the syntax for how to tell it what to do. It works fine, but God help me if I ever need to do a restore. I have no idea how to do that.

I also looked at rsync, but couldn't make heards nor tails of the syntax.

Any suggestions for a super-simple disk-based backup utility for a standalone Linux box used by an utter dummy?

---


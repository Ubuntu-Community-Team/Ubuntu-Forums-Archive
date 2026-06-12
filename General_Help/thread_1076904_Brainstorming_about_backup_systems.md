---
title: "Brainstorming about backup systems"
date: 2009-02-21
forum: General Help
---

### Post by MountainX on 2009-02-21
What is the ideal system/method for backing up a home file server?

Here are my backup requirements:

1. all new or changed files copied to another HDD periodically (say every hour)

2. Directories that are moved on the original, are moved on the back up copy too. Directory structure on backup matches source structure.

3. files deleted on the original are NOT deleted on backup -- at least not immediately.

4. backup has versioning - X number of versions of changed files are saved for Y number of days.

5. the backup destination contains unarchived files so a single file can be restored with copy/paste and no special tools.

[B]What strategy should I use?

What tools should I use?[/B]

I have started a list of [all Linux backup solutions]("http://davestechshop.net/ListOfFreeOpenSourceLinuxUbuntuBackupSoftware") here: [http://davestechshop.net/ListOfFreeOpenSourceLinuxUbuntuBackupSoftware](http://davestechshop.net/ListOfFreeOpenSourceLinuxUbuntuBackupSoftware)

I would appreciate hearing ideas from people with experience in backing up Linux file servers.

---

### Post by handy on 2009-02-21
You might like what FreeNAS can do?

It will happily run on a PII/III (less electricity than modern boxes) CPU doesn't have to do much unless you choose to use soft RAID, which is usually a waste of time in a home user situation as the LAN is the bottleneck as far as speed of data throughput.

The hardware will cost nothing or close to it, except possibly for a new HDD, if you want to use SATA the simplist method is to buy a cheap PATA to SATA adapter that just plugs directly into an IDE socket on your motherboard (where either the Primary or the Secondary IDE ribbon cable plugs in).

I keep important data backed up on my headless FreeNAS box, it also streams video's across my 10/100 LAN whilst at the same time recording .torrent files.

FreeNAS is easy to set up, has a magnificent browser based GUI that is accessed from a client on the network.

Have a look at the *man rsync* , may do what you want software wise.

---

### Post by HermanAB on 2009-02-21
Rsync is your friend.  It runs on Windows too (Cygwin).

Cheers,

Herman

---

### Post by MountainX on 2009-02-21
> **HermanAB said:**
> Rsync is your friend. 

As far as I can tell, rsync doesn't meet my requirements (particularly #2). [BackupPC]("http://davestechshop.net/ListOfFreeOpenSourceLinuxUbuntuBackupSoftware") seems to be a closer match from what I can tell by doing a little reading... of course, reading doesn't make up for experience (and I don't have any of that).

BTW, I have the hardware. Just looking for a strategy and software recommendations. Thanks.

---

### Post by oiad on 2009-02-22
Check out Back in time

[http://www.le-web.org/back-in-time/]("http://www.le-web.org/back-in-time/")

This is what I run.  It is based to be like the osx time machine feature.  It meets all the features you are looking for.  It uses rsync and a couple of other programs.

---

### Post by MountainX on 2009-02-22
> **oiad said:**
> Check out Back in time

[http://www.le-web.org/back-in-time/]("http://www.le-web.org/back-in-time/")

This is what I run.  It is based to be like the osx time machine feature.  It meets all the features you are looking for.  It uses rsync and a couple of other programs.

Thanks

---

### Post by fjgaude on 2009-02-22
> **MountainX said:**
> As far as I can tell, rsync doesn't meet my requirements (particularly #2). [BackupPC]("http://davestechshop.net/ListOfFreeOpenSourceLinuxUbuntuBackupSoftware") seems to be a closer match from what I can tell by doing a little reading... of course, reading doesn't make up for experience (and I don't have any of that).

BTW, I have the hardware. Just looking for a strategy and software recommendations. Thanks.

I believe **rsync** does meet all your requirements. I would suggest getting **grsync** and giving it a try... it's easy to learn and GUI based, if that helps.

---

### Post by MountainX on 2009-02-22
> **fjgaude said:**
> I believe **rsync** does mean all your requirements. I would suggest getting **grsync** and giving it a try... it's easy to learn and GUI based, if that helps.

Frank - I have no problem learning rsync if that is the best tool. I have read several articles on rsync and looked at the man page. From that reading it seems clear to me that rsync does not satisfy my requirement #2, while [BackupPC and Link-Backup do]("http://davestechshop.net/ListOfFreeOpenSourceLinuxUbuntuBackupSoftware").

I think I have not explained the requirement very well.
This link discusses the requirement in more detail:
[http://wiki.rdiff-backup.org/wiki/index.php/DetectMoves](http://wiki.rdiff-backup.org/wiki/index.php/DetectMoves)

Here's a summary:
Linux logrotate and many other programs change the names of old files with every run, so a large weblog kept online on the original host for four weeks for user access and rotated daily would take up 28 times as much space on a backup server. Similarly it would eat 28 times the network bandwidth, and would slow down the backup runs every single day by the amount of time it took to transfer the entire file. There are other cases a bit less pathological but still significant, such as  when I reorganize my media files that can result in gigabytes of data requiring a second transfer.

---

### Post by MountainX on 2009-03-21
OK, I finally found a great backup solution after a lot of looking. My other backup thread is here:
[http://ubuntuforums.org/showpost.php?p=6933657&postcount=9](http://ubuntuforums.org/showpost.php?p=6933657&postcount=9)

My solution is  [storeBackup]("http://savannah.nongnu.org/projects/storebackup") - [http://savannah.nongnu.org/projects/storebackup](http://savannah.nongnu.org/projects/storebackup)
 
storeBackup is one of only 3 open source backup apps that can handle file renames, moves and copies without wasting space and time. And it is the only backup app that meets all my requirements.

---

### Post by fjgaude on 2009-03-22
Happy you have found what you wanted... **storebackup** sure seems like a full-featured, complex program that handles complex issues.

Keep us informed as to how things go with it. Thanks!

---


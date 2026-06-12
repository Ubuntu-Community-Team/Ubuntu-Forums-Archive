---
title: "[SOLVED] Tracker returns error message on NTFS drive"
date: 2007-12-13
forum: Desktop Environments
---

### Post by schierly on 2007-12-13
Maybe someone can help me!

I have an hdd in my laptop which is partitioned as follows:

1. Windows XP NTFS
2. Linux SWAP
3. Linux EXT3
4. extended NTFS drive with 60GB

I'm using Gutsy.

My problem is that I get an error when trying to search for files:

If I try Locations -> Search for files -> and select my NTFS drive (no. 4) 

the search results come up, but I get the following error code:
"find: //media/Daten/System Volume Information/_restore{62997D7A-4FD7-4262-8FC1-8922E0956ED2}/RP12: input/output error"

The same problem appears if I use the command line search with "find /media/Daten -name ....."
I get tthe same error message.

This doesn't happen on the NTFS partition no 1. 

I assume it must be related with the Folder "Sytem Volume Information" which is created by Win XP. Unfortunately I can't delete this folder. Even not as root.
Is this folder essential? Do I need this folder for the file system? Why there is not such a folder on the first partition?

---

### Post by catach on 2007-12-17
> Is this folder essential? Looks like a Windows [restore point](http://www.microsoft.com/windowsxp/using/helpandsupport/learnmore/systemrestore.mspx) to me. Keeping it around is probably a good idea. You might be able to remove it from inside Windows though, and sudo rm -r _restore{62997D7A-4FD7-4262-8FC1-8922E0956ED2}/RP12 worked for me. 

I would assume the error message is normal however, with the find command simply not having the permissions for the folder. 

(Incidentally, neither of the search methods you mentioned above actually use Tracker)

---

### Post by schierly on 2007-12-17
sudo rm -r _restore{62997D7A-4FD7-4262-8FC1-8922E0956ED2}/RP12 doesn't work for me.

I tried also sudo -Rf ......

And actually I never set a restore point.

---

### Post by catach on 2007-12-17
That is vexing indeed. Out of my depth.

Also, Windows XP creates a restore point at first start, according to [this](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/app_system_restore_hss_understand.mspx).

---

### Post by schierly on 2007-12-17
Ok, I Solved the problem:

First I disabled the System Recovery in Windows XP for the Partition No 4.
After that I still was unable to delete the folder.

After renaming the Folders System Volume information and the sub folder in something without special characters I was able to delete it.

Strange problem, seems that there is I problem with file names including special characters.

---


---
title: "How can I create shell script to copy contents of a shared folder on a XP PC?"
date: 2011-04-08
forum: Desktop Environments
---

### Post by penn919 on 2011-04-08
Hi,

I was wondering if there would be a way for me to copy the contents of a shared folder that's running on an XP system using shell script. Actually, there are two shared folders that I want to do this with. I want to be able to launch the script and automatically copy all the contents of each folder into two separate folders on my ubuntu desktop. For example;

Lets say that I have Shared Folders A1 and A2 on my networked XP system and I have Folders B1 and B2 on my Ubuntu desktop. I want the script to automatically copy the contents of A1 into B1 and likewise for A2 and B2. During the copying, I want the script set up such that any pre-existing files in the B1 & B2 folders will automatically get overwritten by the ones copied from A1 & A2.

Is there any possibilities of me achieving this?

---

### Post by JEDIDIAH on 2011-04-08
Get that remote file system exported from the XP box mounted on your Ubuntu box first. 

Once you do that then it just becomes a generic Unix problem.

---

### Post by penn919 on 2011-04-08
> **JEDIDIAH said:**
> Get that remote file system exported from the XP box mounted on your Ubuntu box first. 

Once you do that then it just becomes a generic Unix problem.

Okay, so how do I do that? ..and would I have to do that every time I launch the script?

---

### Post by oldfred on 2011-04-08
I gave up on Samba since sometimes Ubuntu updates and most of the time any update to windows, firewall or other security stuff I had in windows would stop Samba from working. I liked Ubuntu enough I installed Ubuntu on my portable that had XP and have not looked back. I changed to NFS (not in windows) and now using SSH(may be possible on windows but I do not know how).

But I saved some links. As JEDIDIAH said once you get it mounted then it is just a standard rsync script.

[http://ubuntuforums.org/showthread.php?t=1375183](http://ubuntuforums.org/showthread.php?t=1375183)  Morbius1
The two ways you can share folders are Nautilus-Share ( or Simple Sharing ) and "Classic Samba". Do not mix them up as that can cause issues.

Howto: Fix Windows share browsing issues 
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)
Sharing issues
[http://ubuntuforums.org/showthread.php?t=1374369](http://ubuntuforums.org/showthread.php?t=1374369)
See posts by Morbius1
[http://ubuntuforums.org/showthread.php?t=1649380](http://ubuntuforums.org/showthread.php?t=1649380)

 HOWTO: Setup Samba peer-to-peer with Windows 
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
For definitive explanation of SMB (CIFS) and how it works, see here .
[http://ubiqx.org/cifs/SMB.html](http://ubiqx.org/cifs/SMB.html)

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by cjhabs on 2011-04-08
In the script have:

sudo mount -t smbfs //pc_server/share_folder /media/local_folder -o file_mode=0777,dir_mode=0777,user=user_on_pc%password_on_pc

.. rsync files for copy here ...

sudo umount /media/local_folder

---

### Post by penn919 on 2011-04-08
> **cjhabs said:**
> In the script have:

sudo mount -t smbfs //pc_server/share_folder /media/local_folder -o file_mode=0777,dir_mode=0777,user=user_on_pc%password_on_pc

.. rsync files for copy here ...

sudo umount /media/local_folder

I'd like to try that out, but I'd really appreciate it if someone could either show me or at least direct me to a link to show me howto do the rsync part. I've already searched on google, but I couldn't find anything with regards to rsync with a remote mounted file system.

sorry,I'm completely new to scripting.

---

### Post by cjhabs on 2011-04-08
Here is an excerpt from one of my backup scripts - SOURCE is on the local Ubu machine, DEST is the mounted filesystem from the remote machine.
```

#!/bin/sh

#######################################################################
# Backup /home/chris/Music to the media drive on the server
SOURCE="/home/chris/Music/"
DEST="/media/internal/Media/Music"
LOGFILE="/home/chris/logs/rsync_music2server.txt"

rm -rf $LOGFILE
rsync -auz --log-file=$LOGFILE $SOURCE $DEST
echo "Music backup Done - log file is $LOGFILE"

```

---

### Post by oldfred on 2011-04-08
Links to a couple of more:

Back to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

---


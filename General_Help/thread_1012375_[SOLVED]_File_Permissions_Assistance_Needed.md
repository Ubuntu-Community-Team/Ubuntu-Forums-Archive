---
title: "[SOLVED] File Permissions Assistance Needed"
date: 2008-12-15
forum: General Help
---

### Post by elanning on 2008-12-15
Greetings,

I am running Ubuntu 8.10 i386, and I have VirtualBox installed, and a single VM with WinXP Pro sp2 running on it.  Inside the VM I downloaded a few music tracks, then again from within the VM I accessed a shared folder that is on the Ubuntu OS and copied the files to that folder, basically as a way to get the songs from inside the VM to outside the VM.

It worked, but they have that little lock icon, and when i look at permissions no one has any permissions.  I am unable to to move or do anything to the files it keeps saying permission denied.  

Two questions:

Is there a way to like take ownership of the files?
Or
Is there a better way I should be transferring files from the XP-VM out to the host Ubuntu system?


Thanks!

---

### Post by drs305 on 2008-12-15
To change the ownership, use this command. the second command sets the user permissions to rwx, group to rx, and others have no access:

```

sudo chown -R *yourusername* /path.to.music.folder
chmod 750 -R /path.to.music/folder

```

Example with *elanning* as your username:
sudo chown -R elanning /home/elanning/mymusic
chmod 750 -R /home/elanning/mymusic

Note: If the partition you saved the files to is either fat or ntfs, ownership is set at mounting and will not be changed by the above commands.

Added: If you ever have problems moving files, you can open nautilus with the command "gksudo nautilus" and you will have admin rights to do anything you wish with any file, including moving or deleting folders/files (so be careful).

---


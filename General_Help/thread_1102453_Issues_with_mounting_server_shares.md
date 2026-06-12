---
title: "Issues with mounting server shares"
date: 2009-03-21
forum: General Help
---

### Post by Nano_ext3 on 2009-03-21
&#65279;Im trying to figure out why I cant save an Open Office doc to my server, root can , but not mikeyd.  This is not a permissions thing with the mount command, as rw is default, and any internal partitions (on my desktop).    I can save to the windows NTFS partition just fine.  Its only on my server share.   Do you think I need to add "mikeyd" , my user name, on my linux box, to the users/groups on my Server 2003 box?

[LIST]
[*]I Can:  Can save to any internal NTFS drive on my LINUX DESKTOP
[*]I CANNOT: Cannot save to the server drive on my Windows 2003 Server,  unless I "sudo cp" the file over.  
[/LIST]

**Here is ls -la for my server at /mnt/DEATH_SERVER**

> mikeyd@mikeyd-desktop:/mnt/DEATH_SERVER$ ls -la
total 8
drwxr-xr-x 6 root root 4096 2009-03-09 17:57 .
drwxr-xr-x 3 root root 4096 2009-03-09 17:54 ..
drwxrwxrwx 1 root root    0 2009-03-10 17:40 DEATH_SERVER_MOVIES_GAMES
drwxrwxrwx 1 root root    0 2009-03-19 12:54 DEATH_SERVER_MP3
drwxrwxrwx 1 root root    0 2009-03-21 17:12 DEATH_SERVER_PROGRAMS
drwxrwxrwx 1 root root    0 2009-02-12 03:02 DEATH_SERVER_TV
mikeyd@mikeyd-desktop:/mnt/DEATH_SERVER$ 

**Here is the contents of the script that I use to mount the drives**

> #! /bin/bash
# script to mount my DEATH_SERVER shares while on the Local LAN


mount -t cifs //192.168.1.25/E          /mnt/DEATH_SERVER/DEATH_SERVER_PROGRAMS/         -o credentials=/root/.smbcredentials;
mount -t cifs //192.168.1.25/F          /mnt/DEATH_SERVER/DEATH_SERVER_MP3/              -o credentials=/root/.smbcredentials;
mount -t cifs //192.168.1.25/G          /mnt/DEATH_SERVER/DEATH_SERVER_MOVIES_GAMES/     -o credentials=/root/.smbcredentials;
mount -t cifs //192.168.1.25/H          /mnt/DEATH_SERVER/DEATH_SERVER_TV/               -o credentials=/root/.smbcredentials;


Is this a group / users issue?  Im wondering do I have to add "mikeyd", my user name on the LINUX BOX to the permissions of the drives on my Server 2003 Box?

Im welcome to any suggestions.  Let me know if you need any more output from my Linux Box.


Cheers!'

_Nano

---

### Post by dcstar on 2009-03-21
> **Nano_ext3 said:**
> 
..........
Im welcome to any suggestions.  Let me know if you need any more output from my Linux Box.


There are two sets of permissions **on the server** that you have to conquer: The "share" permissions as well as the ACL permissions.

If **either** do not allow your user credentials to write, then you cannot write.

---

### Post by Nano_ext3 on 2009-03-21
What do I need to add the server share permissions?  My linux username?

---


---
title: "strange file permissions - who's the owner?"
date: 2005-07-23
forum: Desktop Environments
---

### Post by spudley on 2005-07-23
I've got a situation with a file (presently only 1) that is unusual and I'd like to find out what I may have done to create the 'situation', how to fix the situation and possibly prevent this from happening in the future.

First, an outline of my system/network
1) a linux based storage server
2) several Windows systems (XP & 2Kpro machines)
3) Ubuntu on a workstation (for testing/playing, hopefully eventually full migration)
4) a w2k server (irrelevant for this situation).

Anyway...
on my last Ubuntu install, I saved a file "ubuntu todos.txt" on my storage server (mounted in /media/nas)

I ended up shuffling drives around and reloaded Ubuntu onto a different box -- I don't recall the user name I had used before - so I just setup a new user name & password  this time around user is 'e').

Anyway, logged in as 'e', I loaded my old "ubuntu todos.txt" file from my storage server, made some changes, saved fine.

I think in there I had a reboot to do (probably to test my networking settings/whatever).

Now, I can't edit that file - I can open it, view its contents, but can't make changes & save - Ubuntu says 'permission denied'.  So, I try the 'sudo gedit FILENAME' enter my password and STILL can't save changes to the file.
I copied the file - and even the copy has permissions of the original.
I can't "sudo rm FILENAME" either (permission denied).

My XP machines report permission denied, and my W2K machines say "file in use".

How did this happen, how can I over-ride the permissions that are on there?


Any thoughts??

---

### Post by crashtest on 2005-07-23
[QUOTE=spudley]I've got a situation with a file (presently only 1) that is unusual and I'd like to find out what I may have done to create the 'situation', how to fix the situation and possibly prevent this from happening in the future.

First, an outline of my system/network
1) a linux based storage server
2) several Windows systems (XP & 2Kpro machines)
3) Ubuntu on a workstation (for testing/playing, hopefully eventually full migration)
4) a w2k server (irrelevant for this situation).

Anyway...
on my last Ubuntu install, I saved a file "ubuntu todos.txt" on my storage server (mounted in /media/nas)

I ended up shuffling drives around and reloaded Ubuntu onto a different box -- I don't recall the user name I had used before - so I just setup a new user name & password  this time around user is 'e').

Anyway, logged in as 'e', I loaded my old "ubuntu todos.txt" file from my storage server, made some changes, saved fine.

I think in there I had a reboot to do (probably to test my networking settings/whatever).

Now, I can't edit that file - I can open it, view its contents, but can't make changes & save - Ubuntu says 'permission denied'.  So, I try the 'sudo gedit FILENAME' enter my password and STILL can't save changes to the file.
I copied the file - and even the copy has permissions of the original.
I can't "sudo rm FILENAME" either (permission denied).

My XP machines report permission denied, and my W2K machines say "file in use".

How did this happen, how can I over-ride the permissions that are on there?


Any thoughts??[/QUOTE]


SO what are the file permissions, and who is the owner?  Can you logon to the file server directly as root, or with an account with sudo rights, and change the permissions there?

Trying to change permissions or ownership with sudo on the Ubuntu box won't work unless the fileserver is exporting NFS shares with root permissions intact.  (You are using NFS, right?)  By default most systems will export NFS shares with root permissions "squashed", so if that's the case, you will need to be on the file server to fix the problem, NOT on a machine that is mounting the filesystem.

Check the /etc/exports file on the fileserver, and see how the share is being exported.

---

### Post by scoon on 2005-07-23
Hey there, 

What does stat on the file show you ?

regards, 

scoon

---

### Post by spudley on 2005-07-23
Crashtest:
The linux based file server is a 'locked out' system... I can access only very basic read-only info on it.... so its not much help in that regard.

The server is using SMB not NFS.

Scoon & Crashtest:

stat on the file reports:
  File: `ubuntu todos.txt'
  Size: 568             Blocks: 2          IO Block: 4096   regular file
Device: eh/14d  Inode: 342263      Links: 1
Access: (0755/-rwxr-xr-x)  Uid: ( 1000/   e)   Gid: (    0/    root)
Access: 2005-07-23 15:44:28.000000000 -0400
Modify: 2005-07-22 20:53:46.000000000 -0400
Change: 2005-07-22 20:53:46.000000000 -0400


I just now wonder if this could in some way be related to a problem I have with mounting my network file server?

I install samba & smbfs, but in fstab I have to 'force' the mount with my specific user name -- I've never been able to get other users to work with it by assiging a group -- here's my fstab entry:
//nas-media/disk-2	/media/nas-disk2	smbfs	username=admin,password=XXXX,workgroup=TCM,uid=e	0	0

I've tried to change uid=e to gid=mygroup (where my group has various UID's assigned to allow access to this network share) but never had any luck (always end up with read only access doing this).

Not sure if that has anything to do with it or not, just a thought that might shed light on the matter.

Thanks for any continued advice/ideas!

---

### Post by scoon on 2005-07-23
Hey there, 

If that file lives on a read only file server then you will only beable to read it.
 There are plenty of threads around that will help you with samba.  

regards, 

scoon

---

### Post by crashtest on 2005-07-23
[QUOTE=spudley]
Access: (0755/-rwxr-xr-x)  Uid: ( 1000/   e)   Gid: (    0/    root)
[/QUOTE]

The gid (Group ID) of the file is root.  The file is owned by account 'e' which is part of group root, but only 'e' can write it - not even other members of group root can write the file.   I really don't follow who 'e' is supposed to be here.  Have you created a user account with gid 0?

When you log into the ubuntu box as account 'e', type 'id', and let's see who you really are.  Please report back the output when you type 'id'.

About the file server - is this your server, or someone else's?  If it is yours, why you do have such limited access?

---

### Post by spudley on 2005-07-23
Scoon,  the file server the file is on, is _not_ read only -- only 'settings' and info reported by the fs OS.

Crashtest, logged in as user 'e', id reports:
uid=1000(e) gid=1000(e) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(lpadmin),108(scanner),109(admin),1000(e)

This is based on a pretty much 'new' Ubuntu install... only done some updates, and basic app installs since I started running it... the file was originally created on Ubuntu, but after a _lot_ of messing around trying to get the fstab gid/uid 'situation' to work.  Perhaps I messed something up with gid/uid in my lack of understanding of those entries in fstab, which caused the file to lock up now that I tried again to use it with a new Ubuntu install?  (although it baffles me as to why it worked (let me save changes) once, but no longer).

The file server is mine... its very restricted as its a custom linux build that does nothing but boot the machine into a file server mode (the only thing to configure is my workgroup name, and machine name/IP) and its done.  (its more of a NAS box than a 'file server'.

---


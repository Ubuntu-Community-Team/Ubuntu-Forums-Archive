---
title: "Best way to automount NAS SMB shares for separate users"
date: 2012-07-08
forum: Desktop Environments
---

### Post by Gink on 2012-07-08
Hello, I'm setting up a new system that has 2 user accounts
user1 - admin acount
user2 - standard account

I have a NAS with 3 SMB shares set up: Storage, Music, Utilities.
Both users have accounts on the NAS and all permissions are set up in the NAS filesystem (FreeNAS 7).

I want to automount all 3 shares for user1 w/appropriate login/perms, and 2 of the 3 (Storage/Music) for user2.

I installed smbfs, created a .smbcredentials file in each users home folder that looked like:

username=user1
password=password

or 

username=user2
password=password

then added to fstab

//192.168.xxx.xxx/Storage /home/user1/NAS/Storage cifs credentials=/home/user1/.smbcredentials
//192.168.xxx.xxx/Music /home/user1/NAS/Music cifs credentials=/home/user1/.smbcredentials
//192.168.xxx.xxx/Utilities /home/user1/NAS/Utilities cifs credentials=/home/user1/.smbcredentials
//192.168.xxx.xxx/Storage /home/user2/NAS/Storage cifs credentials=/home/user2/.smbcredentials
//192.168.xxx.xxx/Music /home/user2/NAS/Music cifs credentials=/home/user2/.smbcredentials

And while this sort of worked to mount, the permissions were all screwed up and basically showed all the folders and such in the share as being owned by user2, and wouldn't allow user1 access into folders that are actually owned by user1.

I changed fstab with the same 5 entries but ditched using the smbcredentials file...

//192.168.xxx.xxx/Storage /home/user1/NAS/Storage cifs username=user1,password=password,uid=user1,gid=homegroup 0 0
//192.168.xxx.xxx/Storage /home/user2/NAS/Storage cifs username=user2,password=password,uid=user2,gid=homegroup 0 0

I set up these users with the same usernames they have on the NAS, added the "homegroup" group to ubuntu with them as members, and added the uid/gid into fstab hoping that would get permisions correct. It works better, but permissions show the group for all folders/files as being user2, which isn't hurting anything, but isn't correct.

My guess is the main problem here is fstab mounts these system wide, and what I'm really trying to do is mount the same shares in different places with different user login info and that's causing some issues. But I've searched around and haven't found any information in setting things up to automount anywhere besides fstab. Is there a file that can be created in a user's home folder that will automount shares just when they login, rather than at boot via fstab?

Any tips would be appreciated. Thanks.

---

### Post by LewisTM on 2012-07-09
Can you access these SMB locations using Nautilus's Network Browser?

If so then the solution is surprisingly easy. 
[LIST=1][*]Install **Gigolo**.
[*]For each user open Gigolo and add network bookmarks to the shares. 
[*]Set the keyring to remember the passwords forever.
[*]Set the bookmarks to autoconnect
[*]Add Gigolo to the startup applications. 
[*]Set Gigolo to start minimized in the Notification area.
[/LIST]
The locations will be mounted in each user's home directory in ~/.gvfs
You can create symlinks to them if you would like to see them in another location.

This can be labeled as the "modern" way of automounting network shares at the user level.

Cheers!

---

### Post by Gink on 2012-07-09
Cool, thanks for the detailed response. It figures there's a simple "modern" way of doing this. Of course, I spent hours researching and implementing a rather complex method having bash scripts autorun for each user at login, which of course involved learning about sudoer, sudoer.d and associated config files. 

I ended up having to use mount -t smbfs in the commands, for some reason mount -t cifs and mount.cifs both didn't apply permissions correctly. 

Anyway, glad to have this info, I think I'll disable the autostart scripts and give this method a whirl, see how well it works. Running the bash scripts to mount at login seems to slow down the process of getting logged in and the gui loaded up more than I would expect, so maybe Gigolo will get things running faster.

Cheers!

---

### Post by Gink on 2013-05-04
This has stopped working upon upgrading to 13.04, shares are no longer showing up in the .gvfs folder. I'm wondering if there was a change to the file manager that's causing it, but haven't turned anything up yet, hopefully will figure it out soon.

---

### Post by Morbius1 on 2013-05-04
It may be still working but the "gvfs" folder has moved. It's now at:
```
/run/user/your-user-name/gvfs
```

---

### Post by Gink on 2013-05-06
Thanks Morbius, made new symlinks from that path and they seem to be working just fine.

---


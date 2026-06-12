---
title: "Question about users and permanently mounted samba shares?"
date: 2009-04-17
forum: General Help
---

### Post by rhcm123 on 2009-04-17
I have a samba share on my home server. It is setup so that each user gets their own directory (i.e. /share/ussr, /share/elisabeth, etc) and the directory is chowned to them (they have a unix account on the server for our home email) and chmoded 700. (There is also a /share/public that they all can read).

My question is, when the share is permanently mounted with this code in /etc/fstab (this mounts my username to the share):
```
//192.168.2.193/share /media/remote smbfs credentials=/root/.smb1,umask=000,user,auto   0 0

```
I can logically enough access my own directory.


Now, here is my problem. I want it to be that when elisabeth logs in, the system mounts the server with her username. It then unmounts it when she logs out. When fred logs in, it mounts the server under his name. This is to make sure the users get proper access to their directories.

Ideas?

---

### Post by aaronp on 2009-04-18
I may be misunderstanding what you are trying to do but are you saying you want the same mountpoint to handle three different shares depending on who logs in? Could this cause problems if more than one of you log in to the server simultaneously?

Also, I believe Samba has a much easier implementation of what you are after by using the [homes] share settings. In which case each user who logs in is given appropriate access to their own home folder, assuming they have a user account and home folder on the server system.
Is this more what you are after?

---

### Post by rhcm123 on 2009-04-18
> **aaronp said:**
> I may be misunderstanding what you are trying to do but are you saying you want the same mountpoint to handle three different shares depending on who logs in? Could this cause problems if more than one of you log in to the server simultaneously?

Also, I believe Samba has a much easier implementation of what you are after by using the [homes] share settings. In which case each user who logs in is given appropriate access to their own home folder, assuming they have a user account and home folder on the server system.
Is this more what you are after?

Yes, i would like the same mountpoint used, and it to change it's login credentials everytime a user logs out. I doubt this will cause problems, but ill deal with those as they come along. heck, my dad is really the only one who uses that PC anyways.

the problem is, i already setup a pretty complex /share partition (it's it's own 200 GB) and i would like to keep it that way. Do you mean changing the users home directory to /share and letting them go in that way? I guess i could do that - ill post my smb.conf soon, it's sleep time now :)

---

### Post by aaronp on 2009-04-18
> **rhcm123 said:**
> Yes, i would like the same mountpoint used, and it to change it's login credentials everytime a user logs out. I doubt this will cause problems, but ill deal with those as they come along. heck, my dad is really the only one who uses that PC anyways.

the problem is, i already setup a pretty complex /share partition (it's it's own 200 GB) and i would like to keep it that way. Do you mean changing the users home directory to /share and letting them go in that way? I guess i could do that - ill post my smb.conf soon, it's sleep time now :)

I wasn't really sure what you were looking to do but potentially you could mount each person's part of the 200gb share as (or in) their home partition and then let the samba auto stuff take care of the permissions depending on who logs in.

---

### Post by rhcm123 on 2009-04-18
> **aaronp said:**
> I wasn't really sure what you were looking to do but potentially you could mount each person's part of the 200gb share as (or in) their home partition and then let the samba auto stuff take care of the permissions depending on who logs in.

the problem is anything not mounted in /media dosen't show up on the desktop, and that was a major selling point for my dad

---

### Post by aaronp on 2009-04-18
How is this the case if he is accessing it via Samba. His desktop would be his own desktop on whatever local client he is using?

---

### Post by rhcm123 on 2009-04-18
> **aaronp said:**
> How is this the case if he is accessing it via Samba. His desktop would be his own desktop on whatever local client he is using?

wait, what?

I want the share to unmout whenever a user logs out, and remount when ever a user logs in (with apporpriate login names/credentials).

---

### Post by Yashiro on 2009-04-18
Do not mount it in the fstab.
Connect to the Server using Nautilus.
Create a bookmark within Nautilus that points to the server.

The share will always show on the desktop after the bookmark has been clicked and will also unmount on logout.

---

### Post by aaronp on 2009-04-18
> **rhcm123 said:**
> wait, what?

I want the share to unmout whenever a user logs out, and remount when ever a user logs in (with apporpriate login names/credentials).

Oh I see, sorry. You are using the Samba shares to share these partitions to users who log into the same workstation. I was thinking these people were going to be logging into a 'server' from other workstations.
You could probably achieve this without worrying about Samba but now that you have Samba set up you could just create launchers to the appropriate mountpoint on the Samba server for each user's desktop.

---


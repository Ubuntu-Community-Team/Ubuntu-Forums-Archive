---
title: "Connect to Server - Location on Filesystem"
date: 2007-07-16
forum: Desktop Environments
---

### Post by discern on 2007-07-16
When one uses the "Connect to Server" option in Ubuntu, where does one find the link to this newly mounted share in the filesystem?

:confused:

For example, I selected Places > Connect to Server... then selected "Windows share" from the list. I was able to mount to the desired point, in this case, a network drive on the network, and an alias appeared on my Ubuntu desktop. However, any efforts to locate the mount point using Terminal were futile. There IS something called /NetHDD (the default name for the network drive) in the root directory, but it appears to be empty. However, clicking the alias on the desktop reveals that it is not empty.

I need to find where the "Connect to Server" mounts this so I can use it as an automatic backup drive.

Thanks.

---

### Post by fjgaude on 2007-07-16
It mounts on the share set up on the Server under SMB, Samba. Find that and change it to what ever you wish to where your backup will go.

Am I missing something here?

frank

---

### Post by discern on 2007-07-17
Forgive me as I am relatively new to Ubuntu.

"...On the share set up on the Server under SMB, Samba."

Where exactly is that located? For example, /home/share/smb/ (I know that doesn't exist, but I would like the file path to the mount point). Does that make sense? I've browsed around to no avail. Ideally, I would like to replace the "alias" on the desktop with a tru link to the mount point so I can configure sbackup quickly.

Cheers!

P.S. I am running Ubuntu 7.04, The Feisty Fawn.

---

### Post by discern on 2007-07-19
Anyone have any idea where "Connect to Server" stores an accessible (in Terminal) link in the file system?

---

### Post by mcduck on 2007-07-19
> **discern said:**
> Anyone have any idea where "Connect to Server" stores an accessible (in Terminal) link in the file system?

I'm pretty sure it doesn't work that way.

If you want to access Samba shares from terminal you should just mount them somewhere using smbfs (samba file system).

---


---
title: "NFS Mount Problem?"
date: 2009-05-13
forum: General Help
---

### Post by r0d3nt on 2009-05-13
I have a Fedora Core 10 64-BIT server that has a very basic export:

/home/username 192.168.0.0/16(rw,sync)

When I try to connect a Ubunu 9.04 32-BIT system via this fstab option:

servername:/home/username /home/username/mnt/sharename nfs rw,auto 

I get a sharename mounted that only root can write too with a weird uid and gid:

drwx------ 59  500   500 4096 2009-05-13 15:39 sharename

I've tried a few options including nfsvers=2 in the options section of the fstab file, but nothe tried a to work.  I know for a fact that if I attempt this on another Fedora Core 10 based system, this will mount the nfs share with the proper  read and write permissions I am expecting.  I've seen a few other posts regarding this, but I wasn't able to get what was suggested to work.

Does anyone have any ideas on  what might be causing this problem?  Is there a server option that I need to enable because Ubuntu is a little more strict in how it treats NFS mounts?

Please advise...

---

### Post by HuckleSmothered on 2009-05-15
That UID of 500 is the number for the user that owns the folder on your fedora server. The command "cat /etc/passwd" (on your server) will show the list of users and id's. As well as doing a "id <username>" command.

I think you still have to make sure the permissions on the server folder are appropriate for what you want. A home folder does not typically have R or W permissions for anyone besides the owner. The mounting "rw" option does not override this. Change the permissions on the server folder to something at least 755 (R and X for all) or more open if you need. Re-export the share. Re-mount the share.

---

### Post by r0d3nt on 2009-05-15
That makes sense, and no wonder it worked with one Fedora system connecting to another because of the same UID.  I thought a quick fix would be to change the UID for my ubuntu user account to match 500...not the best idea.  So now it sounds like if I want to get this to work, the share is going to have to be a different directory altogether with a different set of permissions.  Are there any other ways around this via NFS?  I'd really rather just access the home directory share.  I do have it shared out via SAMBA, so maybe I'll just settle for that.

---

### Post by HuckleSmothered on 2009-05-16
Doesn't have to be a different directory than the home folder. You just have to setup the home folder with the right permissions, RWX for everyone. Some may disagree with the security of this approach, but it is one that I use with NFS. I prefer NFS much more than Samba as well.

Might also want to add the no_root_squash option to the exports file. Add it where the rw,sync are to look like this /home/username 192.168.0.0/16(rw,sync,no_root_squash)

---


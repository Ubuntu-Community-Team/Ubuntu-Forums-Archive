---
title: "Samba Permissions"
date: 2007-04-14
forum: Desktop Environments
---

### Post by sparty2809 on 2007-04-14
When using eclipse with samba, I am able to read and write.  However, when I switch from eclipse to firefox, it always comes back with this message ""The file has been changed on the file system.  Do you want to load the changes?"

I mount the drive like this: 
mount -t cifs -o username=username,password=password //IP_ADDRESS/SHARE_NAME /mnt/MOUNT_FOLDER

It is a Windows Network drive.  

Any ideas why this is happening and how to fix it?

---

### Post by neurosis on 2008-05-13
Have you found any resolution to this? 

I've been getting this one for ages, and it drives me a little batty. It would be nice if you could just turn the file monitoring feature off entirely (since I'm the only one working on this project). There are a few bugs filed against this at bugs.eclipse.org, but no fix as of yet.

---


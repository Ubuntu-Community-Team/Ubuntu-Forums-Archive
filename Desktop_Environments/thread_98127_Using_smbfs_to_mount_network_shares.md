---
title: "Using smbfs to mount network shares"
date: 2005-12-02
forum: Desktop Environments
---

### Post by polpak on 2005-12-02
The only problem I have with this  is that it requires the user to either have administrative privileges(via sudo) or the samba details (user & password) have to be in a world readable file (/etc/fstab) in order to mount remote shared directories.

If anyone else knows of a way to remove the restrictions above I'd love to hear them.

Basically I feel that so long as the directory the smbfs is mounted to is owned by the user, and the user has the appropriate username & password for the shared directory, the user should be able to use mount (without root privileges and without an entry in fstab) to mount it.

I'm writing a script which will use a user readable only config to mount shares to a given users home directory. Then you can edit /etc/sudoers to specify which users you want to be able to use this script. This will solve the problem but I'd like to know if there is a more "standard" way of accomplishing this task.

Thanks

---

### Post by Robgould on 2005-12-02
There is a way, I read it somewhere and even did it once, but it did not stick.  It involves making a credentials file.  It was in one of the documentation pages...I can't find it right now.  I will look later

---

### Post by Robgould on 2005-12-02
I looked, I can't find it anymore.  Maybe I am having a misfire.  Sorry.

---

### Post by MetalMusicAddict on 2005-12-02
[HERE]("http://ubuntuguide.org/#automountnetworkfoldersall")

Its from the 5.04 guide but is still good. ;)

---

### Post by Abhi Kalyan on 2006-11-06
> **MetalMusicAddict said:**
> [HERE]("http://ubuntuguide.org/#automountnetworkfoldersall")

Its from the 5.04 guide but is still good. ;)
Thank you for the info.
Will work on it

---

### Post by mattskr on 2006-11-07
Try this one:

[http://www.ubuntuforums.org/showthread.php?t=255872&highlight=smbfs]("http://www.ubuntuforums.org/showthread.php?t=255872&highlight=smbfs")

---

### Post by dannyboy79 on 2006-11-07
best thread for this ever, [http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

---


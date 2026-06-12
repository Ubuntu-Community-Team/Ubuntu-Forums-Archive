---
title: "Cannot mount volume"
date: 2008-01-04
forum: Desktop Environments
---

### Post by IndianaThreepwood on 2008-01-04
I am able to sudo mount my NTFS hard drive, with full read&write support through the Terminal. But this is annoying, as every time I want to mount or unmount, I need to do it through the Terminal, using sudo commands. When I try mounting through the GUI (or without the sudo command in the Terminal) I get this error message:
Cannot mount volume.
Unable to mount the volume 'Backup'.
Details: Error opening partition device: Permission denied.
Failed to mount '/dev/hdb5': Permission denied.

I've edited my /etc/fstab file to give permission to all users, but this does not seem to work.
/dev/hdb5 /media/Backup ntfs-3g user,noauto,sync,exec,umask=1000,gid=1000 0 0
I've tried changing various things, and the 'noauto' part works. But I cannot give the user access, it is reserved only for root. Changing the umask and/or gid had no effect.

Am I missing something? Where can I change the permission rights? I just want to be able to mount the hard drive through the GUI.

---

### Post by metalheart on 2008-01-04
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

HTH

---

### Post by IndianaThreepwood on 2008-01-04
I've used the NTFS Configuration Tool, but it does not solve my problem. I cannot click on the Backup icon under Places > Computer to mount the hard drive - I get the same error message. This USED to work, and stopped working after I tried NTFS Configuration Tool (I was led to believe it could defragment ntfs) and removed it again.

It's not like I cannot mount the hard drive, it's just I have to sudo mount it. And I don't understand why the 'user' part in the /etc/fstab file seems to have no effect, when the 'noauto' works just fine.

---


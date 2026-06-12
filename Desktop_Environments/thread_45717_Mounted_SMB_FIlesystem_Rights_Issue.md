---
title: "Mounted SMB FIlesystem Rights Issue"
date: 2005-07-01
forum: Desktop Environments
---

### Post by kklingerman on 2005-07-01
HI,

  I am trying to mount a SMB filesystem to access documents on a Windows 2000 Share.  I created a directory under the mnt folder called share.  I am the owner and therefore have full rights.  I am unable to mount the filesystem using my user account so I use a root terminal.   I've mounted it using the following command:

**mount-t smbfs -o username=username,password=password //server/share /mnt/share**

Now when I check the owner, root is now the owner of the directory.  My user only has read rights.  I've tried using chmod in a root terminal to change the rights to 777 using the following command:

**chmod -R 777 share**

It says it makes a change, but it doesn't.  I am doing this right?  Uggh!!! ](*,) 

Thanks.
Kevin

---

### Post by nocturn on 2005-07-01
Hmm..

I think there is a mount option to set the permissions.
You could also try putting it in fstab with the user option, then mount it as user

[http://linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=205](http://linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=205)

---

### Post by kklingerman on 2005-07-01
Ok.  Put it in the FSTAB and it works.  It seems the UID,GID and UMASK do not work when just running the mount command form the terminal.  Thanks.

---

### Post by Sionide on 2005-07-01
ubuntuguide.org solved all my samba troubles <3

---


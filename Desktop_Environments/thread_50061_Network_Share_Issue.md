---
title: "Network Share Issue"
date: 2005-07-18
forum: Desktop Environments
---

### Post by slada on 2005-07-18
I have a mixed network of WinXP and Ubuntu machines.  The server is running Windows Server 2000.  The Ubuntu machines connect to the network shares with no problem.  However, Openoffice can not open files directly off the network or save directly to the share.

I found the problem in this thread:

[http://ubuntuforums.org/showthread.php?t=39859](http://ubuntuforums.org/showthread.php?t=39859)

My question is whether or not switching to KDE will solve the problem?

Thanks

---

### Post by Zyrix on 2005-07-18
Are you mounting these in fstab or through gnome? If you are mounting them in fstab please post your config file.

Also, is this only in OOo apps? Or can you open a text file on the server and save it? I dont see how this would be a KDE/Gnome issue if you were mounting it in fstab, but if you aren't... try downloading the Live Kubuntu CD and see if you can replicate the same issue.

---

### Post by slada on 2005-07-18
I mounted the share through the gnome interface.  I was going off the thread I linked as well as a couple of others that said it was a gnome/OO issue.  

Thanks for the idea of the Live KDE CD.  I will try it.

---

### Post by bdamon on 2005-07-19
This is a known issue between the gnome vfs and the applications.  You'll find that gedit can open files on a share in this manner but read only. You can find more info from this thread.

[http://ubuntuforums.org/showthread.php?t=45208&highlight=vfs](http://ubuntuforums.org/showthread.php?t=45208&highlight=vfs)

You will have to actually mount the share in fstab so it is mounted at boot or manually mount the share at the cli using mount -t smbfs.
You may have to install smbfs.

sudo apt-get install smbfs

Ben

---


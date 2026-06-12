---
title: "how to change owner of sudo"
date: 2006-08-14
forum: Desktop Environments
---

### Post by torchman on 2006-08-14
While trying to change the permissions for my second hard drive, I accidentally changed the owner of /usr/bin/sudo. When I do "ls -l", what i see is that anyone has read,write, and execute permissions, but the owner is mike (my username) while the group still lists root. When I try to use sudo for a command, I see:
   "sudo: must be setuid root"
I think this is telling me that I need to change the owner of the sudo program to root, however, to do that, I need to be root! I searched around, and the only possible solution I found was:
  become root via su or such
  cd /usr/bin
  chmod 4111 sudo
Since Ubuntu has no root password set, su does not accept any password. The above solution does not work for me. I also tried running visudo, but of course permission was denied, because I was not root.

Does anyone have any solutions, short of reinstalling Ubuntu? Or have I found a weakness in the no-root philosophy, in that a simple "chown mike sudo" can remove the ability to sudo?

---

### Post by aysiu on 2006-08-14
Reboot into recovery mode. Then you'll be root.

---

### Post by torchman on 2006-08-15
Thanks for that help; it sounds like it would work, however I'm not sure how to boot in recovery mode. Could you explain how to do that?

---

### Post by aysiu on 2006-08-15
This explains a bit about how to do that:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

Of course, instead of modifying /etc/sudoers or /etc/group, you'd be changing the permissions on /usr/bin/sudo

---

### Post by torchman on 2006-08-15
I was able to boot into recovery mode, and of course was presented with a root terminal. I changed the owner of sudo back to root, however that still gave me an error when using 'sudo -i' from the user terminal. I even set a root password, figuring that 'su root' would work. Sadly, this is not true either. Here is a listing of what I have now:


$whoami
mike
$cd /usr/bin
/usr/bin$ ls -l sud*
-rwxrwxrwx 1 root root 93844 sudo
lrwxrwxrwx 1 mike root 4 sudoedit ->sudo
-r--r----- 1 root root 0 sudoers
-r--r----- 1 root root 0 sudoers.old
$cd /etc
$ls -l sud*
-r--r----- 1 root root 422 sudoers
$sudo -i
sudo: must be setuid root
$su
Password:
su: Authentication failure
Sorry.
$

All files look normal (see [http://www.psychocats.net/ubuntu/sudo]("http://www.psychocats.net/ubuntu/sudo") ) when opened for editing. 

Even when using 'chown root sudoedit', and getting no errors, sudoedit's owner would not change. Is this important? 
If root owns sudo and sudoers, how is it that I cannot use sudo?

It is possible that I have tweaked the permissions beyond the point of no return, and I would not lose much at all by reinstalling Ubuntu (it is a recent install). I would like to be able to solve this problem, but if there is nothing more to try, I have no issues with reinstalling.

---

### Post by aysiu on 2006-08-15
It looks as if you might have the wrong permissions (here's my output): ```
ls -al sud*
-rwsr-xr-x 1 root root 93844 2006-05-17 01:41 sudo
``` According to [this site](http://www.courtesan.com/sudo/troubleshooting.html), it's supposed to be ```
chmod 4111
```

---

### Post by torchman on 2006-08-17
In recovery mode, I ran:
#cd /usr/bin
#chmod 4111 sudo

Now sudo works perfectly. 
I also set the root password last night, so now su works as well.

I felt that being able to boot into recovery mode as root posed a security risk, so a root password will stop anyone from getting in as root. Am I correct, or is it better to remove the root password (sudo passwd -l root) like this site recommends?

Also, I mounted my second hard drive as root (using 'sudo mount /dev/hdb1 /30gb'). Now, to write to it requires sudo. I have not tried this, but how does one change the write permissions on a disk? Does the chmod have to reference the mount point or the device? In other words, is it:
a) chmod a+w /dev/hdb1
b) chmod a+w /30gb
c) something else?

Also, will a VFAT file system on this hard drive (with root as owner) be readable if I connected it to a Windows machine?

---

### Post by aysiu on 2006-08-17
> **torchman said:**
> 
I felt that being able to boot into recovery mode as root posed a security risk, so a root password will stop anyone from getting in as root. Anyone who has physical access to your computer can do whatever she wants on it... if she's knowledgeable enough. She can boot a live CD and gain root access to all your files. She can remove your hard drive and put it into another computer. And, as you've noted, she can boot into recovery mode.

---

### Post by lupine_nickt on 2006-08-17
Keep the root password - it's very handy to have. Sudo is good for most things, but you should always have a backup plan :). In addition, with physical access to the machine (i.e., the ability to pass options to the kernel at boot time), you can get it to boot you as root even if you don't have the password... so worrying about it is pretty pointless ;).

As for the VFAT partition, it doesn't actually store details about owners, groups, permissions, etc... so setting them will have no effect. Windows will read &write it fine.

To get a partition r/w by a user... firstly, create a group (e.g. "sharedfiles"), make the user part of that group, and chgrp the partition mount point to be that group as well (so owner root, group sharedfiles). Next, edit /etc/fstab (as root) and edit (or add) the entry for the drive so it looks a bit like this:-

/dev/hdXX        /media/mountpoint  auto    rw,user 0 1

That "should" work...

xF,

...Nick

---

### Post by aysiu on 2006-08-17
Step by step on mounting partitions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---


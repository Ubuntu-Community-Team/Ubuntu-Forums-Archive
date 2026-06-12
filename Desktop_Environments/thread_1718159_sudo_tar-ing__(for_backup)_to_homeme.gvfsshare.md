---
title: "sudo tar-ing / (for backup) to /home/me/.gvfs/share"
date: 2011-03-30
forum: Desktop Environments
---

### Post by rocket777 on 2011-03-30
In searching the forums, there's a thread on how to do a backup of your system using tar on the / directory (with some excluded dirs).

The problem is it puts the backup file right in / after you become su using:

```
sudo su

cd /

tar cvpzf ubackup.tgz ....  /

```
I want to do my tar over to my windows share, as there's not enough room - I'd need over 50% free it would seem.

At first, I thought one could use smb://machine/share/... on the command line but this apparently does not work.

I found the .gvfs directory in my /home/me/.gvfs with a directory in it which is the share I just opened from the desktop. Provided I remain the logged in local user, I can access the share through this path using the command line.

Problem is, as superuser (via sudo), I can't access this share - but I must be su to tar up all of the "/" directory.

If I become the su then I can't even cd to the .gvsf directory.

I was also puzzled about the removing of / from member names as well, but that's probably a secondary issue.

Here's what I tried and the result:

```

cd "/home/me/.gvfs/share on xp"
 sudo tar cvpzf ubackup.tgz --exclude=/proc --exclude=/lost+found --exclude=ubackup.tgz --exclude=/mnt --exclude=/home/me/.gvfs --exclude=/media --exclude=/sys --exclude=/dev /
[sudo] password for me:
tar: Removing leading `/' from member names
tar: ubackup.tgz: Cannot open: Permission denied
tar: Error is not recoverable: exiting now

```

---

### Post by eltommo on 2011-03-31
could you use smbmount to mount in to a folder instead?

---

### Post by rocket777 on 2011-03-31
> **eltommo said:**
> could you use smbmount to mount in to a folder instead?

Yup, all it took was to google "example of smbmount" and I was able to mount it.

I also found the -P tar option, which I probably don't need if I cd to the / directory instead of running the command from the /mnt/share directory I setup.

Now, I just need the nerve to try the restore command. Maybe I'll wait till I mess up something :P

Thanks

---


---
title: "Unable to write to hdb1"
date: 2006-09-09
forum: Desktop Environments
---

### Post by Rhapsody on 2006-09-09
hdb1 is a partition that I've been having a few problems with. First, some history on it.

I created this partition using an Ubuntu Live CD as a place to put my data when a backup was needed, and as a large partition for putting stuff I find on torrents. While resizing it to fill the partition, I got an unspecified error that remains something of a mystery (it was just a dialog window with 'Error' as the title). Since the partition seems to be working OK, I've crossed my fingers and hoped that it was trivial.

Either way, the Live CD refused to let me write to the partition. I had to use 'gksudo nautilus' to change the permissions so Owner, Group, and Others could all view and modify content. That solved the immediate problem.

However, once I had Kubuntu reinstalled and running, it wouldn't let me mount the partition at all. I created a new folder for it to be mounted in (/mnt/torrents) then placed a line (/dev/hdb1   /mnt/torrents  ext3  defaults  0  0) in my fstab file to get it mounted on boot. This worked, and I can now read the partition.

However, I still can't write to the partition. /home is nowhere near full yet so I'm not in any immediate danger, but hdb1 is my biggest partition, making it a good place to put my larger files. So help would be appriciated in finding out why Kubuntu isn't letting me write to it.

---

### Post by kidders on 2006-09-09
One thing worth checking is what **ls -ld /mnt/torrents** tells you about the permissions you've given the partition ... *after* it's mounted.

If Ubuntu won't let you write to something, chances are it's because you told it not to ... so all we need to do is figure out how, and you're sorted :-)

One question: Is this disk intended exclusively for your own personal use, or do you intend other users of your PC be allowed access to it too?

---

### Post by Rhapsody on 2006-09-09
> **kidders said:**
> One thing worth checking is what **ls -ld /mnt/torrents** tells you about the permissions you've given the partition ... *after* it's mounted.
That produced:

drwxrwxrwx 31 root root 4096 2006-09-04 21:46 /mnt/torrents

> **kidders said:**
> If Ubuntu won't let you write to something, chances are it's because you told it not to ... so all we need to do is figure out how, and you're sorted :-)
Yeah, that is usually the way. I'm slowly learning.

> **kidders said:**
> One question: Is this disk intended exclusively for your own personal use, or do you intend other users of your PC be allowed access to it too?
Well at the moment there's only one user account. Setting up a second, more restrictive account has been something I've been meaning to do for some time now, though I've never gotten around. I see no reasons why that second account would need any access to the partition though, so I'd only want access from the current account.

---

### Post by kidders on 2006-09-09
> 
drwxrwxrwx 31 root root 4096 2006-09-04 21:46 /mnt/torrents
 

Hmm... that suggests that (unless of course your partition is mounted read-only), everyone has write access to /mnt/torrents. Try **touch /mnt/torrents/delete_me** and see if you get any error messages.

Are you really certain you can't write to this partition?

---

### Post by Rhapsody on 2006-09-09
> **kidders said:**
> Hmm... that suggests that (unless of course your partition is mounted read-only), everyone has write access to /mnt/torrents. Try **touch /mnt/torrents/delete_me** and see if you get any error messages.
Tried it. No errors.

> **kidders said:**
> Are you really certain you can't write to this partition?
Well it's sort of weird really. I tried creating and deleting a new folder (which worked) but then I tried copying a file from /home to it, and I got an access denied error.

---

### Post by kidders on 2006-09-09
Hmm... well if the "touch" command worked, you **can** write to the disk. (The command I suggested has the effect of creating a new file called "delete_me".) The same applies to being able to create directories.

What was the error you saw? Perhaps you were having difficulty accessing the source location and not the destination.

---

### Post by Rhapsody on 2006-09-10
Well I've finally found a pattern. I seem to have full write access to the partition itself, but I'm unable to write to any of the folders that are on the drive. Doing an ls -ld on one of these folders produced:

drwxr-xr-x 3 999 999 4096 2005-09-25 15:29

This is definitely a different result than I got on the partition itself.

---

### Post by kidders on 2006-09-10
Looks like you need to read up a little on file access permissions! (Google is your friend). The file you mentioned in your last post is owned by a user your computer does not recognise, and you have been explicitly denied permission to write to it.

Seems as though you should have no difficulty writing on this disk, but if you want to modify files on your system (no matter where they are), you have to make sure you have permission!

Try the following to reset the file/directory access permissions for all files on the entire mount point to something a bit more reasonable:

```

chown -R username:username /mnt/torrents
chmod -R 644 !$
chmod -R +X !$

```

Needless to say, you'd have to be root to do it.

Hope that helps!

---


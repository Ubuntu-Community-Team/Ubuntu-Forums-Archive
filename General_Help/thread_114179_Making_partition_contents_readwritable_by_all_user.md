---
title: "Making partition contents read/writable by all users?"
date: 2006-01-08
forum: General Help
---

### Post by LxP on 2006-01-08
Hi all,

Thanks for taking a look at my thread. Here's my situation:

I have freshly installed Ubuntu Breezy on one of the computers on my home network (it's replacing Windows XP). I've managed to create a partition on the second hard drive for **/home** (at least I think it's working as expected!) so that user data is separate from the system drive.

I'd like to create another partition accessible through **/public**, which will allow each user to read and write to it without having to worry about setting permissions themselves.

I've set up an ext3 partition for this (is that the best choice?) and I've managed to configure Samba to allow other PCs on the network (all Windows) to access it like any other unprotected folder; now I'd like to have that functionality local to the computer itself and that's where I'm stuck. :oops:

Thanks very much for any help that you can give. I only hope that in time I can give something back to this community.

---

### Post by zoiks on 2006-01-08
I'm a little surprised, if the users can access the partition through samba (with rw permissions) then the system's users should also have access to the same partition.  In any event, a couple of things you can do are change the permissions of the mount point or use options in the appropriate fstab line, like "users,umask=0666,rw".  Check out man mount and man fstab.

---

### Post by LxP on 2006-01-08
Thanks very much for your response zoiks.

I didn't word my initial post as well as I could have; what I would essentially like is for files to 'lose' their permissions/ownership details when they enter the **/public** area, thus making files available to other users of the network immediately. Currently anyone on the computer running Ubuntu can indeed read and write to the directory, however I'm not able to access files from my WinXP computer unless they've been appropriately **chmod**ded. I'm looking to have this task automated or something.

Having said that, I think you've pointed me in the right direction. Thanks again -- I'll let you know how it goes.

---

### Post by LxP on 2006-01-08
After looking closer at your **fstab** example and reading the **man** page for **mount**, it seems to me that I would need to reformat this partition to a file system that doesn't offer permissions and ownership.

Is this a correct assumption and if so, would you recommend any particular file system?

---

### Post by Thirsteh on 2006-01-08
Just a little note on the filesystem consideration. ReiserFS is MUCH better if it's a partition with millions of small files, e.g. a MUD host, web host, or similar. ext3 however is better if you're going to have both small and large or of course large only.

---


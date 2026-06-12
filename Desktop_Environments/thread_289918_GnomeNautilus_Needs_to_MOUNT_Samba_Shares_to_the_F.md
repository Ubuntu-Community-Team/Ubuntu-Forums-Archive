---
title: "Gnome/Nautilus Needs to MOUNT Samba Shares to the Filesystem!"
date: 2006-10-31
forum: Desktop Environments
---

### Post by Avian00 on 2006-10-31
I am posting here bring some attention to what I consider to be a serious flaw in the way Gnome/Nautilus handles Samba Shares.  Currently, there is at least the beginnings of a great system for accessing and returning to network shares.  If I connect to a Samba share, that share appears in my list of Network Places both in my Places menu on the Gnome Panel and in the Nautilus listing of mounted media.  This provides at least the illusion of mounted media.  However, this media is NOT ACTUALLY MOUNTED.

To put this in perspective, let's consider what happens when I plug in a USB hard drive.  It, too, gets an entry in the Gnome/Nautilus Places menu, but it also has the benefit of being mounted in the filesystem in the /media folder.  The advantage of this, of course, is that applications that are not "Nautilus-Aware" can still access this media.  Network shares, however, cannot be accessed by applicaions that are not fully "Nautilus-Aware."  Thus, the point of this rant:

Gnome/Nautilus Needs to MOUNT Samba Shares to the Filesystem!

If anybody should come across this posting who has some influence in the Gnome/Nautilus development process, PLEASE pass this along.  If anybody has a better suggestion on where this rant should be posted, PLEASE let me know by replying to this post.  Thanks!

Matt

---

### Post by emkamau on 2006-11-12
Perhaps if enough people complain the devs may implement this. Its a flaw in Nautilus that it does not mount samba shares to the filesystem; preferably under /media.

Pass it on!

emk

---

### Post by mcduarte2000 on 2007-11-09
One year has passed and the situation is exactly the same.

Doesn't anyone want to correct this? This not working is a big turnoff to me. :(

---

### Post by jatatar on 2008-03-30
I fully agree, this would enhance the usability of the places>network feature of the menu and aid in interoperability with programs like amarok that are not nautilus aware.

---

### Post by hornetster on 2008-04-14
Ditto. If this were introduced, Nautilus would be a much more usable in regards to the network...  Please....

---

### Post by Racy on 2008-04-28
I completely agree about this annoyance.

---

### Post by Saneless on 2008-04-28
It's just seems weird that in ubuntu you can pretty much not have to ever worry about dropping to a command line, but mounting network drives is still so damn elusive.

When you read up on how to mount drives it all talks about the fstab or whatever, groups and users that differ, making directories and giving them certain rights, etc.  It's very confusing for most people and something that's literally as simple as picking "Map Network Drive" and clicking the "Reconnect at login" box to have it always part of the filesystem.

---

### Post by mcrsnap on 2008-05-25
Ditto! This is sorely needed.

---

### Post by mcrsnap on 2008-05-25
I found this article in link [http://www.debian-administration.org/articles/165](http://www.debian-administration.org/articles/165)

It does provide a workaround that allows nautilus visibility to mounted remote smb filesystems, drives, folders, files.

I have tested it and works well so far...

Mike

---

### Post by bradandersen on 2008-05-26
Very true,

  All they need is a "Map Network Drive" or Right-Click --> Mount This Folder.  Currently, VLC can only play videos from a mounted volume and browsing != mounted.

  It is such a basic necessity, but one that is overlooked because the "command line is so easy"?????

Argh,
Brad

---

### Post by simes2 on 2008-06-19
Yes, nautilus **definitely** needs to mount windows / samba / smbfs/cifs shares! Or at least not pretend to!

Try to upload/download files in firefox to/from a folder _that automagically popped up as one of the available options_, and not only does it not work, but it doesn't even pop up a warning!

I would've lost an important file I thought I'd uploaded if I hadn't noticed.

Is there a reason as to why it doesn't mount the shares? I would be more than willing to help if it's a conf/sh scripting issue (but I don't write much C/C++).

(BTW, I'm VERY IMPRESSED with how far ubuntu has come since I last looked at it a few years ago! Great work!)

---

### Post by tomjennings on 2008-07-23
I agree, it's a little weird. It doesn't seem like it would be a big deal for nautilus to simply put it's mount points in some consistent place, similar to /media.

I'm using smbmount etc to do the job, but it seems silly to have to mount the same share twice -- once in nautilus, and once via command line smbmount. Either should suffice --

* If I mount //host/name to /media/host.name, with smbmount, nautilus should see it.

* If I mount smb://host/name via Location in nautilus, I should be able to see it in /media/host.name.

What's the big deal?

---


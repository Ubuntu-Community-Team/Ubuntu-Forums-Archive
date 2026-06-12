---
title: "shared folder driving me NUTS!"
date: 2008-12-30
forum: General Help
---

### Post by Tom_ZeCat on 2008-12-30
I have a Windows XP machine and an Ubuntu Linux 8.04 machine networked together with a simple wired router.  I've shared a folder named "ShareThis" on the XP machine's internal drive C.  It's been that way for months and has always worked great.  I download large files on the Ubuntu PC and then copy them over to ShareThis on the XP machine.  All this is working perfectly and still is.  That's not the problem.

The problem is the new shared folder on the XP machine's new external drive that I've just hooked up.  It's a 500 GB Western Digital hard drive designated drive O.  I created a folder named "SharedO" the same way I did it for ShareThis.  It seemed to work.  On the Ubuntu machine, I started Dolphin and then clicked on: > Samba Shares (World logo icon) ==> Samba Shares  ==> Workgroup ==> athlon_screamer (the name of my XP machine)

At this point, it seems to work okay.  Both ShareThis and SharedO are listed.  When I click on ShareThis, I can see the contents of the folder.  However, if I click on SharedO, I get the message: > The file or folder smb://athlon_screamer/SharedO does not exist

Well, it does exist.  For some reason Ubuntu can't see it.  I thought that maybe it was a problem with the external drive's file system.  It's FAT32 for now.  I haven't converted it to NTFS yet.  However, I have another external drive that's already converted to NTFS.  I tried sharing one of its folders, but had the same problem accessing it from Ubuntu.  I turned off the firewalls on both machines, but still had the same problems.  In the XP machine, I right clicked on SharedO, chose "Sharing and Security", and then clicked on "Permissions".  I gave everyone "full control", "change", and "read," but it was to no avail.  The Ubuntu machine still thinks SharedO does not exist.  

I'm extremely frustrated.  Why does my Ubuntu PC think SharedO does not exist, and how can I fix this?

---


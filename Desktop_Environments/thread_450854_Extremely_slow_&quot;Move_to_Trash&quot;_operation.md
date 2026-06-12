---
title: "Extremely slow &quot;Move to Trash&quot; operation"
date: 2007-05-21
forum: Desktop Environments
---

### Post by explainer on 2007-05-21
I have Feisty installed on two systems, 1 32-bit and 1 64-bit.  On both systems, I am experiencing extremely long times before I get a Nautilus "Move to Trash" operation to complete.  The desktop appears to freeze, as though some code is running without yielding in the background.  I see no disk activity.  This should be a simple mv to a 'to-be-deleted' folder, and should not be compute intensive at all.  What gives?:(

---

### Post by prazgod on 2007-10-25
Just so you are not a lone voice - I am also experiencing this - but with the new Gutsy version (upgraded from earlier version)

If I right click a file on the desktop and then select "Move to deleted items" the whole gnome freezes - and then takes 3-5 mins to return to normal useable use.

---

### Post by fallingleaf on 2007-12-11
I'd like to add my "me too" here with the additional information that this is an intermittent problem for me.  I can't relate it to anything I'm doing because sometimes it happens with a clean boot and sometimes I can go days without a problem.

I'm running feisty.

---

### Post by Lostincyberspace on 2007-12-11
Does it doe the same thing if you just press the delete key with it selected.

---

### Post by fallingleaf on 2007-12-11
Actually, pressing the delete key is what I always do, but I tried with right-click, move to trash and it does the same thing. 

I may be on to something though.  I checked out /var/log/syslog and when I delete it says

```
Dec 11 19:02:38 localhost kernel: [25933.980000] smb_add_request: request [e7c58ec0, mid=32834] timed out!

```

Presumably this is because I had a samba share mounted and then changed to a different network. The files I'm moving to trash on the local disk, though.  I thought unmounting the share would fix it but I've been unable to unmount it. I get a "device is busy" error and the same smb error showing up in syslog.

Trying to use fuser to find out what is occupying to mount point returns
```
Cannot stat /mnt/samba: Input/output error
```

after a couple of minutes

---

### Post by Lostincyberspace on 2007-12-11
You are trying to delete from a samba share right?

---

### Post by fallingleaf on 2007-12-11
No, I didn't make it that clear in my last post because I was hurrying and didn't proof read very well.  I am deleting from a local hard drive.  For some reason Nautilus finds it necessary to try to access a samba share on a network that is no longer connected.  There are no windows even open for that samba share.  I even did a killall nautilus.  I did finally manage to unmount the samba share after logging out and logging back in.  The problem went away.  There seems to be a problem with nautilus and samba in general.  The reason I am mounting the samba share instead of browsing in nautilus is because sometimes nautilus refuses to browse the network at all.

---

### Post by Lostincyberspace on 2007-12-11
Do you have other samba shares, if you don't, or don't need them at least for a little while you uninstall samba. If you finish that and all is fine then you should be able to reinstall samba.

---

### Post by ratm355 on 2008-01-01
I have the same problem too. I just now "fixed" it by removing a samba mount out of /etc/fstab and doing the Connect to Server from the Places menu. I am using Gutsy x64.

---

### Post by explainer on 2008-02-10
Nautilus is doing a 'breadth-first' search of all mounted file systems whenever a 'move-to-trash' operation takes place?  This is to determine if the file(s) to be moved to trash are local or remote?  If so, this seems bass-ackward.  A depth-first search of the selected files/folders to determine if they are all local seems to be the right approach.  If a file is not local, then the move-to-trash is undetermined, it must become a remote delete request.  That logic needs to be modified.

---

### Post by crjackson on 2008-02-10
> **prazgod said:**
> **_[COLOR="Red"]but with the new Gutsy version (upgraded from earlier version)[/COLOR]_**
.

What do you mean with the NEW Gutsy version.  Has a newer ISO been released for download?

---

### Post by tcommbee on 2008-02-10
Maybe this should be filed as a bug against nautilus?

---

### Post by scohar70 on 2008-04-17
Bump!

I get this problem, and it's extremely annoying.  I think it's a bug that should be fixed.

I have samba shares mounted, but I am deleting from my local drive.

If I pop open a terminal and do an "rm", it is lickety-split fast.

---


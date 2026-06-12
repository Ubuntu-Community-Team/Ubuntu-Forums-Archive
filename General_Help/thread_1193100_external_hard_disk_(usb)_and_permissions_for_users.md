---
title: "external hard disk (usb) and permissions for users (ext3)"
date: 2009-06-21
forum: General Help
---

### Post by scheuri on 2009-06-21
Hi all

I have an external harddisk which I can connect with USB and which I formatted to use it with ext3 (instead of vfat or ntfs).

Now I have an issue with the permissions whenever I plug this ext3 external harddisk in.

**Situation:**
I have two users - "scheuri" and "joe" - on my system. Both use Gnome. Whenever I plug in my harddisk the harddisk gets detected with both users  and they are being asked what shall be done. My main (and actually only) choice is open a file browser (nautilus or whatever) so I can browse the content.
So that is fine so far...

Now, when I am logged in with "scheuri" and plug in the harddisk it gets mounted and the file browser opens.
However, I am not able to write on to this harddisk (into its /) with user "scheuri".
So "scheuri" seems not able to create new folders or files with his current permission.
The same applies to user "joe".

I completely understand that joe can not alter (and not even read) content created by scheuri and vice versa. 
That is a permission thing with ext3 and is absolutely fine and works as intendend.
However, the "root" (/) of the disk can not be written to by either user in the first place.

**Goal:**
The root of the harddisk is accessible and writable for ALL users who plug in the harddisks. Of course, when scheuri writes something on the disk it belongs to scheuri and depending on the permission scheuri sets no one else can write and/or read it. The same applies to all other users.
But I really want ALL users to be able to make folders or put files on the root of the harddisk in the first place.

**Edit:**
I am aware that plugging in the usb-disk on another computer which does not know "scheuri" or "joe" will lead into seeing UIDs instead of names (or, if "scheuri" or "joe" does exist, they might not be able to access it, because the UID is different).
However, as I am using this disk only for my purposes, that is not an issue...

Is there anything I need to do with udev permissions or with fstab? Anyone an idea how this might work?
I am working on jaunty 64bit by the way.

Thanks a lot for your help
cheers
scheuri

---

### Post by scheuri on 2009-09-24
Bump....sorry

---

### Post by aquamammal on 2009-10-02
Bump!!

Help~ how do I enter as root?

---

### Post by sisco311 on 2009-10-02
@scheuri
create a new group:
```
sudo addgroup **groupname**
```
add the users to the group:
```
sudo adduser *username1* **groupname**
sudo adduser *username2* **groupname**
```
if you are logged in as username1 or username2, you may have to log out and log back in.

change the permission of the root of the partition to 1775(or 1777)
and the owner and group to root:groupname.

assuming that it's mounted under /media/mydisk:
```

sudo chown root:groupname /media/mydisk
sudo chmod 1775 /media/mydisk

```

the initial "1" means that only the owner of a particular file can affect that file.

now anybody who is in the groupname group can write to the disk.

---


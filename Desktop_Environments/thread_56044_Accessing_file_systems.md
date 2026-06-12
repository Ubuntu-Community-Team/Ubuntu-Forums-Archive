---
title: "Accessing file systems"
date: 2005-08-11
forum: Desktop Environments
---

### Post by michas on 2005-08-11
Hi,

Is there a simple way to access other filesystems (windows, other Linux,...) in a default ubuntu installation?
Ok, I could manually mount it, or I could manually add it to fstab, but isn't the a GUI-way for beginners?

For example in Knoppix you have an icon for each file system. clicking it will mount and open it.
Can i create such an icon in ubuntu too?

If I add it to fstab, is then a fast way to access it?
(Can I create a link to the mountpoint on the desktop?)

I'm pretty new to gnome, so any references to proper documentation, would be nice too. :)

---

### Post by kassetra on 2005-08-11
[QUOTE=michas]Hi,

Is there a simple way to access other filesystems (windows, other Linux,...) in a default ubuntu installation?
Ok, I could manually mount it, or I could manually add it to fstab, but isn't the a GUI-way for beginners?

For example in Knoppix you have an icon for each file system. clicking it will mount and open it.
Can i create such an icon in ubuntu too?

If I add it to fstab, is then a fast way to access it?
(Can I create a link to the mountpoint on the desktop?)

I'm pretty new to gnome, so any references to proper documentation, would be nice too. :)[/QUOTE]

Well, in gnome you can go to Places->Network Servers or Places->Connect to Server...  and the first one will show you all the connected boxes.  The connect to server is the option I used when I wanted to connect to another box in the house (and even one across the country.) ... using either of those options will create links on your desktop.

---

### Post by michas on 2005-08-12
[QUOTE=kassetra]Well, in gnome you can go to Places->Network Servers or Places->Connect to Server...  and the first one will show you all the connected boxes.  The connect to server is the option I used when I wanted to connect to another box in the house (and even one across the country.) ... using either of those options will create links on your desktop.[/QUOTE]

Thanks, but I think my problem is even simpler. There is no Network, I just want to access local file systems.
There surely is an easy way for that, isn't it?

I just want to have an icon named "WindowsC" on the desktop, and clicking on it should open the former windows drive C. This can't be so difficult, or did i miss something?

---

### Post by blakamin on 2005-08-12
[http://ubuntuguide.org](http://ubuntuguide.org) .... something about "mounting ntfs/fat filesystems at boot"... cant find a link at the moment... too many beers...(it is friday night in NZ)

---

### Post by fresco on 2005-08-12
From Ubuntu Guide:

Q: How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only?

   1. Read General Notes
   2. Read How to list partition tables?
   3.

e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
     Local mount folder: /media/windows

   4.

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

   5. Append the following line at the end of file

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0


Of course, you should speify right device in fstab. And you can change mount point too.  Then, sudo mount -a.

Then, create a launcher on your desktop which will refer to /media/windows (or a place where you mounted your win partition). Fill "Command" field with *nautilus /media/windows*. Don't know, maybe it isn't the simplest way, but it works.
  :)

---

### Post by michas on 2005-08-13
[QUOTE=fresco]Then, create a launcher on your desktop which will refer to /media/windows (or a place where you mounted your win partition). Fill "Command" field with *nautilus /media/windows*. Don't know, maybe it isn't the simplest way, but it works.
  :)[/QUOTE]

Thanks, I was looking for something like this.

I now played a little bit with Gnome and found, that one can make a link to a folder throught pressing shift and ctrl while drag and drop. This should do the trick. (This seems to be the only way creating a desktop-link.)

---


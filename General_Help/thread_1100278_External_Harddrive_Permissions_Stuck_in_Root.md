---
title: "External Harddrive Permissions Stuck in Root"
date: 2009-03-19
forum: General Help
---

### Post by sidka on 2009-03-19
Short Version: External hard drive's permissions are stuck in Root, and no solution I have tried has changed it.

Long Version: Hi, I'm having a bit of trouble with the permissions on my external harddrive, and I was wondering if any of you had any suggestions. There was a power outage as I was transferring some files to my external harddrive (not unusual in my side of town), and I waited for the power to come back on, rebooted my computer, and had to unplug my external and plug it back in for Ubuntu to recognize it again (once again, as usual).

However, when I try to pick up where I left off (including overwriting the half-completed file), it would not let me write anything to the disk, nor delete the file. After about fifteen minutes of being stubborn, I actually checked the permissions, which are now:
User Root is the owner
User Root can create/delete files
Group Root can create/delete files
Others can create/delete files
Last changed: Dec 11, 2008

I have searched the forums, and have tried several solutions, but nothing seems to have any effect. In Nautilus, I could select new settings, only to have them revert as soon as I clicked away.

External Hard drive Info:
Size: 160.0GB
File System: NTFS 3.1
Vendor: Maxtor
Model: 3200

What I have tried: (in order and with intermittent cursing)
Unmounting and remounting the harddrive
Rebooting the harddrive
Rebooting the computer with the hard drive plugged in
Rebooting the computer, then booting and mounting the hard drive
Changing the permissions of the entire harddrive in terminal
Changing the permissions of individual folders in terminal
Changing the permissions of individual files in terminal
Changing my user group to Admin
Changing my user group to Root
Changing the permissions of the entire harddrive in Nautilus as Root
Changing the permissions of individual folders in Nautilus as Root
Changing the permissions of individual files in Nautilus as Root
Trying to delete individual files in Nautilus as Root

Sudo commands: chown, chmod (icluding and excluding -R (both) and 777 (chmod))


Thanks again for any help you can offer me!

---

### Post by pmlxuser on 2009-03-19
have you tried restarting your machine with the hard disk plugged in. it seem there is a prosess that has locked your permission; i would give it a short restarting while the ext hdd is plugged in..

---

### Post by blazemore on 2009-03-19
What filesystem does the hard disk use?
You could try copying all the files onto a filesystem formatted as FAT32, which doesn't support UNIX permissions (I think).
Then you could reformat the dodgy drive, and copy the files back.

---

### Post by sidka on 2009-03-19
> **pmlxuser said:**
> have you tried restarting your machine with the hard disk plugged in. it seem there is a prosess that has locked your permission; i would give it a short restarting while the ext hdd is plugged in..

I have, but I forgot to list it in my attempted solutions, but I just forgot to put it down. Sorry about that.


> **blazemore said:**
> What filesystem does the hard disk use?
You could try copying all the files onto a filesystem formatted as FAT32, which doesn't support UNIX permissions (I think).
Then you could reformat the dodgy drive, and copy the files back.

The file system is ntfs 3.1, but I don't have any other hard drives laying around, and the reason I had that one in the first place is because I'm basically out of room on my computer.

---

### Post by blazemore on 2009-03-19
Okay so couldn't you copy everything to a folder on your desktop, change the permissions there, reformat the disk and copy it back?

---


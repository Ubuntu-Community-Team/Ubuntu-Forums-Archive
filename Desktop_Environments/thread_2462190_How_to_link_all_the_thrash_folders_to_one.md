---
title: "How to link all the thrash folders to one?"
date: 2021-05-15
forum: Desktop Environments
---

### Post by linerman on 2021-05-15
Hi,

I have four harddrives with 7 partitions. When I delete a file on a partition, then system is making ".Thrash100" folder on the partition.
But in the end of the day I have to check all of my partitions and delete that folders to gain space. Is there a possibility to simlink all these ".Thrash100" folders into one?
(Yeah, I know, a habit from Windows Recycle Bin....)
Deleting only one folder, not the 7 would save me a lot of time and clicking...

---

### Post by TheFu on 2021-05-15
The implementation of "trash" keeps the files on the same partition because doing anything else would be a copy/delete not a move.  

Move within a partition is instantaneous - 1 file system command - just changing a pointer for where the data is located.  
Moving across partitions would be a copy to the new partition, followed by a delete on the old one, infinitely slower.  That could take many minutes, depending on the size of the file.  
Also, if the file is already on a partition, then the move will work, while a copy/delete may not if the target partition doesn't have sufficient space available.  Lots of considerations.

The easy answer is to stop using the trash completely and just have daily, versioned, backups.  Then if you accidentally delete some, which happens once a year, perhaps once every other year, then getting it back is a slight hassle, but not impossible. How to disable trash would be a DE question and perhaps a file manager question. Different file managers do it differently.

BTW, there are many different implementations of "Trash" on the different Linux GUIs.  Also, they are all tied to the userid, necessarily. On a multi-user system, it would be bad if files deleted became available to other users, right?

What else can you do?  Well, you could create a little script that searches all the mounted partitions for the /.Trash/ directories, then look for all the files owned by your current userid, and delete them.  Be 100% certain your script only looks in exactly the Trash directories you want, because if it finds files outside those areas and starts deleting them, well ... let's just say ... it will be a very bad day, indeed.

I don't use trash myself - when I delete something, I want it gone, deleted, now. I don't want to waste time later.

For example, some directories for trash on 1 system here:
[LIST]
[*]/nfs/home/thefu/.local/share/Trash/
[*]/nfs/home/thefu/.claws-mail/imapcache/mail/Trash/
[/LIST]

So, my little script is
```
#!/bin/bash

/usr/bin/find $HOME/.local/share/Trash/ $HOME/.claws-mail/imapcache/mail/Trash/ -type f -delete
```

That can be run safely from any directory, but only by my userid to get the desired results.  If another userid runs it, then HOME will be different.

So, you could run that script (assuming you modify it for other partitions) 
or 
you could setup a little automation using **xdotool** to enter the keystrokes into your file manager.  [https://linuxhint.com/xdotool_stimulate_mouse_clicks_and_keystrokes/](https://linuxhint.com/xdotool_stimulate_mouse_clicks_and_keystrokes/)  Avoid using mouse inputs. Try to do everything with the keyboard and existing accel keys already built into the program.  Mice movements and buttons are trouble when doing automation. They seldom work as expected, unless the exact same windows and buttons are in the exact same locations every time.  

Another option is **cnee**, but this is less accurate than xdotool and requires more detailed step design.  I use cnee for some multi-program/window integrations and it was ugly to setup.  Before I can run that automation, I have to verify 3 windows are in exactly the correct locations and 1 button is in a very specific location on the screen or it will fail.  It is a 10 minute long, complex, script, but at least I don't have to manually do it anymore.

---

### Post by Holger_Gehrke on 2021-05-15
Emptying the trash in the file manager should empty all the trash directories on all filesystems currently mounted. The directories themselves and the directories in them (named expunged, files and info on GTK-based GUIs) will still be there but be empty and shouldn't take more than a few kb of disk space. Additionally there's a command line tool named 'gio' that should be available on all GTK-based GUIs (Gnome, XFCE, Mate ...) . Calling 'gio trash --empty' should do the same thing as emptying the trash in the file manager. 'gio list trash://' will show all the files in the trash.

Holger

---

### Post by linerman on 2021-05-22
> **Holger_Gehrke said:**
> Emptying the trash in the file manager should empty all the trash directories on all filesystems currently mounted. The directories themselves and the directories in them (named expunged, files and info on GTK-based GUIs) will still be there but be empty and shouldn't take more than a few kb of disk space. Additionally there's a command line tool named 'gio' that should be available on all GTK-based GUIs (Gnome, XFCE, Mate ...) . Calling 'gio trash --empty' should do the same thing as emptying the trash in the file manager. 'gio list trash://' will show all the files in the trash.

Holger

That does not work. Most of my partitions are NTFS or FAT32. Thrash folder in the file manager is empty despite the fact that .Thrash100 is full on NTFS partition.

---


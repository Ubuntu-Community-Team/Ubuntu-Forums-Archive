---
title: "Talking to Windows"
date: 2005-10-28
forum: Desktop Environments
---

### Post by megamania on 2005-10-28
With Breezy out, I decided it was time to move Linux to my primary hard disk, and kick Windows out of my computer. That's what I did. :-)

My second hard disk is the same size as the primary one, and it's on a removable rack, being used exclusively for backing up my data.

I thought I would install Win XP there, since I still need it from time to time. The options I see at the moment are:

1) format the entire disk in Fat32, so that I can easily back up my hard disk to it (disadvantages: file system reliability?).
2) create a small ntfs partition for XP and a ext3 partition for the backup (disadvantages: this would make accessing the data from win more difficult)
3) format the disk in ntfs and use Captive in linux to access it (disadvantages: is Captive reliable? I need to backup 160Gb of data!).

After the first full back-up, I'd need a software to create a mirror of the /home directory (like xxcopy or viceversa for win).

All suggestions are welcome!

---

### Post by MarcDM on 2005-10-28
I would make a small (<=10GB) NTFS Partition to install WinXP and friends (Office,VB,Nero,Premiere). 
Then I would make the rest of the drive EXT2 and access it from XP using 
ext2fsd : an open source Ext2 file system driver for Windows (NT/2K/XP)

[http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)

I've used it in XP and it works pretty well for ext2. I don't remember what happened when I tried to mount an ext3 partition.

At this point, if you're not comfortable writing to ntfs from linux, or writing to ext2 from windows, you can still read everything from everywhere. You can save the file on the NTFS from Windows and copy it back when you reboot.

---

### Post by megamania on 2005-10-28
[QUOTE=MarcDM]I would make a small (<=10GB) NTFS Partition to install WinXP and friends (Office,VB,Nero,Premiere). 
Then I would make the rest of the drive EXT2 and access it from XP using 
ext2fsd : an open source Ext2 file system driver for Windows (NT/2K/XP)

[http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)

I've used it in XP and it works pretty well for ext2. I don't remember what happened when I tried to mount an ext3 partition.
[/QUOTE]

Thanks. I used ext2IFS ([http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)), but it says it *probably* doesn't work under XP... didn't know about ext2fsd.

Any more suggestions? And what about the software to use? As I said, I loved ViceVersa and Xxcopy for Windows...

---


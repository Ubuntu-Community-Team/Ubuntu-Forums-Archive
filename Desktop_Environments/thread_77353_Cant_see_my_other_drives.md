---
title: "Cant see my other drives"
date: 2005-10-16
forum: Desktop Environments
---

### Post by Darrin on 2005-10-16
I have two Hard Drives, C and D. C partitioned in two with Windows XP and Ubuntu. My D drive has all my Windows Back up files on it. When I was using Linspire I could browse my D drive still. Using Ubuntu I dont see it. How do I get it to display?

---

### Post by seldenthuis on 2005-10-16
You first have to mount it. Usually when you install Ubuntu it already recognises you're windows partitions. If it did you should be able to find them under /media/hd...

---

### Post by Darrin on 2005-10-16
[QUOTE=seldenthuis]You first have to mount it. Usually when you install Ubuntu it already recognises you're windows partitions. If it did you should be able to find them under /media/hd...[/QUOTE]

I have a /media, but within that is just shows CDrom and Floppy drives.

---

### Post by mustang on 2005-10-16
[QUOTE=Darrin]I have a /media, but within that is just shows CDrom and Floppy drives.[/QUOTE]

Did you follow this guide?

[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

---

### Post by NZ-Wanderer on 2005-10-16
this is what I do

(Note if you only use normal terminal you probably need to use the sudo command in front of some of the commands.. :)

goto root terminal and type: ```
fdisk -l
``` (this gives me list of drives etc which I copy and print out)
then I go: ```
cd ..
``` (until I back out at root (file system)
then: ```
cd media
``` (to get into media)
then: ```
ls
``` (to view the contents)
then: ```
mkdir ???????
``` (where ???? is the name for your drive)
and repeat for as many as you want

then I do: ```
gedit /etc/fstab
```
 and edit my drives corresponding to the drives in theprintout and what I had done in the mkdir commands.. eg:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd6       /home           ext3    defaults        0       2
/dev/hdd7       /media/go-between vfat  iocharset=utf8,umask=000        0       0
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /media/hda5     ntfs    defaults        0       0
/dev/hda6       /media/hda6     ntfs    defaults        0       0
/dev/hda7       /media/hda7     ntfs    defaults        0       0
/dev/hda8       /media/hda8     ntfs    defaults        0       0
/dev/hda9       /media/hda9     ntfs    defaults        0       0
/dev/hda10      /media/hda10    ntfs    defaults        0       0
/dev/hda11      /media/hda11    ntfs    defaults        0       0
/dev/hda12      /media/hda12    ntfs    defaults        0       0
/dev/hda13      /media/html     vfat    iocharset=utf8,umask=000        0       0
/dev/hda14      /media/jukebox  vfat    iocharset=utf8,umask=000        0       0
/dev/hda15      /media/misc     vfat    iocharset=utf8,umask=000        0       0
/dev/hda16      /media/ztmppic  vfat    iocharset=utf8,umask=000        0       0
/dev/hda17      /media/hda17    ntfs    defaults        0       0
/dev/hdb2       /media/hdb2     ntfs    defaults        0       0
/dev/sda1       /media/backup-apps   ntfs  iocharset=utf8,umask=000        0       0
/dev/sda5       /media/backup-fs2004 ntfs  iocharset=utf8,umask=000        0       0
/dev/sda6       /media/backup-games  ntfs  iocharset=utf8,umask=000        0       0
/dev/sda7       /media/backup-misc   ntfs  iocharset=utf8,umask=000        0       0
/dev/sda8       /media/backup-hdd    ntfs  iocharset=utf8,umask=000        0       0
/dev/sda9       /media/sda9     vfat    iocharset=utf8,umask=000        0       0
/dev/hdd5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

after you finish reboot the computer :)

Note the: ```
iocharset=utf8,umask=000
```

This is what lets me access the drives... (Be very careful tho, it not good to write to a ntfs partition, it ok to read tho :)

Dunno if this helps or not, but it the way I do it..

---

### Post by Darrin on 2005-10-16
I did not. Thank you. 
Do I just type this stuff in the terminal? If so when I do that it asks for a password. Im assuming my root. My keyboard isnt responding to my keystrokes in the terminal.

---

### Post by steve.horsley on 2005-10-16
[QUOTE=Darrin]I have two Hard Drives, C and D. C partitioned in two with Windows XP and Ubuntu. My D drive has all my Windows Back up files on it. When I was using Linspire I could browse my D drive still. Using Ubuntu I dont see it. How do I get it to display?[/QUOTE]

Any hard drives can be seen in the /dev directory. First you need to know what name it has. Try this comand:

ls /dev/hd*

Here is mine:
steve@dingly:~$ ls /dev/hd*
/dev/hda   /dev/hda2  /dev/hda5  /dev/hda7  /dev/hda9
/dev/hda1  /dev/hda3  /dev/hda6  /dev/hda8  /dev/hdc

hda is my first hard disk, which has many partitions, 1-9 (but not 4).
hdc is my CD drive.

I guess your other hard drive will be hdb or hdc, so the D: partition will be hdb1 or hdc1.

Once you know, you can "mount" it, making it readable. Mounting a drive makes it take the place of a (usually) empty direcory. Make a directory to mount the drive on (in /mnt or /media would make sense) with the command:

sudo mkdir /mnt/D

then mount the drive there with the command:

sudo mount -t auto /dev/hdb1 /mnt/D

You may have to say "-t ntfs" or "-t vfat" instead of "-t auto", but it can usually figure out the type by itself. If this works, you can now see the drive contents in /mnt/D. This will not be permanent - it will disappear when you reboot. To make it permanent, you must make an entry in the configuration file /etc/fstab, which says which partitions should be mounted where when booting. WARNING: If you screw this file up, you essentially screw the O/S up and may have to re-install.

Here is the line from my fstab file that mounts a FAT partition (drive E to my windows). 

/dev/hda9  /mnt/E   vfat  umask=0,iocharset=iso8859-15,codepage=850 0 0

Try adding the above line (with the first 3 fields changed to suit) to your /etc/fstab file, at the end - "sudo gedit /etc/fstab". Do not change any other lines.

Hope this helps.

---

### Post by NZ-Wanderer on 2005-10-16
It is, it's just that passwords are hidden.. - so type your password and hit ENTER....

[QUOTE=Darrin]My keyboard isnt responding to my keystrokes in the terminal.[/QUOTE]

---

### Post by Darrin on 2005-10-16
Im going to try this out in the morning. I want to write it all down or knowing me Ill mess it up. Messing up things, Im good at.;) 
Thanks for all the info. I appreciate all the help

---

### Post by Darrin on 2005-10-21
Im totally lost on this. Sorry :( I think Im going to mess something up. Im just staring at the posts not knowing what is being said. It looks like a different language to me.

---

### Post by Tass on 2005-10-22
Hi

Thanks for the help on this.  Just installed.  Followed the instructions given above, and I've got the drive mounted now.  If I go to System > Administration > Disks.  I can see the different drives there, and if I click on browse, I can browse the drive.  The drives now have a shortcut on my desktop, and are in the places pane inthe filebrowser window.

But, when I close this browsing window and try to access the drive through filebrowser, I get the message : "The folder contents could not be displayed.  You do not have the permissions necessary to view the contents of "HDD1" (HDD1 is the folder I created in /media)

If I right-click > properties on the icon (on my desktop, or in places in filebrowser), under permissions, the owner is root, and it says that because I'm not the owner, I can't change the permissions.

when I mounted the drives, I just added the -t ntfs switch.  Is there something else I should be using?

Thanks

Tass

---

